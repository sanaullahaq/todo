# Todo Woo

A Django practice project — a todo list web app with user authentication. Users can sign up, log in, create todos, mark them as important, edit them, complete them, and delete them.

## Features

- User registration, login, and logout (POST-only logout for CSRF safety)
- Create todos with a title, optional memo, and importance flag
- View all incomplete (current) todos — important ones highlighted
- Edit existing todos
- Mark todos as complete (sets a timestamp)
- View all completed todos, ordered by completion date
- Delete todos
- Django admin at `/admin/` for superusers

## Tech Stack

- **Backend:** Django 3.1, Python 3.8, SQLite
- **Frontend:** Bootstrap 4.4, jQuery 3.4
- **Production:** Gunicorn, Whitenoise (static files), Heroku-ready

## Installation

```bash
git clone <repo-url>
cd todo
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Visit `http://127.0.0.1:8000` in your browser.

## Usage

1. **Sign up** at `/signup/` with a username and password.
2. **Create todos** at `/create/` — set a title, optional memo, and mark as important if needed.
3. **View your current todos** at `/current/` — click any todo to edit, complete, or delete it.
4. **View completed todos** at `/completed/`.

## Routes

| URL | View | Description |
|-----|------|-------------|
| `/` | `home` | Landing page |
| `/signup/` | `signupuser` | Register a new account |
| `/login/` | `loginuser` | Log in |
| `/logout/` | `logoutuser` | Log out (POST only) |
| `/current/` | `currenttodos` | List incomplete todos |
| `/completed/` | `completed` | List completed todos |
| `/create/` | `createtodo` | Create a new todo |
| `/todo/<id>/` | `viewtodo` | View / edit a todo |
| `/todo/<id>/complete` | `completetodo` | Mark todo complete (POST) |
| `/todo/<id>/delete` | `deletetodo` | Delete a todo (POST) |

## Deployment

This project is configured for Heroku:

- `Procfile` — runs Gunicorn
- `runtime.txt` — Python 3.8.5
- `ALLOWED_HOSTS` includes `todowolist.herokuapp.com`

Set `DEBUG=False` and use environment variables for `SECRET_KEY` in production.

## License

[MIT](LICENSE)
