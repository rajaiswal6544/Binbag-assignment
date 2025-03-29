# User Profile Management API

A simple **User Profile Management API** built using **Node.js, Express.js, MongoDB**, and **JWT authentication**. It allows users to register, log in, retrieve, and update their profiles securely.

## Features
- **User Authentication** (JWT-based)
- **Profile Management** (Create, Retrieve, Update)
- **Password Hashing** (using bcrypt.js)
- **Protected Routes** (Users can only access their own profile)
- **MongoDB Database Support**
- **Error Handling**

## Tech Stack
- **Backend:** Node.js, Express.js
- **Database:** MongoDB (Mongoose ODM)
- **Authentication:** JWT (JSON Web Token)

---

## Getting Started

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/rajaiswal6544/Binbag-assignment.git

```

### 2️⃣ Install Dependencies
```bash
npm install
```

### 3️⃣ Configure Environment Variables
Create a **.env** file in the root directory and add the following:
```
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
```

### 4️⃣ Start the Server
```bash
npm run dev
```

The server should be running at `http://localhost:5000`

---

## API Documentation

### **1️⃣ User Registration**
**Endpoint:** `POST /api/users/register`
- **Headers:** `Content-Type: application/json`
- **Request Body:**
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "password": "123456",
    "address": "123 Main St",
    "bio": "Software Engineer",
    "profilePicture": "http://example.com/john.jpg"
  }
  ```
- **Response:**
  ```json
  { "message": "User registered successfully" }
  ```

---

### **2️⃣ User Login**
**Endpoint:** `POST /api/users/login`
- **Headers:** `Content-Type: application/json`
- **Request Body:**
  ```json
  {
    "email": "john@example.com",
    "password": "123456"
  }
  ```
- **Response:**
  ```json
  { "token": "your_jwt_token_here" }
  ```

Save the **token** to use for authenticated requests.

---

### **3️⃣ Get User Profile (Protected Route)**
**Endpoint:** `GET /api/users/profile`
- **Headers:**
  ```
  Authorization: Bearer your_jwt_token_here
  ```
- **Response:**
  ```json
  {
    "_id": "user_id",
    "name": "John Doe",
    "email": "john@example.com",
    "address": "123 Main St",
    "bio": "Software Engineer",
    "profilePicture": "http://example.com/john.jpg",
    "createdAt": "2025-03-29T12:00:00.000Z"
  }
  ```

---

### **4️⃣ Update User Profile (Protected Route)**
**Endpoint:** `PUT /api/users/profile`
- **Headers:**
  ```
  Authorization: Bearer your_jwt_token_here
  Content-Type: application/json
  ```
- **Request Body:**
  ```json
  {
    "name": "John Updated",
    "address": "456 Updated St",
    "bio": "Senior Software Engineer",
    "profilePicture": "http://example.com/updated.jpg"
  }
  ```
- **Response:**
  ```json
  {
    "_id": "user_id",
    "name": "John Updated",
    "email": "john@example.com",
    "address": "456 Updated St",
    "bio": "Senior Software Engineer",
    "profilePicture": "http://example.com/updated.jpg",
    "updatedAt": "2025-03-29T12:30:00.000Z"
  }
  ```

---

## Running Tests in Postman
1. **Import API requests** into Postman.
2. **Set `{{base_url}}`** as `http://localhost:5000/api/users`.
3. **Automate Token Handling**:
   - In **Tests** tab of Login API, add:
     ```js
     pm.environment.set("auth_token", pm.response.json().token);
     ```
   - Use `{{auth_token}}` in `Authorization: Bearer` header for protected routes.

---

## Deployment
1. Set up MongoDB Atlas or a cloud database.
2. Configure `.env` variables with production values.
3. Use **PM2** for process management:
   ```bash
   npm install pm2 -g
   pm2 start src/app.js --name user-profile-api
   ```
4. Deploy using **Vercel, Heroku, or DigitalOcean**.

---

## Contributing
1. Fork the repository.
2. Create a feature branch.
3. Commit changes and push.
4. Open a Pull Request.

---

## License
This project is licensed under the MIT License.

---

## Contact
For any queries, contact: **rajaiswaldev24@gmail.com**

