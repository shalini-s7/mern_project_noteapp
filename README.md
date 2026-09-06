# 📝 MERN Note App

A full-stack Note Taking application built using the **MERN stack**.

This project was built to understand how a complete full-stack application works and, more importantly, how the different technologies are **interconnected and communicate with each other**.

Through this project, I learned how **React.js, JavaScript, Tailwind CSS, Node.js, Express.js, REST APIs, middleware, CORS, rate limiting, Mongoose, MongoDB, and deployment** work together to build a real-world web application.

---

## 🚀 Project Overview

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | React.js | Builds the user interface |
| Programming | JavaScript | Handles application logic |
| Styling | Tailwind CSS | Styles the application |
| API Communication | Axios | Sends requests from frontend to backend |
| Backend Runtime | Node.js | Runs the server-side application |
| Backend Framework | Express.js | Creates APIs and handles HTTP requests |
| API | REST API | Connects frontend and backend |
| Middleware | Express Middleware | Processes requests before they reach the route |
| CORS | CORS | Allows communication between different origins |
| Rate Limiting | Upstash Rate Limit | Controls excessive API requests |
| Database | MongoDB | Stores notes |
| ODM | Mongoose | Communicates with MongoDB |

---

## 🏗️ Application Architecture

The application follows a simple full-stack architecture:

```text
                    USER
                      │
                      ▼
              ┌──────────────┐
              │   React.js   │
              │  Frontend    │
              └──────┬───────┘
                     │
                     ▼
                 Axios
                     │
                     ▼
              ┌──────────────┐
              │   REST API   │
              └──────┬───────┘
                     │
                     ▼
          ┌──────────────────────┐
          │ Express.js + Node.js │
          └──────────┬───────────┘
                     │
                     ▼
                Middleware
              ┌──────┼───────┐
              │      │       │
            CORS  Rate Limit  Error Handling
              │      │       │
              └──────┼───────┘
                     │
                     ▼
                Mongoose
                     │
                     ▼
              ┌──────────────┐
              │   MongoDB    │
              └──────────────┘
                     │
                     ▼
                  Response
                     │
                     ▼
                React UI
```

### 🔄 Basic Data Flow

```text
User Action
     ↓
React
     ↓
Axios Request
     ↓
Express API
     ↓
Middleware
     ↓
Route / Controller
     ↓
Mongoose
     ↓
MongoDB
     ↓
Response
     ↓
React
     ↓
Updated UI
```

---

## 📱 Application Pages

The application currently has three main pages:

| Page | Description |
|---|---|
| 🏠 **Home Page** | Displays all notes stored in MongoDB |
| ➕ **Create Note** | Allows the user to create a new note |
| 📝 **Note Detail / Update** | Displays an individual note and allows the user to update or delete it |

---

## 🔄 CRUD Operations

The application implements the basic **CRUD** operations.

| Operation | HTTP Method | Endpoint | Description |
|---|---|---|---|
| Create | `POST` | `/api/notes` | Creates a new note |
| Read | `GET` | `/api/notes` | Retrieves all notes |
| Read One | `GET` | `/api/notes/:id` | Retrieves a specific note |
| Update | `PUT` | `/api/notes/:id` | Updates an existing note |
| Delete | `DELETE` | `/api/notes/:id` | Deletes a note |

---

## 🌐 How the API Works

For example, when a user creates a note:

```text
1. User enters note details
          ↓
2. React collects the data
          ↓
3. Axios sends POST request
          ↓
4. Express receives the request
          ↓
5. Middleware processes the request
          ↓
6. Route/controller handles the request
          ↓
7. Mongoose sends data to MongoDB
          ↓
8. MongoDB stores the note
          ↓
9. Backend sends response
          ↓
10. React updates the UI
```

This helped me understand that the frontend does **not directly communicate with MongoDB**.

Instead:

```text
React → API → Express/Node.js → Mongoose → MongoDB
```

---

## 🛡️ Rate Limiting

This project uses **rate limiting** to control how many requests can be made to the API within a specific time period.

### Why rate limiting?

Without rate limiting, an API could receive too many requests from a client in a short period of time.

Rate limiting helps:

- Protect the API
- Reduce unnecessary traffic
- Prevent request abuse
- Improve application reliability

The project uses **Upstash Redis / Rate Limit** for this functionality.

---

## 🌐 CORS

**CORS (Cross-Origin Resource Sharing)** allows the frontend and backend to communicate when they are running on different origins.

For example:

```text
Frontend
http://localhost:5173

        ↓
      CORS
        ↓

Backend
http://localhost:5001
```

I learned why CORS is required when the frontend and backend are running separately.

---

## 🧩 Middleware

Middleware is a function that runs between the incoming request and the final route handler.

In this project, middleware is used for things such as:

| Middleware / Concept | Purpose |
|---|---|
| CORS | Handles cross-origin requests |
| Rate Limiting | Limits excessive requests |
| Error Handling | Handles errors from the application |
| Request Processing | Processes requests before reaching routes |

The general flow is:

```text
Request
   ↓
Middleware
   ↓
Route
   ↓
Controller
   ↓
Database
   ↓
Response
```

---

## 🗄️ MongoDB & Mongoose

**MongoDB** is used as the database for storing notes.

**Mongoose** is used to interact with MongoDB from the Node.js backend.

```text
Express.js
     ↓
  Mongoose
     ↓
  MongoDB
```

When a note is created:

```text
Frontend
   ↓
POST /api/notes
   ↓
Express
   ↓
Mongoose
   ↓
MongoDB
   ↓
Note Stored
```

When a note is updated:

```text
Frontend
   ↓
PUT /api/notes/:id
   ↓
Express
   ↓
Mongoose
   ↓
MongoDB
   ↓
Existing Note Updated
```

---

## 🛠️ Tech Stack

### Frontend

| Technology | Usage |
|---|---|
| React.js | User interface |
| JavaScript | Frontend logic |
| Tailwind CSS | Styling |
| Axios | API requests |

### Backend

| Technology | Usage |
|---|---|
| Node.js | Server runtime |
| Express.js | Backend framework |
| REST API | Frontend/backend communication |
| Middleware | Request processing |

### Database & Services

| Technology | Usage |
|---|---|
| MongoDB | Database |
| Mongoose | MongoDB interaction |
| Upstash Redis | Rate limiting |
| CORS | Cross-origin communication |

---

## 📚 What I Learned

This project helped me understand the following concepts:

| Concept | What I Learned |
|---|---|
| React.js | Components, pages, state, events and UI structure |
| JavaScript | Application logic and data handling |
| Tailwind CSS | Utility-first CSS and responsive design |
| Axios | Sending HTTP requests to APIs |
| REST API | How frontend and backend communicate |
| Node.js | Running JavaScript on the backend |
| Express.js | Creating servers, routes and APIs |
| Middleware | Processing requests before route handlers |
| CORS | Communication between different origins |
| Rate Limiting | Protecting APIs from excessive requests |
| MongoDB | Storing application data |
| Mongoose | Connecting and working with MongoDB |
| CRUD | Creating, reading, updating and deleting data |
| Environment Variables | Managing configuration and sensitive information |
| Deployment | Understanding how a full-stack application works in production |

---

## 🧪 Environment Variables

Create a `.env` file inside the **backend** folder.

### Backend `.env`

```env
MONGO_URI=<your_mongo_uri>

UPSTASH_REDIS_REST_URL=<your_redis_rest_url>
UPSTASH_REDIS_REST_TOKEN=<your_redis_rest_token>

NODE_ENV=development
```

> ⚠️ **Important:** Never upload your `.env` file to GitHub.

Add the following to `.gitignore`:

```text
.env
node_modules
```

---

## 🔧 Run the Backend

From the project root:

```bash
cd backend
npm install
npm run dev
```

The backend will run on:

```text
http://localhost:5001
```

---

## 💻 Run the Frontend

Open a **new terminal**:

```bash
cd frontend
npm install
npm run dev
```

The frontend will normally run on:

```text
http://localhost:5173
```

---

## 📁 Project Structure

```text
mern_project_noteapp/
│
├── backend/
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routes/
│   │   └── server.js
│   │
│   ├── .env
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   │   ├── HomePage.jsx
│   │   │   ├── CreatePage.jsx
│   │   │   └── NoteDetailPage.jsx
│   │   │
│   │   ├── lib/
│   │   ├── App.jsx
│   │   └── main.jsx
│   │
│   ├── tailwind.config.js
│   └── package.json
│
├── .gitignore
└── README.md
```

---

## 🚀 Deployment

This project also helped me understand the basics of deploying a full-stack application.

In development, the application runs locally:

```text
React
localhost:5173
     ↓
Express
localhost:5001
     ↓
MongoDB
```

After deployment, the same architecture works using production URLs:

```text
User
 ↓
Deployed React Frontend
 ↓
Deployed Backend API
 ↓
MongoDB
```

This helped me understand that deploying a MERN application is not just about deploying the frontend — the **frontend, backend, database, environment variables, and API configuration all need to work together**.

---

## 🎯 Main Goal of the Project

The main goal of this project was **not simply to build a note-taking application**.

I wanted to understand how the different parts of a MERN stack application are connected.

Before this project, technologies such as React, Node.js, Express.js, MongoDB and APIs can feel like separate topics.

This project helped me understand their relationship:

```text
React
  ↓
Axios
  ↓
REST API
  ↓
Express.js
  ↓
Node.js
  ↓
Middleware
  ↓
Mongoose
  ↓
MongoDB
```

and how the response travels back:

```text
MongoDB
   ↓
Mongoose
   ↓
Express.js
   ↓
REST API
   ↓
Axios
   ↓
React
   ↓
Updated UI
```

The project helped me move from learning individual technologies to understanding **how they work together as one complete system**.

---

## 💡 Key Takeaways

- Learned how frontend and backend communicate through APIs.
- Understood how REST APIs work.
- Learned how Express.js handles requests and routes.
- Understood the role of middleware.
- Learned why CORS is required.
- Implemented API rate limiting.
- Learned how Mongoose communicates with MongoDB.
- Implemented CRUD operations.
- Learned how changes in the application are reflected in the MongoDB database.
- Understood how frontend, backend and database are connected during deployment.
- Gained practical experience building a complete MERN stack application.

---

## 👩‍💻 Author

**Shalini S**

GitHub: [@shalini-s7](https://github.com/shalini-s7)

---

⭐ If you found this project useful, consider giving it a star!
