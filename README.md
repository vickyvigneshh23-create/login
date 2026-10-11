# Secure Login System

A beginner-friendly Flask web application demonstrating core login security controls.

## Features

- Account registration and login
- Password hashing with Werkzeug's scrypt-based password hashing
- SQLite database and parameterized SQL queries
- CSRF protection for forms with Flask-WTF
- Rate limiting for login and registration endpoints
- Protected dashboard
- Session clearing on login and logout
- HttpOnly and SameSite session-cookie settings
- Generic invalid-login error message
- Responsive HTML/CSS interface

## Requirements

- Python 3.10 or newer recommended
- pip

## Install

```bash
python3 -m venv .venv
```

Activate the environment:

Linux/macOS:
```bash
source .venv/bin/activate
```

Windows:
```powershell
.venv\Scripts\Activate.ps1
```

Install dependencies:

```bash
python -m pip install -r requirements.txt
```

Set a strong development secret key before running.

Linux/macOS:
```bash
export SECRET_KEY="$(python -c 'import secrets; print(secrets.token_hex(32))')"
python app.py
```

PowerShell:
```powershell
$env:SECRET_KEY = python -c "import secrets; print(secrets.token_hex(32))"
python app.py
```

Then open http://127.0.0.1:5000 in your browser. The SQLite database is created automatically when the app starts.

## Try it

1. Create a test account with a username and a password of at least 12 characters.
2. Log in and open the dashboard.
3. Log out, then confirm the dashboard redirects to the login page.

Use a unique test password, not a password used for a real account.

## Security notes and production limitations

This is an educational starter project, not a production-ready identity system. Before deployment:

- Set a strong, private `SECRET_KEY`; never commit secrets to GitHub.
- Serve only over HTTPS and set `COOKIE_SECURE=1` in the production environment.
- Replace the in-memory rate-limit storage with Redis or another shared persistent backend in multi-worker deployments.
- Use a production WSGI server and secure reverse-proxy configuration; do not expose Flask's development server.
- Add email verification, password reset, MFA, account recovery, monitoring, and a tested backup/migration strategy as appropriate.
- Review password policy and breach-password screening requirements for your use case.
- Do not reuse this demo as the only protection for sensitive or regulated data.

## Files

- `app.py` — Flask application
- `templates/` — HTML pages
- `static/style.css` — styling
- `requirements.txt` — dependencies
- `.gitignore` — ignores local database, virtual environment, and secrets
