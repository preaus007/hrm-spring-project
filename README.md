# HRM & Project Management System (Backend)

A robust backend service designed to streamline organizational workflows, tracking everything from employee daily productivity to complex project lifecycles and financial deposits. This system provides granular control over organizational data through a RESTful architecture.

## 🚀 Key Modules & Features

### 1. Project & Feature Management
Manages the core work of the organization by breaking down large projects into manageable features.
* **Dynamic Project Lifecycle:** Tracks projects from inception to completion via dedicated `/complete` endpoints.
* **Team Collaboration:** Specialized endpoints to `add-member` or remove members from specific projects and features.
* **Categorization:** Implements a two-tier classification system using `Project Categories` and `Domains` for better filtering and organization.

### 2. Daily Goal & Productivity Analytics
Focuses on individual employee performance and daily output.
* **Daily Tracking:** Employees can log, update, and manage their daily tasks.
* **Carry-Forward Logic:** A unique `PATCH /carry-forward` feature to move uncompleted tasks to the next business day.
* **Performance Analytics:** Provides both individual daily snapshots and broad monthly analytics to track productivity trends over time.
* **Admin Overview:** A dedicated `/admin` view for supervisors to monitor goals across the entire team.

### 3. Financial Management (Cash Deposits)
Handles internal financial transactions or employee-related deposits.
* **Transaction Logging:** Full CRUD support for recording and auditing cash deposits.
* **Traceability:** Every deposit is linked to unique IDs for transparent financial tracking.

### 4. Content & Client Management
* **Blog System:** Integrated internal or external blog management for company updates and knowledge sharing.
* **Client Directory:** Manages client profiles to link projects with specific stakeholders.

---

## 🛠 API Architecture

The system follows standard REST principles with consistent endpoint naming conventions:

| Controller | Purpose | Key Special Endpoints |
| :--- | :--- | :--- |
| **Project** | Project lifecycle & team assignment | `/projects/{id}/complete`, `/add-member` |
| **Daily Goal** | Productivity & Analytics | `/analytics/monthly-analytics/{userId}`, `/carry-forward` |
| **Feature** | Component-level task management | `/features/{id}/add-member` |
| **Cash Deposit** | Financial transaction tracking | Standard CRUD |
| **Category/Domain** | Metadata and filtering options | `/form-filters`, `/filter-options` |

---

## 🚦 Technical Implementation Details

* **State Management:** Uses `PATCH` requests for partial updates (like adding a single team member) to reduce payload size and improve efficiency.
* **Filtering Engine:** Includes specialized `form-filters` and `filter-options` endpoints to provide the frontend with dynamic dropdown data based on existing database entries.
* **Security:** All endpoints are visualized through Swagger/OpenAPI with padlocks indicating integrated **Spring Security** (likely JWT or Session-based).

## 📖 How to Use the API
Access the full interactive documentation via Swagger UI at:
`http://localhost:8080/api/v1/swagger-ui/index.html`
