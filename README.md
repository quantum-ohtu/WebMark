# WebMark

[![MIT Licence](https://badges.frapsoft.com/os/mit/mit.png?v=103)](https://opensource.org/licenses/mit-license.php)

![Python package](https://github.com/ohtu2021-kvantti/WebMark/workflows/Python%20package/badge.svg)

Web platform for benchmarking quantum computing algorithms

## Django - structure

WebMark = Project

WebCLI = Application

Requirements: django, django-on-heroku, gunicorn, django-dotenv

## Setting up the development environment

Install PostgreSQL:

```
sudo apt install postgresql postgresql-contrib libpq-dev python3-dev
```

Create a database:
```
sudo -u postgres psql
postgres=# create database quantdb;
postgres=# create user quantuser with encrypted password 'secret';
postgres=# grant all privileges on database quantdb to quantuser;
postgres=# alter user quantuser createdb; --allow user to create a test database
postgres=# \q
```

Create a .env file in the project root with the following contents:
```
DATABASE_NAME=quantdb
DATABASE_USER=quantuser
DATABASE_PASSWORD=secret
DATABASE_HOST=127.0.0.1
DATABASE_PORT=5432
```

Create and activate a virtual environment:
```
python3 -m venv venv
source venv/bin/activate
```

Install the dependencies:
```
pip install -r requirements.txt
```

Now you can run the development server with command:
```
python manage.py runserver
```

## Heroku

You can push your local PostgreSQL database to Heroku with
```
heroku pg:push postgres://quantuser@localhost/quantdb  postgresql-flexible-07270 --app=quantmark
```


