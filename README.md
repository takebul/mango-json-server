<div align="center">

<a href="https://mango-books-platform.vercel.app">
  <img src="public/logo.png" alt="Mango Books Logo" width="110" style="border-radius: 24px; box-shadow: 0 10px 25px rgba(245, 158, 11, 0.3);" />
</a>

<br />

# 🥭 Mango Books — Mock REST API Server
### *High-Performance JSON-Server Backend for Mango Books Digital Library*

[![JSON-Server](https://img.shields.io/badge/JSON--Server-v1.0.0--beta.15-blue?style=for-the-badge&logo=json)](https://github.com/typicode/json-server)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-green?style=for-the-badge&logo=node.js)](https://nodejs.org/)
[![Render](https://img.shields.io/badge/Hosted_on-Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)](https://mango-json-server.onrender.com)
[![Frontend](https://img.shields.io/badge/Frontend-mango--books--platform.vercel.app-0070F3?style=for-the-badge&logo=vercel&logoColor=white)](https://mango-books-platform.vercel.app)
[![License](https://img.shields.io/badge/License-ISC-amber?style=for-the-badge)](package.json)

<br />

**[🌐 Live API Base URL](https://mango-json-server.onrender.com)** • **[🚀 Live Frontend App](https://mango-books-platform.vercel.app)** • **[📡 Endpoints](#-api-endpoints-reference)** • **[🛠️ Local Setup](#️-local-development)**

</div>

---

## 📌 Overview

**mango-json-server** is the lightweight, high-performance mock REST API backend powering **Mango Books** ([mango-books-platform.vercel.app](https://mango-books-platform.vercel.app)). Built on top of `json-server`, it serves a curated database of **45 books**, category taxonomies, and user reader reviews with full RESTful querying capabilities, route filtering, and pagination support.

---

## 📊 Database Schema & Endpoints Summary

The server reads from and writes to [`db.json`](db.json), which is partitioned into three core collections:

| Collection | Count | Description | Primary Fields |
| :--- | :---: | :--- | :--- |
| **`books`** | **45** | Master catalog spanning Story, Tech, and Science | `id`, `title`, `author`, `category`, `available_quantity`, `discount`, `imageUrl`, `rating`, `pages`, `language` |
| **`categories`** | **3** | Taxonomy with book counts and descriptions | `id`, `name`, `slug`, `description`, `count` |
| **`reviews`** | **6** | Reader reviews and ratings | `id`, `review`, `reviewer_name`, `reviewer_position`, `rating`, `image` |

---

## 📡 API Endpoints Reference

### Base URL
- **Production**: `https://mango-json-server.onrender.com`
- **Local**: `http://localhost:5000`

---

### 1. Books (`/books`)

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/books` | Retrieve all 45 books in the catalog |
| `GET` | `/books/:id` | Retrieve a single book by ID (e.g. `/books/1`) |
| `GET` | `/books?category=Tech` | Filter books by category (`Story`, `Tech`, `Science`) |
| `GET` | `/books?title_like=Clean` | Case-insensitive title search |
| `GET` | `/books?_sort=rating&_order=desc` | Sort books by rating descending |
| `POST` | `/books` | Add a new book (requires JSON payload) |
| `PATCH` | `/books/:id` | Partially update a book record |
| `DELETE` | `/books/:id` | Remove a book from the catalog |

#### Sample Book Response (`GET /books/1`):
```json
{
  "id": 1,
  "title": "The Crimson Thread",
  "author": "Julian Vance",
  "description": "An intricate web of secrets unravels in a small coastal town after a mysterious artifact is discovered.",
  "category": "Story",
  "available_quantity": 14,
  "discount": "20%",
  "imageUrl": "https://i.ibb.co.com/6RM29rmN/1777902285285.png",
  "rating": 4.8,
  "pages": 384,
  "language": "English"
}
```

---

### 2. Categories (`/categories`)

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/categories` | Retrieve all 3 genre categories with descriptions & counts |
| `GET` | `/categories/:id` | Retrieve a category by ID (e.g. `/categories/1`) |

#### Sample Category Response (`GET /categories/1`):
```json
{
  "id": 1,
  "name": "Story",
  "slug": "story",
  "description": "Immersive novels, mysteries, classics & timeless narratives.",
  "count": 15
}
```

---

### 3. Reviews (`/reviews`)

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/reviews` | Retrieve all 6 reader testimonials and reviewer avatars |
| `GET` | `/reviews/:id` | Retrieve single testimonial by ID |

#### Sample Review Response (`GET /reviews/1`):
```json
{
  "id": 1,
  "review": "A profound masterpiece on the power of persistence. It beautifully illustrates that when you truly want something, the entire universe conspires to help you achieve it.",
  "reviewer_name": "Elena Rossi",
  "reviewer_position": "Creative Director",
  "rating": 5,
  "image": "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150&auto=format&fit=crop&q=80"
}
```

---

## 🛠️ Local Development

### 1. Prerequisites
- **Node.js**: `v18.0.0` or later
- **npm**: `v9.0.0` or later

### 2. Installation
Navigate to the `mango-json-server` directory and install dependencies:
```bash
cd mango-json-server
npm install
```

### 3. Run the Server
```bash
npm run server
```

The server will launch with auto-reload at:
```text
  Index:     http://localhost:5000/
  Books:     http://localhost:5000/books
  Category:  http://localhost:5000/categories
  Reviews:   http://localhost:5000/reviews
```

---

## 🚀 Deployment to Render

To deploy this JSON server to Render as a Web Service:

1. **Repository**: Connect your GitHub repository (`mango-json-server`).
2. **Environment**: `Node`
3. **Build Command**:
   ```bash
   npm install
   ```
4. **Start Command**:
   ```bash
   npx json-server --watch db.json --port $PORT --host 0.0.0.0
   ```
5. **Auto-Deploy**: Enabled on pushes to the `main` branch.

---

## 👨‍💻 Developer & Contact

**Takebul Islam**  
*Full-Stack Web Developer*

- **Portfolio**: [takebulislam.vercel.app](https://takebulislam.vercel.app)
- **Email**: [takebulislam@gmail.com](mailto:takebulislam@gmail.com)
- **GitHub**: [@takebul](https://github.com/takebul)
- **LinkedIn**: [in/takebulislam](https://www.linkedin.com/in/takebulislam)

---

## 📄 License

This project is licensed under the **ISC License**.
