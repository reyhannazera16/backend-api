# Laravel Backend Test API

> **Backend Developer Test Submission for PT SKK**  
> **Candidate:** Reyhan Nazera Rusmana  
> **Position:** Backend Developer  
> **Framework:** Laravel 11 with Sanctum Authentication

## 📋 Project Overview

This project implements a complete REST API authentication system using Laravel 11 and Laravel Sanctum. It demonstrates modern backend development practices including user registration, authentication, and protected routes.

### 🎯 Requirements Fulfilled

✅ **API Register User** - Complete user registration with validation  
✅ **API Authentication** - Login system with access token generation  
✅ **API Get User Data** - Protected route using access token  
✅ **Laravel Sanctum** - Token-based authentication implementation  
✅ **Complete Documentation** - Postman collection and setup guide

## 🚀 Features

- **User Registration** with comprehensive validation
- **JWT-like Token Authentication** using Laravel Sanctum
- **Protected Routes** with middleware authentication
- **Error Handling** with proper HTTP status codes
- **API Documentation** with Postman collection
- **Professional Code Structure** following Laravel best practices

## 🛠️ Tech Stack

- **Laravel 11** - Latest PHP framework
- **Laravel Sanctum** - API authentication
- **MySQL** - Database
- **PHP 8.2+** - Programming language
- **Composer** - Dependency management

## 📁 Project Structure

```
backend-test-api/
├── app/
│   ├── Http/Controllers/Api/
│   │   ├── AuthController.php          # Authentication endpoints
│   │   └── UserController.php          # User data endpoints
│   └── Models/
│       └── User.php                     # User model with Sanctum
├── routes/
│   └── api.php                          # API routes definition
├── database/migrations/                 # Database schema
├── Backend Test API - Reyhan Nazera Rusmana.postman_collection.json            # Complete API testing collection
└── README.md                           # This file
```

## ⚡ Quick Start

### Prerequisites

- PHP 8.2 or higher
- Composer
- MySQL/PostgreSQL
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/reyhannazera16/backend-api.git
   cd backend-api
   ```

2. **Install dependencies**
   ```bash
   composer install
   ```

3. **Environment setup**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Configure database** in `.env`
   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=backend_test_api
   DB_USERNAME=root
   DB_PASSWORD=your_password
   ```

5. **Install Sanctum and setup API**
   ```bash
   composer require laravel/sanctum
   php artisan install:api
   ```

6. **Run migrations**
   ```bash
   php artisan migrate
   ```

7. **Start the server**
   ```bash
   php artisan serve
   ```

The API will be available at `http://localhost:8000`

## 📚 API Documentation


### Endpoints

#### 1. Register User
**POST** `/auth/register`

**Request Body:**
```json
{
    "name": "Reyhan Nazera Rusmana",
    "email": "reyhan@example.com",
    "password": "password123",
    "password_confirmation": "password123"
}
```

**Response (201):**
```json
{
    "status": "success",
    "message": "User registered successfully",
    "data": {
        "user": {
            "id": 1,
            "name": "Reyhan Nazera Rusmana",
            "email": "reyhan@example.com",
            "created_at": "2025-06-21T10:30:00.000000Z"
        }
    }
}
```

#### 2. Login User
**POST** `/auth/login`

**Request Body:**
```json
{
    "email": "reyhan@example.com",
    "password": "password123"
}
```

**Response (200):**
```json
{
    "status": "success",
    "message": "Login successful",
    "data": {
        "user": {
            "id": 1,
            "name": "Reyhan Nazera Rusmana",
            "email": "reyhan@example.com"
        },
        "access_token": "1|abcdefgh123456789...",
        "token_type": "Bearer"
    }
}
```

#### 3. Get User Profile (Protected)
**GET** `/user/profile`

**Headers:**
```
Authorization: Bearer {access_token}
Accept: application/json
```

**Response (200):**
```json
{
    "status": "success",
    "message": "User data retrieved successfully",
    "data": {
        "user": {
            "id": 1,
            "name": "Reyhan Nazera Rusmana",
            "email": "reyhan@example.com",
            "email_verified_at": null,
            "created_at": "2025-06-21T10:30:00.000000Z",
            "updated_at": "2025-06-21T10:30:00.000000Z"
        }
    }
}
```

#### 4. User Endpoint 
**GET** `/user`

**Headers:**
```
Authorization: Bearer {access_token}
Accept: application/json
```

**Response (200):**
```json
{
    "status": "success",
    "data": {
        "id": 1,
        "name": "Reyhan Nazera Rusmana",
        "email": "reyhan@example.com",
        "created_at": "2025-06-21T10:30:00.000000Z",
        "updated_at": "2025-06-21T10:30:00.000000Z"
    }
}
```

### HTTP Status Codes

- `200` - Success
- `201` - Created
- `401` - Unauthorized
- `409` - Conflict (user already exists)
- `422` - Validation Error
- `500` - Internal Server Error

## 🧪 Testing with Postman

### Import Collection

1. Download `Backend Test API - Reyhan Nazera Rusmana.postman_collection.json` from this repository
2. Open Postman → **Import** → **Upload Files**
3. Select the downloaded JSON file
4. Create environment with variable: `base_url = http://localhost:8000`

### Testing Flow

1. **Register User** → Creates new user account
2. **Login User** → Returns access token (auto-saved)
3. **Get User Profile** → Uses saved token automatically
4. **Logout** → Revokes token

### Advanced Features

- ✅ **Automatic token management** - Token saved and used automatically
- ✅ **Comprehensive testing** - All responses validated
- ✅ **Error handling** - Proper error messages and status codes
- ✅ **Console feedback** - Clear success/error messages

## 🔧 Development

### Running Tests

```bash
# Run Laravel tests
php artisan test
```

### Debugging

```bash
# Clear all caches
php artisan config:clear
php artisan cache:clear
php artisan route:clear

# View routes
php artisan route:list --path=api

# Check logs
tail -f storage/logs/laravel.log
```

## 🚀 Deployment

### Production Setup

1. **Environment configuration**
   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```

2. **Database optimization**
   ```bash
   php artisan migrate --force
   php artisan db:seed --class=ProductionSeeder
   ```

3. **Security checklist**
   - Set `APP_DEBUG=false`
   - Configure proper `APP_URL`
   - Set secure database credentials
   - Enable HTTPS


**Thank you for reviewing my submission. I look forward to discussing this implementation and my approach to backend development.**
