Response Format
===============

API response will be in **application/json** format.


Error Response
--------------

An error response will have an **error_code** and **error_description**::

    {
        "error_code": "invalid_token",
        "error_description": "Token is expired"
    }

Success Response
----------------

A success response for a single entity is a hash map, for example::

    {
        "id": 1,
        "key": "value"
    }

Response for a list of entities will be wrapped in **data** section
of the hash map::

    {
        "data": [
            {
                "id": 1,
                "key": "value"
            },
            {
                "id": 2,
                "key": "value"
            }
        ]
    }


Pagination
----------

Pagination is useful when a single array data response can not hold all the
data. In this case, you can fetch the next page::

    {
        "data": [],
        "pagination": {
            "total": 121,
            "perpage": 20,
            "page": 1,
            "pages": 7,
            "prev": null,
            "next": 2
        }
    }

Request pagination with parameters **page**. For example::

    GET /api/resource?page=2

Cursor
------

Cursor is another efficient way to fetch data. When a single array data response
can not hold all the data::

    {
        "data": [],
        "cursor": 10
    }

An array data response will always return with a **pagination** or **cursor**.
