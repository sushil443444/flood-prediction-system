# Flood Prediction System

A Django-based machine learning web application that predicts whether a flood event is likely based on rainfall and river values. The app loads a pre-trained ML model from `model.joblib` and exposes a simple form interface to accept user input and show predictions.

## Project Overview

This project includes:
- Django backend for the web app
- Machine learning model loaded with `joblib`
- NumPy-based input conversion for prediction
- SQLite database used by Django
- HTML template-based UI

## Technologies and Libraries

The project depends on the following libraries:

- Python 3.9+ (recommended 3.10 or 3.11)
- Django 4.0.5
- NumPy
- joblib
- scikit-learn (used to train the underlying ML model and required for compatibility with the saved model)
- SQLite (built into Python and used by Django)

Optional development tools:
- virtualenv or venv
- Git

## Prerequisites

Before running the project, make sure you have:

1. Python installed
2. `pip` available
3. A command prompt or terminal opened in the project root

## Step-by-Step Setup

### 1. Open the project folder

```powershell
cd path\to\Flood-Prediction-System-new
```

### 2. Create a virtual environment

```powershell
python -m venv venv
```

### 3. Activate the virtual environment

On Windows PowerShell:

```powershell
.\venv\Scripts\Activate.ps1
```

If PowerShell blocks script execution, use:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\venv\Scripts\Activate.ps1
```

### 4. Install project dependencies

```powershell
pip install --upgrade pip
pip install Django==4.0.5 numpy joblib scikit-learn
```

If you are using Python 3.12 or later and run into package compatibility issues, consider using Python 3.10 or 3.11 for best compatibility.

### 5. Apply database migrations

```powershell
python manage.py migrate
```

### 6. Start the Django development server

```powershell
python manage.py runserver
```

Then open the app in your browser:

```text
http://127.0.0.1:8000/flood
```

> The app is mounted under the `/flood` route in `main/urls.py`, so the homepage is not the project root URL.

## How the Application Works

- The app is available at `/flood` and uses the prediction form in the template.
- User enters:
  - rainfall amount
  - river amount
- The values are sent to the Django view.
- The prediction is generated using the saved model file `model.joblib`.
- The result is displayed on the page.

## Project Structure

```text
Flood-Prediction-System-new/
├── flood/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── main/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── templates/
│   └── index.html
├── db.sqlite3
├── main.csv
├── manage.py
├── model.joblib
├── log.py
├── yo.ipynb
├── README.md
└── requirements.txt (if added later)
```

## Important Notes

- The app expects the file `model.joblib` to exist in the project root.
- If `model.joblib` is missing, the app will fail when loading the model.
- The project is a basic demo app and is not production-hardened.
- The default Django secret key and debug mode are configured in `main/settings.py` for local development only.

## Common Troubleshooting

### Model loading error

If you see an error related to the model file, make sure `model.joblib` is present in the project root and you are running the server from the correct directory.

### Module not found errors

If Django or a library is missing, reinstall dependencies:

```powershell
pip install Django==4.0.5 numpy joblib scikit-learn
```

### Server not starting

Check that the virtual environment is activated and confirm you are in the project folder with `manage.py`:

```powershell
python manage.py check
```

## Optional: Create a Requirements File

If you want to save dependencies for easier setup later, run:

```powershell
pip freeze > requirements.txt
```

Then another developer can install them with:

```powershell
pip install -r requirements.txt
```

## License

This project is intended for educational and demonstration purposes.
