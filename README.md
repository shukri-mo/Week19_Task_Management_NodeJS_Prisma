# Week 19: Task Management API using Prisma ORM with Supabase

## RESTful API Development and CRUD Operations

## Introduction

- You have learned the basics of Node.js and Express.js, now let's test your knowledge of how to setup API endpoints with this Task Management project using Prisma ORM and Supabase database.

### Task 1: Project Setup

1. Fork and Clone this project repository in your terminal
2. CD into the project base directory `cd Week19_Task_Management_NodeJS_Prisma`
3. Install dependencies:
   ```bash
   npm install
   ```
4. Create a `.env` file in the root directory with your Supabase database URL
5. Complete the Prisma schema and service functions (see tasks below)
6. Generate Prisma client and push schema to database:
   ```bash
   npx prisma generate
   npx prisma db push
   ```
7. Start the server:
   ```bash
   npm run dev
   ```
8. The server will run on `http://localhost:3000`

### Task 2: Understanding the Current Implementation

The project currently has a basic task management API with the following structure:

#### Current API Endpoints

**Main Task Operations:**

- `GET /api/tasks` - Get all tasks
- `GET /api/tasks/:id` - Get task by ID ⚠️ **YOU NEED TO COMPLETE THIS**
- `POST /api/tasks` - Create new task ⚠️ **YOU NEED TO COMPLETE THIS**
- `PUT /api/tasks/:id` - Update entire task (Already implemented)
- `DELETE /api/tasks/:id` - Delete specific task (Already implemented)

#### Data Structure

Each task has the following structure:

```json
{
  "id": "cmdsdprqh0000gtd47ipm0qrx",
  "title": "Task Title",
  "description": "Task description",
  "status": "pending|in-progress|completed|cancelled",
  "priority": "low|medium|high|urgent",
  "dueDate": "2024-01-15",
  "assignedTo": "John Doe",
  "subtasks": [
    {
      "id": "cmdsdq3z50002gtd4okxc927x",
      "title": "Subtask Title",
      "description": "Subtask description",
      "completed": false
    }
  ],
  "createdAt": "2024-01-01T10:00:00.000Z",
  "updatedAt": "2024-01-01T10:00:00.000Z"
}
```

### Task 3: MVP Requirements (Minimum Viable Product)

You need to complete the following:

#### 1. Complete Prisma Schema - `prisma/schema.prisma`

**Location:** `prisma/schema.prisma`

The schema file is partially completed. You need to:

- Complete the Subtask model with all required fields
- Complete the TaskStatus enum with values: pending, in_progress, completed, cancelled
- Complete the Priority enum with values: low, medium, high, urgent

#### 2. Configure Environment Variables - `.env`

**Location:** `.env`

- Add your Supabase database URL
- Set the application port and environment

#### 3. Complete getTaskById Function - `services/taskServices.js`

**Location:** `services/taskServices.js` - getTaskById function

The function structure is provided. You need to:

- Use Prisma to find the task by ID
- Include subtasks in the result
- Handle cases where task doesn't exist
- Return the task or null if not found

#### 4. Complete createTask Function - `services/taskServices.js`

**Location:** `services/taskServices.js` - createTask function

The function structure is provided. You need to:

- Create the new task using Prisma
- Create subtasks if provided in taskData.subtasks
- Include subtasks in the response
- Handle validation errors from Prisma

### Task 4: Testing Your Implementation

You can use Postman or curl to test your endpoints.

### Task 5: Stretch Goals

#### Add Task Filtering

**Objective:** Add filtering capabilities to the GET /api/tasks endpoint.

**Requirements:**

1. **Update the getAllTasks function** in `services/taskServices.js` to accept filters
2. **Add query parameter support** for filtering by status, priority, or assignedTo
3. **Implement search functionality** for task titles
4. **Add pagination** for large datasets

#### Add Task Categories

**Objective:** Add category support to tasks.

**Requirements:**

1. **Create a Category model** in the Prisma schema
2. **Add category relationship** to tasks
3. **Update the Task model** to include categoryId
4. **Implement category-based filtering**

#### Add User Authentication

**Objective:** Integrate Supabase Auth for user management.

**Requirements:**

1. **Add User model** to the Prisma schema
2. **Integrate Supabase Auth** for authentication
3. **Add user ownership** to tasks
4. **Implement user-based access control**

## Learning Objectives

By completing this project, you will demonstrate understanding of:

1. **Prisma ORM Setup** - Database schema design and Prisma client configuration
2. **Supabase Integration** - Cloud database setup and connection
3. **RESTful API Design** - Proper endpoint naming and HTTP methods
4. **Data Validation** - Input validation and sanitization using Prisma
5. **Error Handling** - HTTP status codes and error responses
6. **Express.js Routing** - Route parameters and query strings
7. **Async/Await** - Handling asynchronous database operations
8. **Service Layer Architecture** - Separating business logic from routes

## Submission Format

- [ ] Complete the Prisma schema with all required models and relationships
- [ ] Configure environment variables with Supabase credentials
- [ ] Implement getTaskById function with proper error handling
- [ ] Implement createTask function with validation and subtask support
- [ ] Test all endpoints using curl or Postman
- [ ] Optional: Implement stretch goals with filtering and categories

## Getting Help

1. **Check the existing code** - Study the implemented functions for patterns
2. **Read Prisma documentation** - Understand the Prisma client methods
3. **Check Supabase dashboard** - Verify your database connection
4. **Test frequently** - Test each function as you build it
5. **Ask questions** - Don't hesitate to ask for clarification

Good luck with your implementation! 🚀
