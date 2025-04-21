# Attendance Management System

A full-stack attendance management system built with NestJS, React, and MongoDB. This system provides role-based access control for administrators, teachers, and students to manage attendance efficiently.

## Features

- **Role-Based Access Control**
  - Admin: Full system access
  - Teacher: Manage classes and mark attendance
  - Student: View attendance and class information

- **Authentication**
  - JWT-based authentication
  - Password reset functionality
  - Profile management with photo upload

- **Class Management**
  - Create and manage classes
  - Assign teachers to classes
  - Enroll students in classes

- **Attendance Tracking**
  - Mark attendance for students
  - View attendance history
  - Generate attendance reports

## Tech Stack

- **Backend**
  - NestJS (Node.js framework)
  - MongoDB (Database)
  - JWT (Authentication)
  - Multer (File uploads)

- **Frontend**
  - React with TypeScript
  - Material-UI
  - React Router
  - Axios

## Prerequisites

- Node.js (v14 or higher)
- MongoDB
- npm or yarn

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/omsherikar/Attendance.git
   cd Attendance
   ```

2. **Install backend dependencies**
   ```bash
   npm install
   ```

3. **Install frontend dependencies**
   ```bash
   cd frontend
   npm install
   ```

4. **Environment Setup**
   Create a `.env` file in the root directory with the following variables:
   ```
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret
   PORT=3000
   ```

5. **Start the application**
   - Backend:
     ```bash
     npm run start:dev
     ```
   - Frontend:
     ```bash
     cd frontend
     npm start
     ```

## API Documentation

### Authentication

#### Register
- **POST** `/auth/register`
- **Body**:
  ```json
  {
    "name": "string",
    "email": "string",
    "password": "string",
    "role": "string",
    "rollNumber": "string" // Optional, required for students
  }
  ```

#### Login
- **POST** `/auth/login`
- **Body**:
  ```json
  {
    "email": "string",
    "password": "string"
  }
  ```

#### Forgot Password
- **POST** `/auth/forgot-password`
- **Body**:
  ```json
  {
    "email": "string"
  }
  ```

### Classes

#### Create Class
- **POST** `/classes`
- **Body**:
  ```json
  {
    "name": "string",
    "teacherId": "string"
  }
  ```

#### Get Classes
- **GET** `/classes`
- **Query Parameters**:
  - `teacherId`: Filter by teacher
  - `studentId`: Filter by student

### Attendance

#### Mark Attendance
- **POST** `/attendance`
- **Body**:
  ```json
  {
    "classId": "string",
    "date": "string",
    "records": [
      {
        "studentId": "string",
        "status": "string" // "Present", "Absent", "Late"
      }
    ]
  }
  ```

#### Get Attendance
- **GET** `/attendance`
- **Query Parameters**:
  - `classId`: Filter by class
  - `studentId`: Filter by student
  - `date`: Filter by date

## Development

### Backend Structure
```
src/
├── auth/           # Authentication module
├── classes/        # Class management
├── attendance/     # Attendance tracking
├── shared/         # Shared utilities
└── main.ts         # Application entry
```

### Frontend Structure
```
frontend/
├── src/
│   ├── components/     # Reusable UI components
│   ├── contexts/       # React contexts
│   ├── pages/         # Application pages
│   ├── services/      # API services
│   └── App.tsx        # Main component
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support, email [omsherikar0229@gmail.com] or open an issue in the repository. 
