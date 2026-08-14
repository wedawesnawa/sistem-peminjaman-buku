# Library Book Borrowing System

![preview](/public/Video%20Project%2012.gif)

## About

Library Book Borrowing System is a web-based application designed to digitize and simplify the book borrowing process in an offline library.

The system provides two main roles: Admin and User. Administrators can manage books, categories, users, borrowings, and fines. Administrators can also activate new user accounts and block users who have overdue books or outstanding fines.

This system is designed to reduce manual record-keeping and help library staff manage borrowing activities in a more efficient, organized, and centralized manner.

---

## Roles

### Admin

Administrators can:

* Manage books
* Manage book categories
* Manage users
* Manage book borrowings
* Manage fines
* Activate new user accounts
* Block users with overdue books or outstanding fines
* Monitor borrowing activities

### User

Users can:

* Register an account
* Log in to the system
* View available books
* Borrow books
* View borrowing history
* Check borrowing status
* View fine information

---

## Features

* [x] Authentication (Login & Register)
* [x] Role-based access control
* [x] Book management
* [x] Book category management
* [x] Borrowing management
* [x] User management
* [x] Fine management
* [x] User account activation
* [x] User blocking
* [x] Borrowing status management
* [x] Digitalized library management

---

## Tech Stack

| Technology     | Description                   |
| -------------- | ----------------------------- |
| **Laravel**    | Backend framework             |
| **PHP**        | Main programming language     |
| **MySQL**      | Database management system    |
| **Docker**     | Containerization              |
| **Nginx**      | Web server                    |
| **Vite**       | Frontend asset bundler        |
| **JavaScript** | Frontend scripting            |
| **Bootstrap**  | UI framework                  |
| **AdminLTE**   | Admin dashboard template      |
| **phpMyAdmin** | Database management interface |

---

## Project Structure

```text
Sistem-Peminjaman-Buku/
├── app/
├── bootstrap/
├── config/
├── database/
├── public/
├── resources/
├── routes/
├── storage/
├── docker/
├── .env
├── docker-compose.yml
├── package.json
├── composer.json
└── README.md
```

---

# Installation

## 1. Prerequisites

Make sure the following software is installed:

* [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* Git
* Node.js
* npm

> Composer does not need to be installed separately because Composer is available inside the Laravel Docker container.

Make sure **Docker Desktop is running** before continuing.

---

## 2. Clone Repository

Clone this repository:

```bash
git clone https://github.com/wedawesnawa/sistem-peminjaman-buku.git
```

Navigate to the project directory:

```bash
cd Sistem-Peminjaman-Buku
```

---

## 3. Configure Environment

If the repository provides an `.env.example` file, create the `.env` file:

### PowerShell

```powershell
Copy-Item .env.example .env
```

Configure the database connection in `.env`:

```env
APP_NAME="Sistem Peminjaman Buku"
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost:7000

LOG_CHANNEL=stack
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=docker_laravel
DB_USERNAME=root
DB_PASSWORD=password
```

> **Important:** `DB_HOST` must be set to `db` because MySQL is running inside a Docker service named `db`.

---

## 4. Start Docker Containers

Build the Docker image:

```bash
docker compose build
```

Start all containers:

```bash
docker compose up -d
```

Check the container status:

```bash
docker compose ps
```

The following services should be running:

```text
app
db
phpmyadmin
nginx
```

---

## 5. Install Laravel Dependencies

Install Composer dependencies inside the Laravel container:

```bash
docker compose exec app composer install
```

This will generate the `vendor/` directory and Laravel's autoload files.

---

## 6. Generate Application Key

Generate the Laravel application key:

```bash
docker compose exec app php artisan key:generate
```

Clear the configuration cache:

```bash
docker compose exec app php artisan config:clear
```

---

## 7. Setup Database

Run the database migration:

```bash
docker compose exec app php artisan migrate
```

If the project provides seed data, run:

```bash
docker compose exec app php artisan db:seed
```

Alternatively, run migration and seeder together:

```bash
docker compose exec app php artisan migrate --seed
```

### Reset Database

For development purposes, if you need to reset the database completely:

```bash
docker compose exec app php artisan migrate:fresh --seed
```

> **Warning:** This command will delete all existing database tables and data before recreating them.

---

## 8. Install Frontend Dependencies

Install Node.js dependencies:

```bash
npm install
```

Build the frontend assets:

```bash
npm run build
```

This will generate the Vite build files inside:

```text
public/build/
```

including:

```text
public/build/manifest.json
```

---

# Access the Application

After all Docker containers are running, access the application through:

```text
http://localhost:7000
```

## phpMyAdmin

The database can be managed through phpMyAdmin:

```text
http://localhost:8001
```

Use the following credentials:

| Configuration | Value            |
| ------------- | ---------------- |
| Server        | `db`             |
| Username      | `root`           |
| Password      | `password`       |
| Database      | `docker_laravel` |

---

# Docker Commands

### Start Containers

```bash
docker compose up -d
```

### Stop Containers

```bash
docker compose down
```

### Check Container Status

```bash
docker compose ps
```

### View Application Logs

```bash
docker compose logs app
```

### Access Laravel Container

```bash
docker compose exec app bash
```

### Run Artisan Command

```bash
docker compose exec app php artisan <command>
```

Example:

```bash
docker compose exec app php artisan migrate
```

---

# Screenshot
| Image 1                                                                                    |   Image 2                                                                                        |                             
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | 
| ![Image 1](https://drive.google.com/uc?id=1choq2wc-MOJSugKtrLyzLQs8E1CbkQCg)                  | ![Image 2](https://drive.google.com/uc?id=1Q8dU8v4jRwdyIo3Yb2oOt2ra-itkFKKU)                  | 
| ![Image 3](https://drive.google.com/uc?id=1fW_-VGsP9JL-aFCPwzBuf1vPuGydj4LB)                  | ![Image 4](https://drive.google.com/uc?id=1afcpMCljT5KNHb-XNlYJDc9iF9u-w0wS)                  |
| ![Image 5](https://drive.google.com/uc?id=16xdjWH4bDTH-Xns6_2z00cF-RFPPMZa6)                  | ![Image 6](https://drive.google.com/uc?id=1ywOLAx9VaCg-0C97ZN41GeMNXcViKFXT)                 | 
| ![Image 5](https://drive.google.com/uc?id=1gBk7czLrvdzVA-EY90QkSuFz0dHEahQi)                  | ![Image 6](https://drive.google.com/uc?id=1nCgAkfeulyurRhIgjPPZt5gzfeHdEkYK)                 | 
| ![Image 5](https://drive.google.com/uc?id=1lxX36e_RP___ZrLo5HLfaV3H0q0eahxX)                  | ![Image 5](https://drive.google.com/uc?id=1RzrEtvT51euWpMeBxZhS-8c0iFL8GFN1)                | 
| ![Image 5](https://drive.google.com/uc?id=1RzrEtvT51euWpMeBxZhS-8c0iFL8GFN1)                  | ![Image 5](https://drive.google.com/uc?id=1sbpm79O52YJI3IQcHSs_uyG6jvSFfQjq)                |
| ![Image 5](https://drive.google.com/uc?id=1XSPiYluNZ46NsJwvcuPyBSni23F-8YcY)                  | ![Image 5](https://drive.google.com/uc?id=1b27RM07rcozCb09VSzCqdKAygCSZoFoj)                |
| ![Image 5](https://drive.google.com/uc?id=1AJqhqYEQ8aKznVr2Zx920Bj3UzwdR88F)                  | ![Image 5](https://drive.google.com/uc?id=1EMK2YUyRVcaVOXDBH-ziJNBg2lM5nFWk)                |
| ![Image 5](https://drive.google.com/uc?id=1SmBy_GVtqT3wEbmuaaBNSl9H0FwfgpjN)                  | ![Image 5](https://drive.google.com/uc?id=12XVqop_qgF59k-k9m4doYdCAjVcHoslV)                |

---

# Contributors

Contributions are welcome. If you would like to improve this project, you can:

1. Fork this repository.
2. Create a new branch:

```bash
git checkout -b feature/improvement
```

3. Make your changes.
4. Commit your changes:

```bash
git add .
git commit -m "Add improvement"
```

5. Push the branch:

```bash
git push origin feature/improvement
```

6. Create a Pull Request.

### Contributors
* [@bgsptr](https://github.com/bgsptr)
* [@wedawesnawa](https://github.com/wedawesnawa)


---

# License

This project is developed for educational and development purposes.
