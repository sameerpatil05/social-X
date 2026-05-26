# SocialeX — Social Media App (MERN Stack)

A full-stack social media application built with the MERN stack (MongoDB, Express.js, React.js, Node.js) and real-time communication powered by Socket.io.

---

## 📸 Screenshots

| Landing Page | Home Page | Chat |
|---|---|---|
| Login & Register | Stories + Posts Feed | Real-time Messaging |

---

## ✨ Features

- 🔐 **User Authentication** — Register, Login, Logout with JWT tokens
- 📸 **Create Posts** — Upload photos and videos with description and location
- ❤️ **Like & Comment** — Interact with posts in real-time
- 📖 **Stories** — Add stories that auto-delete after 24 hours
- 💬 **Real-time Chat** — Message friends with Socket.io (text + media)
- 👤 **Profile Management** — View and edit profile, username, about section
- 👥 **Follow System** — Follow/unfollow users, auto-create chat on mutual follow
- 🔔 **Notifications** — Real-time activity notifications
- 🔍 **Search** — Search for users by username
- 📱 **Responsive UI** — Built with Bootstrap for all screen sizes

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| React.js | UI Library |
| Socket.io-client | Real-time communication |
| Bootstrap | Styling & responsive design |
| Axios | HTTP requests |
| React Router DOM | Client-side routing |
| React Icons | Icon library |

### Backend
| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Express.js | Web framework & REST API |
| Socket.io | Real-time bidirectional events |
| Mongoose | MongoDB ODM |
| Bcrypt | Password hashing |
| JWT | Authentication tokens |
| Dotenv | Environment variables |
| CORS | Cross-origin requests |

### Database
| Technology | Purpose |
|---|---|
| MongoDB | NoSQL database (local or Atlas) |

---

## 📁 Project Structure

```
SocialeX/
├── client/                        # React Frontend
│   └── src/
│       ├── components/
│       │   ├── chat/
│       │   │   ├── Chats.jsx      # Friends/chat list
│       │   │   ├── Messages.jsx   # Chat window
│       │   │   ├── Input.jsx      # Message input
│       │   │   ├── Sidebar.jsx    # Chat sidebar
│       │   │   └── UserChat.jsx   # Individual chat item
│       │   ├── CreatePost.jsx     # Post creation modal
│       │   ├── CreateStory.jsx    # Story creation
│       │   ├── HomeLogo.jsx       # App logo
│       │   ├── Login.jsx          # Login form
│       │   ├── Navbar.jsx         # Navigation bar
│       │   ├── Notifications.jsx  # Notifications panel
│       │   ├── Post.jsx           # Posts feed
│       │   ├── Register.jsx       # Register form
│       │   ├── Search.jsx         # User search
│       │   └── Stories.jsx        # Stories display
│       ├── context/
│       │   ├── AuthenticationContextProvider.jsx
│       │   ├── GeneralContextProvider.jsx
│       │   └── SocketContextProvider.jsx
│       ├── pages/
│       │   ├── Chat.jsx           # Chat page
│       │   ├── Home.jsx           # Home feed
│       │   ├── LandingPage.jsx    # Landing/auth page
│       │   └── Profile.jsx        # User profile
│       └── RouteProtectors/
│           ├── AuthProtector.jsx  # Protect private routes
│           └── LoginProtector.jsx # Redirect logged-in users
│
└── server/                        # Node.js Backend
    ├── controllers/
    │   ├── Auth.js                # Register & Login logic
    │   └── Posts.js               # Post CRUD operations
    ├── middleware/
    │   └── auth.js                # JWT verification
    ├── models/
    │   ├── Chats.js               # Chat schema
    │   ├── Post.js                # Post schema
    │   ├── Stories.js             # Story schema (24hr TTL)
    │   └── Users.js               # User schema
    ├── routes/
    │   └── Route.js               # API routes
    ├── SocketHandler.js           # All Socket.io events
    ├── index.js                   # Server entry point
    └── .env                       # Environment variables
```

---

## ⚙️ Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/) (v14 or higher)
- [MongoDB](https://www.mongodb.com/try/download/community) (local) or [MongoDB Atlas](https://www.mongodb.com/atlas) (cloud)
- [Git](https://git-scm.com/downloads)

---

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/SocialeX.git
cd SocialeX
```

### 2. Setup Server

```bash
cd server
npm install
```

Create a `.env` file inside the `server` folder:

```env
PORT=6001
MONGO_URI=mongodb://localhost:27017/socialeX
JWT_SECRET=your_secret_key_here
```

> For MongoDB Atlas, replace `MONGO_URI` with your Atlas connection string:
> ```
> MONGO_URI=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/socialeX?retryWrites=true&w=majority
> ```

### 3. Setup Client

```bash
cd ../client
npm install
```

---

## ▶️ Running the App

You need **3 separate terminals**:

**Terminal 1 — Start MongoDB (if using local):**
```bash
mongod
```

**Terminal 2 — Start Server:**
```bash
cd server
npm start
```
You should see: `Running @ 6001`

**Terminal 3 — Start Client:**
```bash
cd client
npm start
```

Open your browser and go to: **http://localhost:3000**

---

## 🗄️ Database Collections

| Collection | Description |
|---|---|
| `users` | User profiles, followers, following |
| `posts` | Posts with file, likes, comments |
| `stories` | Stories with 24-hour auto-delete (TTL) |
| `chats` | Chat rooms with message history |

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login user, returns JWT token |

---

## 🔁 Socket.io Events

### Client → Server
| Event | Description |
|---|---|
| `addUser` | Register user as online |
| `fetch-all-posts` | Get all posts |
| `create-post` | Create a new post |
| `postLiked` | Like a post |
| `postUnLiked` | Unlike a post |
| `makeComment` | Add comment to post |
| `delete-post` | Delete a post |
| `fetch-profile` | Get user profile |
| `updateProfile` | Update profile details |
| `followUser` | Follow a user |
| `unFollowUser` | Unfollow a user |
| `fetch-friends` | Get mutual followers (friends) |
| `fetch-messages` | Get chat messages |
| `new-message` | Send a message |
| `create-new-story` | Upload a story |
| `fetch-stories` | Get all stories |

### Server → Client
| Event | Description |
|---|---|
| `all-posts-fetched` | Returns posts array |
| `profile-fetched` | Returns user profile |
| `friends-data-fetched` | Returns friends list |
| `messages-updated` | Returns chat messages |
| `stories-fetched` | Returns stories array |
| `getUsers` | Returns online users |
| `likeUpdated` | Triggers post refresh |
| `userFollowed` | Returns updated following list |

---

## 👥 Application Flow

1. User registers or logs in on the **Landing Page**
2. After login, redirected to **Home Page** showing posts feed and stories
3. User can **create posts** (photo/video) — stored as base64 in MongoDB
4. User can **like, comment** on posts in real-time
5. User can **follow** other users — mutual follow unlocks **chat**
6. User can **message** friends with text and media
7. User can **add stories** that auto-delete after 24 hours
8. User can **edit profile** (username, about, profile picture)

---

## 📋 Project Details

| Detail | Info |
|---|---|
| Project Title | SocialeX — Social Media App (MERN) |
| Category | Full Stack Development |
| Duration | 30 Days |
| Team | SP |
| Mentor | Syed |

---

## 🧑‍💻 Skills Used

`HTML` `CSS` `JavaScript` `Bootstrap` `React.js` `Node.js` `Express.js` `MongoDB` `Socket.io` `JWT` `REST API`

---

## 📄 License

This project is for educational purposes as part of an internship program.

---

## 🙏 Acknowledgements

- [Socket.io Documentation](https://socket.io/docs/)
- [MongoDB Documentation](https://www.mongodb.com/docs/)
- [React Documentation](https://react.dev/)
- [Express.js Documentation](https://expressjs.com/)
