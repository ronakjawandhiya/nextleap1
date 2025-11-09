# Google OAuth 2.0 Setup Guide

## Error: "Access blocked: Authorization Error - Error 400: invalid_request"

This error occurs when your Google Cloud Console OAuth configuration is incomplete or incorrect.

## Step-by-Step Fix:

### 1. Configure OAuth Consent Screen

1. Go to: https://console.cloud.google.com/apis/credentials/consent
2. Select your project
3. Fill in the required information:
   - **App name**: "Next Leap" (or your app name)
   - **User support email**: Your email address
   - **Developer contact information**: Your email address
4. Click **Save and Continue**
5. Skip Scopes (click **Save and Continue**)
6. Add **Test Users**:
   - Click **Add Users**
   - Add your email: `ronakjawandhiya@gmail.com`
   - Click **Add**
   - Click **Save and Continue**
7. Review and go back to dashboard

### 2. Configure OAuth 2.0 Client ID

1. Go to: https://console.cloud.google.com/apis/credentials
2. Click on your OAuth 2.0 Client ID (`688021959719-9p6c7a55hjq1tr82eersqspd5rk9ml15.apps.googleusercontent.com`)
3. Under **Authorized JavaScript origins**, click **Add URI** and add:
   - `http://localhost`
   - `http://localhost:8000`
   - `http://127.0.0.1`
   - `http://127.0.0.1:8000`
   - Your production domain (if applicable)
4. Click **Save**

### 3. Important Notes

- **Testing Mode**: If your app is in "Testing" mode, only the test users you added can sign in
- **Publishing**: To allow anyone to use the app, you need to publish it (requires verification)
- **Wait Time**: Changes may take a few minutes to propagate

### 4. Testing Locally

For local testing, use a local server instead of opening the file directly:

```bash
# Using Python
python -m http.server 8000

# Or using Node.js
npx http-server
```

Then open: `http://localhost:8000/login.html`

### 5. Common Issues

- **Error 400**: Usually means authorized origins are missing or incorrect
- **Access blocked**: Usually means the user is not in the test users list (if app is in testing mode)
- **Invalid client**: Check that the Client ID is correct in your code

## Current Client ID in Code

```
688021959719-9p6c7a55hjq1tr82eersqspd5rk9ml15.apps.googleusercontent.com
```

Make sure this matches the Client ID in your Google Cloud Console.

