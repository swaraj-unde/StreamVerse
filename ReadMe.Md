# 🚀 StreamVerse

A modern and scalable backend API platform for video streaming, social interaction, and content management built using Node.js, Express.js, and MongoDB.

StreamVerse provides a complete backend infrastructure for handling videos, users, playlists, subscriptions, tweets, comments, likes, authentication, and media uploads with secure JWT authentication and Cloudinary integration.

---

# 📖 Table of Contents

- [Overview](#-overview)
- [Tech Stack](#-tech-stack)
- [Features](#-features)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Environment Variables](#-environment-variables)
- [Running the Application](#-running-the-application)
- [API Endpoints](#-api-endpoints)
- [Database Models](#-database-models)
- [Authentication](#-authentication)
- [Error Handling](#-error-handling)
- [Future Improvements](#-future-improvements)

---

# 🎯 Overview

StreamVerse is a feature-rich backend system designed for media-sharing and social engagement platforms.

The application supports:

- Video uploads and management
- User authentication and profiles
- Likes and comments
- Tweets and social interactions
- Channel subscriptions
- Playlist creation and management
- Dashboard analytics

The project follows a modular MVC architecture with scalable folder organization and reusable utilities.

---

# 🛠️ Tech Stack

## Backend

- Node.js
- Express.js

## Database

- MongoDB
- Mongoose

## Authentication & Security

- JWT (jsonwebtoken)
- bcrypt

## Media Uploads

- Cloudinary
- Multer

## Middleware & Utilities

- CORS
- cookie-parser
- dotenv

## Development Tools

- Nodemon
- Prettier

## Pagination

- mongoose-aggregate-paginate-v2

---

# ✨ Features

## 👤 User Management

- User registration & login
- JWT Authentication (Access & Refresh Tokens)
- Secure password hashing with bcrypt
- Profile management
- Avatar & cover image uploads
- Watch history tracking

## 🎥 Video Management

- Upload videos with thumbnails
- Publish/unpublish videos
- Video metadata management
- Video pagination & filtering
- View count tracking

## 💬 Social Features

- Like videos, comments, and tweets
- Comment on videos
- Create and manage tweets
- Subscribe to channels
- Playlist management

## 📊 Dashboard Features

- Channel statistics
- Video analytics
- Subscriber information

## ☁️ Media Handling

- Cloudinary integration
- Multer file uploads
- Image & video upload support

---

# 🏗️ Architecture

StreamVerse follows the **MVC (Model-View-Controller)** architecture pattern.

```bash
src/
├── models/
├── controllers/
├── routes/
├── middlewares/
├── utils/
├── db/
├── app.js
├── index.js
└── constants.js
```

### Request Flow

```bash
Request
   ↓
Routes
   ↓
Middlewares
   ↓
Controllers
   ↓
Models
   ↓
Database
   ↓
Response
```

---

# 📂 Project Structure

```bash
StreamVerse/
├── public/
│   └── temp/
│
├── src/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middlewares/
│   ├── utils/
│   ├── db/
│   ├── app.js
│   ├── index.js
│   └── constants.js
│
├── .env
├── .env.example
├── .gitignore
├── .prettierrc
├── .prettierignore
├── package.json
├── package-lock.json
└── README.md
```

---

# ⚙️ Installation

## Prerequisites

- Node.js (v14+)
- MongoDB
- Cloudinary Account
- npm or yarn

---

## Clone Repository

```bash
git clone <repository-url>
cd streamverse
```

---

## Install Dependencies

```bash
npm install
```

---

## Setup Environment Variables

Create a `.env` file in the root directory.

---

# 🔐 Environment Variables

```env
# Server
PORT=8000

# Database
MONGODB_URI=your_mongodb_uri
DB_NAME=streamverse

# JWT
ACCESS_TOKEN_SECRET=your_access_secret
ACCESS_TOKEN_EXPIRY=1d

REFRESH_TOKEN_SECRET=your_refresh_secret
REFRESH_TOKEN_EXPIRY=10d

# Cloudinary
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# CORS
CORS_ORIGIN=http://localhost:3000

# Environment
NODE_ENV=development
```

---

# 🚀 Running the Application

## Development Mode

```bash
npm run dev
```

---

## Production Mode

```bash
node src/index.js
```

---

## Server Output

```bash
Server is listening on port 8000
MongoDB connected successfully
```

---

# 📡 API Endpoints

## Base URL

```bash
http://localhost:8000/api/v1
```

---

# ❤️ Health Check

| Method | Endpoint       | Description          |
| ------ | -------------- | -------------------- |
| GET    | `/healthcheck` | Server health status |

---

# 👤 User Routes

| Method | Endpoint                       | Description          |
| ------ | ------------------------------ | -------------------- |
| POST   | `/users/register`              | Register user        |
| POST   | `/users/login`                 | Login user           |
| POST   | `/users/logout`                | Logout user          |
| POST   | `/users/refresh-token`         | Refresh access token |
| GET    | `/users/current-user`          | Get current user     |
| PATCH  | `/users/profile`               | Update profile       |
| PATCH  | `/users/avatar`                | Update avatar        |
| PATCH  | `/users/cover-image`           | Update cover image   |
| POST   | `/users/change-password`       | Change password      |
| GET    | `/users/:userId`               | Get user profile     |
| GET    | `/users/:userId/watch-history` | Get watch history    |

---

# 🎥 Video Routes

| Method | Endpoint                          | Description          |
| ------ | --------------------------------- | -------------------- |
| GET    | `/videos`                         | Get all videos       |
| POST   | `/videos/publish`                 | Publish video        |
| GET    | `/videos/:videoId`                | Get video            |
| PATCH  | `/videos/:videoId`                | Update video         |
| DELETE | `/videos/:videoId`                | Delete video         |
| PATCH  | `/videos/:videoId/toggle-publish` | Toggle publish state |

---

# 💬 Comment Routes

| Method | Endpoint               | Description    |
| ------ | ---------------------- | -------------- |
| GET    | `/comments/:videoId`   | Get comments   |
| POST   | `/comments/:videoId`   | Add comment    |
| PATCH  | `/comments/:commentId` | Update comment |
| DELETE | `/comments/:commentId` | Delete comment |

---

# 👍 Like Routes

| Method | Endpoint                           | Description         |
| ------ | ---------------------------------- | ------------------- |
| POST   | `/likes/toggle/video/:videoId`     | Toggle video like   |
| POST   | `/likes/toggle/comment/:commentId` | Toggle comment like |
| POST   | `/likes/toggle/tweet/:tweetId`     | Toggle tweet like   |

---

# 🐦 Tweet Routes

| Method | Endpoint               | Description     |
| ------ | ---------------------- | --------------- |
| POST   | `/tweets`              | Create tweet    |
| GET    | `/tweets/user/:userId` | Get user tweets |
| PATCH  | `/tweets/:tweetId`     | Update tweet    |
| DELETE | `/tweets/:tweetId`     | Delete tweet    |

---

# 📺 Subscription Routes

| Method | Endpoint                            | Description           |
| ------ | ----------------------------------- | --------------------- |
| POST   | `/subscriptions/toggle/:channelId`  | Subscribe/unsubscribe |
| GET    | `/subscriptions/channel/:channelId` | Channel subscribers   |
| GET    | `/subscriptions/user`               | User subscriptions    |

---

# 📁 Playlist Routes

| Method | Endpoint                                      | Description     |
| ------ | --------------------------------------------- | --------------- |
| POST   | `/playlist`                                   | Create playlist |
| GET    | `/playlist/:playlistId`                       | Get playlist    |
| PATCH  | `/playlist/:playlistId`                       | Update playlist |
| DELETE | `/playlist/:playlistId`                       | Delete playlist |
| POST   | `/playlist/:playlistId/add-video/:videoId`    | Add video       |
| DELETE | `/playlist/:playlistId/remove-video/:videoId` | Remove video    |

---

# 📊 Dashboard Routes

| Method | Endpoint            | Description              |
| ------ | ------------------- | ------------------------ |
| GET    | `/dashboard/stats`  | Channel statistics       |
| GET    | `/dashboard/videos` | Channel videos analytics |

---

# 🗄️ Database Models

## User Model

```js
{
  userName: String,
  email: String,
  fullName: String,
  avatar: String,
  coverImage: String,
  password: String,
  refreshToken: String,
  watchHistory: [ObjectId]
}
```

---

## Video Model

```js
{
  videoFile: String,
  thumbnail: String,
  title: String,
  description: String,
  duration: Number,
  views: Number,
  isPublished: Boolean,
  owner: ObjectId
}
```

---

## Comment Model

```js
{
  content: String,
  video: ObjectId,
  owner: ObjectId
}
```

---

## Like Model

```js
{
  video: ObjectId,
  comment: ObjectId,
  tweet: ObjectId,
  likedBy: ObjectId
}
```

---

## Tweet Model

```js
{
  content: String,
  owner: ObjectId
}
```

---

## Subscription Model

```js
{
  subscriber: ObjectId,
  channel: ObjectId
}
```

---

## Playlist Model

```js
{
  name: String,
  description: String,
  videos: [ObjectId],
  owner: ObjectId
}
```

---

# 🔐 Authentication

StreamVerse uses JWT-based authentication.

## Access Token

- Used for protected routes
- Short expiry duration

## Refresh Token

- Used to generate new access tokens
- Longer expiry duration

Tokens can be sent via:

- Cookies
- Authorization Header

Example:

```http
Authorization: Bearer <token>
```

---

# ⚠️ Error Handling

The project uses:

- Custom `ApiError` class
- `asyncHandler` wrapper
- Standardized API responses

### Success Response

```json
{
    "statusCode": 200,
    "message": "Success",
    "data": {},
    "success": true
}
```

### Error Response

```json
{
    "statusCode": 400,
    "message": "Something went wrong",
    "data": null,
    "errors": [],
    "success": false
}
```

---

# 🔥 Key Highlights

- JWT Authentication
- Refresh Token System
- Cloudinary Media Uploads
- MVC Architecture
- Modular Codebase
- RESTful APIs
- Playlist & Subscription Features
- Social Interaction Support
- Pagination Support
- Secure Password Hashing

---

# 🚧 Future Improvements

- Real-time notifications
- Recommendation system
- Advanced search & filtering
- Video transcoding
- Live streaming
- Analytics dashboard improvements
- Content moderation
- Social sharing features

---

# 👨‍💻 Author

**Swaraj Unde**

---

# ⭐ Support

If you found this project useful, consider giving it a ⭐ on GitHub.

---

# 🌟 StreamVerse

A scalable backend platform for media streaming and social interaction.
