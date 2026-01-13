# 🚀 Biskaken Admin API - Deployment Guide

## Dokploy Deployment Instructions

### 1. Repository Setup
- **Repository**: `https://github.com/plunoo/bisadmin.git`
- **Domain**: `bisadmin.rpnmore.com`
- **Port**: `5000`

### 2. Environment Variables (Required)
Set these in your Dokploy application:

```env
NODE_ENV=production
PORT=5000
JWT_SECRET=your_super_secure_jwt_secret_minimum_32_characters_here
CORS_ORIGINS=https://biskakenauto.rpnmore.com,http://localhost:3000
```

### 3. Optional Database Configuration
If using PostgreSQL:

```env
DATABASE_URL=postgresql://postgres:password@postgres-host:5432/biskaken_auto
DB_HOST=postgres-host
DB_PORT=5432
DB_NAME=biskaken_auto
DB_USER=postgres
DB_PASSWORD=your_db_password
```

### 4. Test Credentials
Default login credentials:
- **Email**: `admin@biskaken.com`
- **Password**: `admin123`

### 5. Health Check Endpoints
After deployment, test these:

```bash
# Health check
curl https://bisadmin.rpnmore.com/health

# API status
curl https://bisadmin.rpnmore.com/api/status

# Test login
curl -X POST https://bisadmin.rpnmore.com/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@biskaken.com","password":"admin123"}'
```

### 6. Frontend Integration
The frontend at `biskakenauto.rpnmore.com` should automatically connect once the API is deployed.

Test admin login at: `https://biskakenauto.rpnmore.com/admin-login`

## Available Endpoints

### Authentication
- `POST /api/auth/login` - Main login
- `POST /api/auth/admin-login` - Admin login
- `POST /api/test/auth/login` - Test login

### Blog Management
- `GET /api/test/blog` - Get all blog posts
- `POST /api/test/blog` - Create new blog post
- `PUT /api/test/blog/:id` - Update blog post
- `DELETE /api/test/blog/:id` - Delete blog post

### System
- `GET /health` - Health check
- `GET /api/status` - API status

### Data Endpoints
- `GET /api/test/customers` - Get customers
- `GET /api/test/jobs` - Get jobs
- `GET /api/test/inventory` - Get inventory
- `GET /api/test/invoices` - Get invoices

All endpoints return JSON responses and support CORS for the frontend domain.

## Security Features
- JWT token-based authentication
- CORS protection
- Helmet security middleware
- Input validation
- Secure password handling (ready for bcrypt hashing)

## Next Steps
1. Deploy this repo to Dokploy
2. Set environment variables
3. Test endpoints
4. Test frontend login
5. Configure PostgreSQL database (optional)
6. Change default admin credentials