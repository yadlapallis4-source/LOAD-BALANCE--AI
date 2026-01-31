# Center-of-Gravity–Aware Load Planning System

A full-stack web application that provides AI-assisted logistics solutions for optimal cargo placement using physics principles (center of mass and torque) to improve safety and efficiency.

## 🚀 Features

- **Physics-Based Optimization**: Calculate center of gravity and stability scores
- **AI-Powered Placement**: Automated cargo placement algorithm
- **Real-Time Analysis**: Instant safety warnings and risk assessment
- **Visual Dashboard**: Intuitive interface for managing vehicles, cargo, and load plans
- **Multi-User Support**: Role-based access control (Admin/Operator)
- **Comprehensive Reporting**: Detailed load plans with stability metrics

## 🏗️ Tech Stack

### Backend
- **FastAPI**: High-performance Python web framework
- **PostgreSQL**: Reliable relational database
- **NumPy & SciPy**: Physics calculations and optimization
- **JWT**: Secure authentication

### Frontend
- **React.js**: Component-based UI framework
- **React Router**: Client-side routing
- **Recharts**: Data visualization
- **Axios**: HTTP client

### Deployment
- **Docker**: Containerized deployment
- **Docker Compose**: Multi-container orchestration

## 📋 Prerequisites

- Docker and Docker Compose (recommended)
- OR:
  - Python 3.11+
  - Node.js 18+
  - PostgreSQL 15+

## 🚀 Quick Start with Docker

### 1. Clone the repository
```bash
cd load-planning-system
```

### 2. Start the application
```bash
docker-compose up --build
```

This will start:
- PostgreSQL database on port 5432
- Backend API on http://localhost:8000
- Frontend on http://localhost:3000

### 3. Access the application
- Frontend: http://localhost:3000
- Backend API Docs: http://localhost:8000/docs

### 4. Login
Use the demo credentials:
- Email: `admin@loadplan.com`
- Password: `password123`

## 🔧 Manual Setup (Without Docker)

### Backend Setup

1. **Navigate to backend directory**
```bash
cd backend
```

2. **Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Setup database**
```bash
# Create PostgreSQL database
psql -U postgres -c "CREATE DATABASE loadplanning;"

# Run initialization script
psql -U postgres -d loadplanning -f ../database/init.sql
```

5. **Configure environment**
```bash
cp .env.example .env
# Edit .env with your database credentials
```

6. **Run backend**
```bash
uvicorn main:app --reload
```

Backend will be available at http://localhost:8000

### Frontend Setup

1. **Navigate to frontend directory**
```bash
cd frontend
```

2. **Install dependencies**
```bash
npm install
```

3. **Configure API URL**
Create `.env` file:
```
REACT_APP_API_URL=http://localhost:8000
```

4. **Run frontend**
```bash
npm start
```

Frontend will be available at http://localhost:3000

## 📊 Database Schema

### Tables
- **users**: User accounts and authentication
- **vehicles**: Vehicle specifications
- **cargo**: Cargo item details
- **load_plans**: Generated load plans with stability metrics
- **cargo_placements**: Cargo positioning within load plans

## 🔌 API Endpoints

### Authentication
- `POST /auth/login` - User login
- `POST /auth/register` - User registration
- `GET /auth/me` - Get current user

### Vehicles
- `GET /vehicles` - List all vehicles
- `GET /vehicles/{id}` - Get vehicle details
- `POST /vehicles` - Create new vehicle
- `DELETE /vehicles/{id}` - Delete vehicle

### Cargo
- `GET /cargo` - List all cargo items
- `GET /cargo/{id}` - Get cargo details
- `POST /cargo` - Create new cargo
- `DELETE /cargo/{id}` - Delete cargo

### Load Plans
- `GET /load-plan` - List all load plans
- `GET /load-plan/{id}` - Get plan details
- `POST /load-plan/generate` - Generate optimized load plan
- `POST /load-plan/analyze` - Analyze custom load configuration
- `DELETE /load-plan/{id}` - Delete load plan

Full API documentation available at http://localhost:8000/docs

## 🎯 Usage Guide

### Creating a Load Plan

1. **Navigate to "Create Plan"**
2. **Select a Vehicle** from the dropdown
3. **Select Cargo Items** by clicking on them
4. **Click "Generate Load Plan"**
5. **Review** the generated plan with:
   - Stability score
   - Center of gravity coordinates
   - Safety warnings
   - Cargo placements

### Understanding Stability Scores

- **70-100**: Safe - Well-balanced load
- **50-69**: Warning - Suboptimal stability
- **0-49**: Critical - Dangerously unbalanced

### Managing Vehicles & Cargo

- Add vehicles with dimensions and max load capacity
- Add cargo items with weight and dimensions
- Delete unused items
- View all items in organized tables

## 🔬 Physics Engine

The system uses sophisticated physics calculations:

### Center of Gravity
```
COG = Σ(mass_i × position_i) / Σ(mass_i)
```

### Stability Score
Calculated based on deviations from ideal center position with weighted factors:
- Lateral deviation: 50% weight
- Longitudinal deviation: 30% weight
- Vertical deviation: 20% weight

### Safety Analysis
- Weight capacity validation
- Lateral balance checks
- Longitudinal balance checks
- Height-based stability assessment
- Torque analysis

## 🛡️ Security

- JWT-based authentication
- Password hashing with bcrypt
- Role-based access control
- HTTPS ready (configure in production)
- SQL injection protection via parameterized queries

## 🐛 Troubleshooting

### Database Connection Issues
```bash
# Check if PostgreSQL is running
docker-compose ps

# View database logs
docker-compose logs database
```

### Backend Issues
```bash
# View backend logs
docker-compose logs backend

# Restart backend
docker-compose restart backend
```

### Frontend Issues
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

## 📝 Environment Variables

### Backend (.env)
```
DB_HOST=localhost
DB_PORT=5432
DB_NAME=loadplanning
DB_USER=postgres
DB_PASSWORD=postgres
SECRET_KEY=your-secret-key-here
```

### Frontend (.env)
```
REACT_APP_API_URL=http://localhost:8000
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License.

## 👥 Authors

- Load Planning System Team

## 🙏 Acknowledgments

- Physics calculations based on classical mechanics principles
- UI/UX inspired by modern logistics platforms
- Built for hackathon demonstration and production readiness

## 📞 Support

For issues and questions:
- Create an issue on GitHub
- Contact: support@loadplan.com

---

**Note**: This is a demonstration system. For production use, ensure proper security hardening, database backups, and scaling configurations.
