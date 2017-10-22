# Snippet Flask por Sublime Text

## FlaskHello

Hello World

```python
# -*- coding: utf-8 -*-
# Librarys
from flask import Flask, render_template

# Variables
app = Flask(__name__)

# Settings
app.config['DEBUG'] = True
app.config['SECRET_KEY'] = 'secret'


# Views
@app.route('/', methods=('GET', 'POST'))
def index():
    return render_template('name.html')


# Run
if __name__ == '__main__':
    app.run()
```

## FlaskModel

Snippet for Model with: Flask-sqlalchemy, Flask-script and flask-migrate.

```python
# -*- coding: utf-8 -*-
# Librarys
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
from flask_script import Manager
from flask_migrate import Migrate, MigrateCommand

app = Flask(__name__)

# Settings
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///database.sqlite'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

# Variables
db = SQLAlchemy(app)
migrate = Migrate(app, db)
manager = Manager(app)
manager.add_command('db', MigrateCommand)


class MyTable(db.Model):
    '''
    MyTable
    '''
    id = db.Column(db.Integer, primary_key=True)
    column_text = db.Column(db.String(128))
    column_int = db.Column(db.Integer)
	

if __name__ == "__main__":
    manager.run()
```

## FlaskTFlash

Snippet Flash message for Template

```jinja
{% with messages = get_flashed_messages() %}
    {% if messages %}
        {% for message in messages %}
            {{ message }}
        {% endfor %}
    {% endif %}
{% endwith %}   
```

## FlaskTFlashCategories

Snippet Flash message with categories for Template

```jinja
{% with messages = get_flashed_messages(with_categories=true) %}
    {% if messages %}
        {% for category, message in messages %}
            <p class="{{ category }}">{{ message }}</p>
        {% endfor %}
    {% endif %}
{% endwith %}   
```
