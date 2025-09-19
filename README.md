# Contact_Manager_App
A simple Node.js + Express REST API for managing contacts with user authentication (JWT).
Built with MongoDB and Mongoose.

## Features
- User authentication (register, login) with JWT
- CRUD operations for contacts
- MongoDB integration with Mongoose
- Error handling middleware
- Token validation middleware

## Project Structure
```
mycontacts-backend/
│── server.js                 # Entry point
│── package.json              # Dependencies & scripts
│── .env                      # Environment variables
│── config/dbConnection.js    # MongoDB connection
│── controllers/              # Request handlers
│   ├── contactController.js
│   └── userController.js
│── models/                   # Mongoose models
│   ├── contactModel.js
│   └── userModel.js
│── middleware/               # Custom middlewares
│   ├── errorHandler.js
│   └── validateTokenHandler.js
│── constants.js              # HTTP status constants
```

## Installation

1. Clone the repository or extract the zip.
   ```bash
   git clone <repo-url>
   cd mycontacts-backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up .env file:
   ```env
   PORT=5000
   MONGO_URI=your_mongodb_connection_string
   ACCESS_TOKEN_SECRET=your_secret_key
   ```

4. Start the server:
   ```bash
   npm start
   ```

   or with nodemon (dev mode):
   ```bash
   npm run dev
   ```

---

## API Endpoints (with Postman Examples)

###  Authentication

#### 1. Register a User
POST `/api/users/register`  
Body (JSON):
```json
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "secret123"
}
```

#### 2. Login a User
POST `/api/users/login`  
Body (JSON):
```json
{
  "email": "john@example.com",
  "password": "secret123"
}
```
 Response:
```json
{
  "accessToken": "your_jwt_token_here"
}
```

#### 3. Get Current User
GET `/api/users/current`  
Headers:
```
Authorization: Bearer your_jwt_token_here
```

---

###  Contacts

#### 1. Get All Contacts
GET `/api/contacts`  
Headers:
```
Authorization: Bearer your_jwt_token_here
```

#### 2. Create a Contact
POST `/api/contacts`  
Headers:
```
Authorization: Bearer your_jwt_token_here
```
Body (JSON):
```json
{
  "name": "Alice",
  "email": "alice@example.com",
  "phone": "1234567890"
}
```

#### 3. Get Contact by ID
GET `/api/contacts/:id`  
Headers:
```
Authorization: Bearer your_jwt_token_here
```

#### 4. Update a Contact
PUT `/api/contacts/:id`  
Headers:
```
Authorization: Bearer your_jwt_token_here
```
Body (JSON):
```json
{
  "name": "Alice Updated",
  "email": "alice_updated@example.com",
  "phone": "9876543210"
}
```

#### 5. Delete a Contact
DELETE `/api/contacts/:id`  
Headers:
```
Authorization: Bearer your_jwt_token_here
```

---

## Scripts
- `npm start` → Start server
- `npm run dev` → Start with nodemon
- `npm test` → Run tests (if added)

## Tech Stack
- Node.js
- Express.js
- MongoDB + Mongoose
- JWT Authentication
