# JARVIS AI — PC + Android starter

A responsive, installable web app starter with a blue holographic dashboard, Gemini chat API route, browser voice input (where supported), spoken replies, and Vercel configuration.

## What works in this starter

- Responsive interface for desktop and Android-sized screens
- Text chat through a server-side Gemini API endpoint
- Browser speech recognition when supported and permitted
- Spoken replies using browser text-to-speech
- Links to Gmail and YouTube
- Installable PWA shell and offline-cached static assets
- Vercel serverless API route and environment-variable setup

## What is NOT connected or included

No device has been granted full access. Gmail, Chrome, YouTube, and WhatsApp accounts are not connected by default. The integration screen contains setup information and safe links, not account access. This project does not read private messages, send messages, control the whole OS, or bypass permissions. Those features require separate authorized integrations and, for some device actions, a companion app or browser extension.

## Requirements

- Node.js 20 or a currently supported Node.js LTS
- A Gemini API key from Google AI Studio
- Optional Vercel account for hosting

## Run locally on Windows

1. Extract the ZIP to a folder.
2. Install Node.js if needed.
3. Open PowerShell or Terminal in the project folder.
4. Run:

   ```powershell
   npm install
   Copy-Item .env.example .env.local
   notepad .env.local
   ```

5. Put your own key after `GEMINI_API_KEY=` in `.env.local`. Never share the key or commit this file.
6. Start the app:

   ```powershell
   npm run dev
   ```

7. Open the local address printed by Vercel CLI (commonly `http://localhost:3000`).

If `npm run dev` says Vercel is missing, run `npm install` again and check that Node.js is installed (`node -v`, `npm -v`).

## Use on Android

Deploy the app to HTTPS using Vercel, then open its URL in Chrome on Android. From Chrome's menu, choose **Install app** or **Add to Home screen** if offered. Microphone input requires permission and browser support. This PWA is not a native Android app and cannot grant itself full device access.

## Deploy to Vercel

1. Upload the project to a private Git repository or use the Vercel CLI from the project folder.
2. Import the project into Vercel.
3. In Project Settings → Environment Variables, add:
   - `GEMINI_API_KEY` — your Gemini key
   - `GEMINI_MODEL` — optional; default is `gemini-2.5-flash`
4. Redeploy after adding variables.
5. Keep `.env.local` out of Git. Do not use a `NEXT_PUBLIC_` or other client-exposed variable name for the API key.

## Integration roadmap

- **Gmail:** Google Cloud project, Gmail API enablement, OAuth consent, narrow scopes, server-side token storage, and any required Google verification.
- **Chrome:** A separate Chrome extension for permitted tab/browser features. Ask for only the specific extension permissions needed.
- **YouTube:** Use supported YouTube APIs for search or metadata; playback and account actions have API/platform limitations.
- **WhatsApp:** Use official supported business messaging APIs where appropriate. It does not provide unrestricted access to personal WhatsApp chats.
- **Windows device actions:** A separate local companion app with an allowlist of commands and confirmation for sensitive actions.
- **Android device actions:** Native Android app and Android runtime permissions; some actions are restricted by Android.

## Security notes

- Keep API keys on the server in environment variables.
- Use OAuth official consent screens for account integrations; never ask users to paste passwords into JARVIS.
- Add authentication, rate limiting, and per-user authorization before exposing a personal deployment publicly.
- Review API usage and quotas in your provider dashboard.
- The starter is a development baseline, not a security-audited production system.
