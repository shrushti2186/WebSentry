# WebSentry — Uptime Monitoring Platform (MySQL)

A starter full-stack project using React, Vite, Tailwind CSS, Node.js, Express and MySQL.

## Requirements
- Node.js 18+
- MySQL 8+
- npm

## 1. Database
Open MySQL Workbench and run `database/schema.sql`.

## 2. Backend
```bash
cd backend
npm install
```
Copy `.env.example` to `.env` and fill in your MySQL details and JWT secret.
```bash
npm run dev
```
The API runs at `http://localhost:5000`. The monitor worker checks active monitors every 60 seconds.

## 3. Frontend
In another terminal:
```bash
cd frontend
npm install
npm run dev
```
Open the Vite URL shown in the terminal (usually `http://localhost:5173`).

## 4. Try it
1. Register an account.
2. Log in.
3. Add a website such as `https://example.com`.
4. Wait up to 60 seconds for the first automatic check.

## API routes
- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/monitors` (JWT)
- `POST /api/monitors` (JWT)
- `DELETE /api/monitors/:id` (JWT)
- `GET /api/monitors/:id/pings` (JWT)
- `GET /api/public/status/:userId`
- `POST /api/ai/analyze/:monitorId` (JWT; requires Gemini key)

## Rename compatibility note
- The application branding is now WebSentry. The existing MySQL database name (`sentinel_db`) and browser storage keys are intentionally retained so an existing installation and saved login session continue to work without a database migration.

## Important notes
- This is a learning/MVP project, not a hardened production monitoring service.
- Before deploying publicly, add strict SSRF protection (including DNS/IP validation and redirect checks), rate limiting, email verification, password reset, request logging, and stronger operational monitoring.
- Keep `.env` private. Never commit API keys or database passwords.
- For deployment, provision a managed MySQL database and configure environment variables on the backend host. The frontend's `VITE_API_URL` must point to the deployed API.
