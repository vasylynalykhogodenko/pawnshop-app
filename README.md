# Pawnshop Management System

A full-stack application for managing pawnshop operations, built with Angular (frontend) and Node.js, Express, MongoDB (backend).

## Table of Contents

- [Pawnshop Management System](#pawnshop-management-system)
  - [Table of Contents](#table-of-contents)
  - [Features](#features)
  - [Technologies](#technologies)
    - [Frontend](#frontend)
    - [Backend](#backend)
  - [Installation](#installation)
  - [API Documentation](#api-documentation)
  - [User Roles](#user-roles)
  - [Authentication](#authentication)
    - [Test Credentials](#test-credentials)
  - [Database Structure](#database-structure)
    - [Main Collections:](#main-collections)
  - [Business Logic](#business-logic)
  - [Contact](#contact)

## Features

- Client management (personal and passport data)
- Item category management
- Pawn transaction processing
- Automatic ownership transfer for overdue items
- Dynamic pricing for items in possession
- Role-based access control
- Comprehensive API documentation

## Technologies

### Frontend

- Angular
- TypeScript
- HTML/CSS
- RxJS

### Backend

- Node.js
- Express
- MongoDB (with Mongoose)
- JWT Authentication
- Swagger for API documentation

## Installation

1. Clone the repository
2. Install dependencies for both frontend and backend:
   ```bash
   cd frontend && npm install
   cd backend && npm install
   ```
3. Configure environment variables (create `.env` file in backend):
   ```
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   PORT=5000
   ```
4. Run the application:

   ```bash
   # In backend directory
   npm start

   # In frontend directory
   ng serve
   ```

## API Documentation

The API is documented using Swagger/OpenAPI. After starting the backend server, access the documentation at:

```
http://localhost:5000/api-docs
```

## User Roles

The system has two types of users with different permissions:

1. **Admin**

   - Full access to all endpoints
   - Can manage item categories
   - Can delete clients and transactions
   - Can view all data

2. **Employee**
   - Can create and manage clients
   - Can create and manage pawn transactions
   - Cannot delete transactions and clients
   - Cannot manage item categories

## Authentication

- All endpoints require JWT Bearer token authentication
- Token must include user role ('Admin' or 'Employee')
- Current UTC time format: YYYY-MM-DD HH:MM:SS

### Test Credentials

```
Admin: email - admin@gmail.com, password - Admin@123
Employee: email - employee@gmail.com, password - Employee@123
```

## Database Structure

### Main Collections:

1. **Clients**

   - First name
   - Last name
   - Middle name
   - Passport number
   - Passport series
   - Passport issue date

2. **Item Categories**

   - Category name
   - Description/notes

3. **Pawn Transactions**
   - Item category reference
   - Client reference
   - Item description
   - Pawn date
   - Return date
   - Loan amount
   - Commission fee
   - Status (active/expired/sold)
   - Price history (for items in possession)

## Business Logic

1. When a client brings an item:

   - Client details are recorded/verified
   - Item is evaluated and categorized
   - Loan amount and commission are determined
   - Transaction is created with return date

2. If client doesn't repay by return date:

   - Item ownership transfers to pawnshop
   - Item becomes available for sale
   - Price can be adjusted multiple times based on market conditions

3. Price tracking:
   - System maintains complete price history for each item
   - Prices can be adjusted up or down
   - Seasonal sales can be implemented (e.g., winter items at end of season)

## Contact

Developer: [vasylynalykhogodenko](https://github.com/vasylynalykhogodenko)
