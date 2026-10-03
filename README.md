# Task Manager Pro 📝⚡

A secure, serverless Progressive Web App (PWA) designed for daily task tracking. It features real-time database syncing, secure PIN-based authentication, and a responsive, modern UI—all built without heavy frontend frameworks.

**🔗 Live Demo:** [Launch Task Manager Pro](https://yashcreateGit.github.io/Task-Manager/)

---

### 🚀 Key Features
* **Secure PIN Authentication:** Frictionless login using a 6-digit PIN, powered securely by Firebase Authentication.
* **Real-Time Cloud Sync:** Tasks instantly save and update across devices using Google Cloud Firestore.
* **Smart Data Filtering:** Filter tasks by Date (anchored to local timezones) and Status (Pending, In Progress, Completed).
* **Chronological Sorting:** Auto-sorts tasks from newest to oldest based on creation and modification timestamps.
* **Installable (PWA):** Can be installed directly to an Android or iOS home screen as a native-feeling application.
* **Zero-Cost Infrastructure:** Hosted entirely on GitHub Pages with a serverless backend.

---

### 🛠 Tech Stack
* **Frontend:** HTML5, CSS3 (Custom Glassmorphism UI), Vanilla JavaScript (ES6 Modules)
* **Backend & Database:** Firebase Authentication, Cloud Firestore (NoSQL)
* **Hosting & Deployment:** GitHub Pages, Git

---

### 🧠 How I Built This (Architecture & Engineering)

This project was engineered to deliver a production-grade experience using a lightweight, 100% free tech stack. Here is the step-by-step development process:

#### 1. Serverless Authentication Strategy
Instead of building a costly backend to handle secure logins, I leveraged **Firebase Authentication**. To streamline the user experience, I engineered a "Username/Email + 6-Digit PIN" login system. The PIN is securely hashed by Firebase just like a standard password, providing enterprise-grade security with a simpler user interface.

#### 2. Database Design & Data Security
I set up a NoSQL **Cloud Firestore** database to handle real-time task operations (CRUD). To guarantee user privacy, I wrote custom **Firestore Security Rules**:
```javascript
match /users/{userId}/tasks/{taskId} {
  allow read, write: if request.auth != null && request.auth.uid == userId;
}
