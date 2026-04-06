# 🚀 Founder Pulse

**Founder Pulse** is a startup relationship management system designed to help organizations track, manage, and support startups throughout their growth journey from idea to full maturity.

---

## 📌 Overview

Founder Pulse provides a structured way to:

- Manage startup profiles
- Track progress through defined growth stages
- Store and version important documents
- Log key activities and milestones
- Maintain accountability across staff members

---

## 🏗️ Database Schema

### 👤 Staff Profiles

Stores information about system users.

| Field       | Type      | Description                  |
|------------|----------|------------------------------|
| id         | UUID     | Unique identifier            |
| name       | String   | Full name                    |
| email      | String   | Unique staff email           |
| role       | Enum     | Admin, Staff, Viewer         |
| created_at | Timestamp| Account creation date        |

---

### 🚀 Startups

Represents startups being tracked.

| Field          | Type      | Description                        |
|---------------|----------|------------------------------------|
| id            | UUID     | Unique identifier                  |
| startup_name  | String   | Name of startup                    |
| founder_name  | String   | Name of founder                    |
| industry      | String   | Startup industry                   |
| current_stage | Enum     | Ideation, Program, Mentorship, Flourish |
| created_by    | UUID     | Staff who created the record       |
| created_at    | Timestamp| Date added                         |

---

### 📂 Documents (Filing Cabinet)

Stores all uploaded files related to startups.

| Field         | Type      | Description                     |
|--------------|----------|---------------------------------|
| id           | UUID     | Unique document ID              |
| startup_id   | UUID     | Linked startup                  |
| file_name    | String   | File name                       |
| file_url     | String   | Storage link                    |
| document_type| Enum     | Pitch Deck, Business Plan, Report, Other |
| uploaded_by  | UUID     | Staff who uploaded              |
| version      | Integer  | Version number                  |
| created_at   | Timestamp| Upload date                     |

---

### 📊 Milestones (Audit Log)

Tracks important actions and stage transitions.

| Field       | Type      | Description                    |
|------------|----------|--------------------------------|
| id         | UUID     | Unique milestone ID            |
| startup_id | UUID     | Linked startup                 |
| stage      | Enum     | Current stage                  |
| action     | String   | Description of activity        |
| logged_by  | UUID     | Staff responsible              |
| created_at | Timestamp| When it was logged             |

---

## 📈 Growth Stages

Startups move through a defined lifecycle:

1. **Ideation**  
   Default stage when a startup is created  

2. **Program**  
   Triggered when the first pitch deck is uploaded  

3. **Mentorship**  
   Triggered when at least one mentorship session is logged  

4. **Flourish**  
   Triggered when an Admin logs a completion/approval milestone  

---

## ⚙️ System Rules

To ensure consistency and data integrity:

- A startup must always have one current stage  
- Stage progression is **forward-only** (no skipping or reverting)  
- Every stage change must create a **milestone record**  
- Documents are **never deleted**, only versioned  
- Deleting a staff member does **not remove associated records**  

---

## 🧠 Core Concepts

- **Auditability** → Every action is logged  
- **Traceability** → Startup journey is fully trackable  
- **Data Integrity** → Strict progression rules  
- **Scalability** → Structured schema for growth  

---

## 🛠️ Tech Stack (Suggested)

- Frontend: React (Vite)  
- Backend: Supabase / Node.js  
- Database: PostgreSQL  
- Storage: Supabase Storage  

---

## 🚧 Future Improvements

- Dashboard analytics (startup success rate, stage distribution)  
- Role-based access control enhancements  
- Notification system for stage transitions  
- AI-powered startup insights  

---

## 🤝 Contributing

Contributions are welcome! Feel free to fork the repo and submit a pull request.

---

## 📄 License

This project is open-source and available under the MIT License.
