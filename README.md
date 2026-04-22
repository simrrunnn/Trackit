# Trackit — Personal Expense Tracker

A clean, minimal web dashboard to track monthly income and expenses — built with Flask and SQLite.

---

## Features

- Dashboard with stat cards and spending charts
- Add, edit, and delete expenses via modal forms
- Category-based spending breakdown with progress bars
- Savings rate calculation
- Export full summary to CSV
- Settings page to update salary and reset data
- Dark / light theme toggle
- User authentication (register, login, password reset)

---

## Tech Stack

- **Backend:** Python, Flask 3.0+
- **Database:** SQLite (local file — `users.db`)
- **Templating:** Jinja2
- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **Charts:** Chart.js, D3.js

---

## Getting Started

### Prerequisites

- Python 3.8+

### 1. Clone the repo

```bash
git clone <your-repo-url>
cd monthly-expenses-tracker
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate       # macOS / Linux
.venv\Scripts\activate          # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up environment variables

Create a `.env` file in the project root:

```env
FLASK_SECRET_KEY=your-secret-key-here
```

Generate a secure secret key:

```bash
python -c "import secrets; print(secrets.token_hex(32))"
```

> Mail variables are optional — only needed if you want password reset emails to work:
> ```env
> MAIL_SERVER=smtp.gmail.com
> MAIL_PORT=587
> MAIL_USE_TLS=true
> MAIL_USERNAME=you@gmail.com
> MAIL_PASSWORD=your-app-password
> MAIL_DEFAULT_SENDER=you@gmail.com
> ```

### 5. Run the app

```bash
python run.py
```

Open your browser at:

```
http://localhost:5001
```

The SQLite database (`users.db`) is created automatically on first run.

---

## Project Structure

```
monthly-expenses-tracker/
├── run.py                    # App entry point
├── requirements.txt          # Python dependencies
├── .env                      # Environment variables (not committed)
├── users.db                  # SQLite database (auto-created)
└── app/
    ├── __init__.py           # Flask app factory
    ├── routes.py             # Main routes (Blueprint)
    ├── auth.py               # Auth routes (login, register, reset)
    ├── models.py             # SQLAlchemy models
    ├── data.py               # Data logic
    ├── email_utils.py        # Password reset email
    ├── templates/
    │   ├── base.html         # Shared layout
    │   ├── dashboard.html    # Stats and charts
    │   ├── expenses.html     # Expense table
    │   ├── settings.html     # Settings page
    │   ├── login.html
    │   ├── register.html
    │   ├── forgot_password.html
    │   └── reset_password.html
    └── static/
        ├── css/
        │   ├── main.css
        │   └── auth.css
        ├── js/
        │   ├── modals.js
        │   ├── dashboard.js
        │   ├── expenses.js
        │   ├── monthly_chart.js
        │   └── gsap_animations.js
        └── Assets/
            └── logo.svg
```

---

## Pages

| Route | Page | Description |
|---|---|---|
| `/` | Dashboard | Overview with stats and charts |
| `/expenses` | Expenses | Full table with add, edit, delete |
| `/settings` | Settings | Update salary, export CSV, reset data |
| `/export` | — | Downloads `budget_export.csv` |
| `/login` | Login | Sign in |
| `/register` | Register | Create account |
| `/forgot-password` | Forgot Password | Request reset link |

---

## License

Licensed under the MIT License. See [LICENSE](./LICENSE).
