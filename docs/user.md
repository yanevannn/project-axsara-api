## User API Spec

## Get All User

> Endpoint : GET /api/users
Header :

- Authorization: Bearer Token

Query Params

| Parameter | Type   | Required | Default | Description                                              |
| --------- | ------ | -------- | ------- | -------------------------------------------------------- |
| `page`    | number | No       | `1`     | Specifies the page number of results to retrieve.        |
| `size`    | number | No       | `10`    | Specifies the number of user records to return per page. |

**Example Request with Query Params:**

> Endpoint: GET /api/users?page=2&size=5

This will retrieve 5 users from the second page of results.

Response Body (Success) :

```json
{
  "message": "Users retrieved successfully!",
  "data": [
    {
      "id": "1",
      "email": "john@mail.com",
      "firstName": "Jhon",
      "lastName": "Doe",
      "role": "USER"
    },
    {
      "id": "2",
      "email": "jane@mail.com",
      "firstName": "Jane",
      "lastName": "Smith",
      "role": "USER"
    }
    // ... user lainnya
  ],
  "paging": {
    "page": 1,
    "size": 10,
    "total_page": 5,
    "total_data": 50
  }
}
```

Response Body (Failed) :

```json
{
  "errors": "Data users empty"
}
```

## Get User By ID

> Endpoint : GET /api/users/:id
Header :

- Authorization: Bearer Token

Response Body (Success) :

```json
{
  "message": "Users retrieved successfully!",
  "data": {
    "id": "1",
    "email": "john@mail.com",
    "firstName": "Jhon",
    "lastName": "Doe",
    "role": "USER"
  }
}
```

Response Body (Failed) :

```json
{
  "errors": "Users not found"
}
```

## Create User

> Endpoint : POST /api/users
Header :

- Authorization: Bearer Token

Request Body :

```json
{
  "email": "john@mail.com",
  "password": "jhonsecret",
  "fistName": "Jhon",
  "lastName": "Doe",
  "role": "USER" //USER or ADMIN
}
```

Response Body (Success) :

```json
{
  "message": "User created successfully!",
  "data": {
    "id": 1,
    "email": "john@mail.com",
    "password": "jhonsecret",
    "fistName": "Jhon",
    "lastName": "Doe",
    "role": "USER",
    "createdAt": "2025-05-30T17:12:56.219Z",
    "updatedAt": "2025-05-30T17:12:56.219Z"
  }
}
```

Response Body (Failed) :

```json
{
  "errors": "error create users!"
}
```

## Update User by ID

> Endpoint : PATCH /api/users/:id
Header :

- Authorization: Bearer Token

Request Body :

```json
{
  "email": "johndoe@mail.com",
  "fistName": "Jhon",
  "lastName": "Doe",
  "role": "USER" //USER or ADMIN
}
```

Response Body (Success) :

```json
{
  "message": "User update successfully!",
  "data": {
    "id": 1,
    "email": "johndoe@mail.com",
    "fistName": "Jhon",
    "lastName": "Doe",
    "createdAt": "2025-05-30T17:12:56.219Z",
    "updatedAt": "2025-05-30T17:12:56.219Z"
  }
}
```

Response Body (Failed) :

```json
{
  "errors": "Invalid input. All fields (email, password, firstName, lastName) are required."
}
```

## Delete User by ID

> Endpoint : DELETE /api/users/:id
Header :

- Authorization: Bearer Token

Response Body (Success) :

```json
{
  "message": "User deleted successfully!"
}
```

Response Body (Failed) :

```json
{
  "errors": "User not found with ID:id"
}
```
