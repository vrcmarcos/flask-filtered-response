# Flask Filtered Response

Add filter capability to JSON responses

[![Build Status](https://travis-ci.org/vrcmarcos/flask-filtered-response.svg?branch=master)](https://travis-ci.org/vrcmarcos/flask-filtered-response) [![Coverage Status](https://coveralls.io/repos/github/vrcmarcos/flask-filtered-response/badge.svg?branch=master)](https://coveralls.io/github/vrcmarcos/flask-filtered-response?branch=master) [![PyPI version](https://badge.fury.io/py/Flask-Filtered-Response.svg)](https://badge.fury.io/py/Flask-Filtered-Response) [![Code Health](https://landscape.io/github/vrcmarcos/flask-filtered-response/master/landscape.svg?style=flat)](https://landscape.io/github/vrcmarcos/flask-filtered-response/master) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/vrcmarcos/flask-filtered-response/master/LICENSE)

## Instalation

```bash
pip install Flask-Filtered-Response
```

## Usage

To use Flask Filtered Response, decorate your view with *@filtered* decorator:

```python
import json
from flask_filtered_response import filtered

@app.route('/filtered/single_node')
@filtered
def single_node():
    response_dict = {
        'test_int': 123,
        'test_string': 'Hey!',
    }
    return Response(json.dumps(response_dict))
```

Using *@filtered* decorator, you will enable the ability to use the query string *fields*:

- Request:
    ```bash
    curl -X GET http://localhost:5000/filtered/single_node?fields=test_int
    ```
  
- Response:
    ```json
    {
        "test_int": 123
    }
    ```

You can filter for multiple fields using **, (comma)**. Nested fields filtering is currently **NOT** supported.

## Changelog

#### 1.0.0:
- **@filtered**: Created **@filtered** decorator