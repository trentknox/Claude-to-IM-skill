# Token Verification Error Handling

When setting up Claude-to-IM-skill, tokens are verified against their respective platform APIs. This document outlines the error handling process when token verification fails.

## Common Verification Failures

### Invalid Tokens

- **Error Message**: `Invalid token provided for <Platform>`
- **Cause**: The token does not match the expected format or is malformed
- **Recovery**: Re-enter the token using the setup interface

### Expired Tokens

- **Error Message**: `Token expired for <Platform>`
- **Cause**: The token has exceeded its validity period
- **Recovery**: Generate a new token from the platform and update it in the configuration

### Platform API Downtime

- **Error Message**: `Unable to verify token with <Platform> API`
- **Cause**: The platform's API is temporarily unavailable
- **Behavior**: The system will retry verification every 30 seconds for up to 5 minutes
- **Recovery**: If the issue persists, check the platform's status page and retry later

## Recovery Steps

1. Access the token configuration interface
2. Locate the platform with the verification error
3. Update the token field with the correct value
4. Save changes to trigger re-verification

Note: You do not need to restart the entire setup process to correct token verification errors.

## Timeout Behavior

When platform APIs are unresponsive:

- Initial verification attempt waits 10 seconds for response
- Subsequent retries occur every 30 seconds
- After 5 minutes of failed attempts, the system will:
  - Log an error
  - Mark the token as unverified
  - Continue operation with limited functionality

To resume full functionality, correct the token and save changes when the platform API is available.