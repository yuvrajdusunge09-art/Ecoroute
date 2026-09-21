# 🌿 EcoRoute AI

### AI-Powered Efficient & Low-Emission Route Optimization

> *"Don't just find the shortest route. Find the most efficient route."*

AI-powered route optimization for lower travel time, lower cost, and lower carbon emissions.

---

## 🚀 What is EcoRoute AI?

EcoRoute AI is an intelligent route optimization platform that goes beyond traditional navigation systems. While most navigation apps optimize for travel time or distance, EcoRoute AI uses **machine learning** and **multi-objective optimization** to find routes that balance:

- ⏱️ **Travel Time**
- 📏 **Distance**
- ⛽ **Fuel/Energy Consumption**
- 🌱 **CO2 Emissions**
- 🚦 **Traffic Congestion**
- 🌦️ **Weather Conditions**

## 🧠 Architecture

```
Historical/Environmental Data
        ↓
ML Prediction (XGBoost)
        ↓
Road-Segment Cost Estimation
        ↓
Multi-Objective Route Optimization
        ↓
Efficient Route Recommendation
```

The system **predicts** the cost of traveling through each road segment using trained ML models, then uses a **multi-objective cost function** to find the optimal route based on user preferences.

## 🎯 Route Objectives

| Objective | Description |
|-----------|-------------|
| **Fastest** | Minimizes travel time |
| **Shortest** | Minimizes distance |
| **Lowest Cost** | Minimizes estimated fuel/energy cost |
| **Greenest** | Minimizes estimated CO2 emissions |
| **Balanced** | Balances time + cost + emissions |
| **Smart AI** | Auto-selects based on user preferences & conditions |

## 🏗️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React, TypeScript, Tailwind CSS |
| **Map** | Leaflet + OpenStreetMap |
| **Charts** | Recharts |
| **Backend** | Python, FastAPI |
| **ML** | scikit-learn, XGBoost |
| **Database** | SQLite (prototype) |

## 📁 Project Structure

```
ecoroute-ai/
├── frontend/                    # React + TypeScript frontend
│   ├── src/
│   │   ├── components/          # UI components
│   │   │   ├── layout/          # Navbar, Footer
│   │   │   ├── hero/            # Landing hero section
│   │   │   ├── map/             # Leaflet map components
│   │   │   ├── route/           # Route planner & comparison
│   │   │   ├── analytics/       # Eco analytics dashboard
│   │   │   ├── fleet/           # Fleet optimization
│   │   │   ├── research/        # Research lab
│   │   │   ├── ai/              # AI assistant & explanations
│   │   │   ├── settings/        # Settings page
│   │   │   ├── methodology/     # Responsible AI disclosure
│   │   │   └── common/          # Shared components
│   │   ├── pages/               # Page-level components
│   │   ├── services/            # API client services
│   │   ├── hooks/               # Custom React hooks
│   │   ├── types/               # TypeScript types
│   │   ├── utils/               # Utilities & formatters
│   │   └── data/                # Demo data
│   └── package.json
├── backend/                     # Python FastAPI backend
│   ├── app/
│   │   ├── api/                 # API route handlers
│   │   ├── database/            # SQLAlchemy models & seeding
│   │   ├── ml/                  # ML training & prediction
│   │   ├── optimization/        # Multi-objective optimizer
│   │   ├── services/            # Business logic services
│   │   ├── schemas/             # Pydantic schemas
│   │   └── config.py            # Configuration
│   └── requirements.txt
├── .env.example                 # Environment variable template
└── README.md
```

## 🚀 Quick Start

### Prerequisites
- **Node.js** 18+ and npm
- **Python** 3.10+

### 1. Clone & Setup Backend

```bash
# Install Python dependencies
cd backend
pip install -r requirements.txt

# Train ML models (first time only)
python -m app.ml.train

# Start backend server
python -m app.main
```

The backend runs at `http://localhost:8000`.

### 2. Setup Frontend

```bash
# Install Node dependencies
cd frontend
npm install

# Start development server
npm run dev
```

The frontend runs at `http://localhost:5173`.

### 3. Open in Browser

Navigate to `http://localhost:5173` — the app works in **Demo Mode** without any API keys.

## 🎮 Demo Flow (3 minutes)

1. **Open** EcoRoute AI → see the hero section
2. **Navigate** to Route Planner
3. **Select**: PCCOE Main Gate → Pune Railway Station
4. **Choose**: Petrol Car, set CO2=40%, Time=30%, Cost=20%, Traffic=10%
5. **Click** "Optimize Route" → see 3-5 route alternatives on the map
6. **Compare** routes: Fastest vs Balanced vs Greenest
7. **Click** "Why This Route?" → see animated trade-off comparison
8. **Try** "What If?" → increase traffic by 30% → watch routes recalculate
9. **Switch** vehicle: Petrol → Electric → see energy/CO2 changes
10. **Explore**: Eco Analytics → City Impact → Fleet Mode

## 🔬 Key Technical Features

### Machine Learning Model
- **Algorithm**: XGBoost regressors
- **Training Data**: Synthetic dataset (~10,000 samples)
- **Features**: Hour, day, road type, length, speed, traffic, temperature, rainfall, vehicle type, congestion, slope
- **Predictions**: Travel time, fuel consumption, CO2 emissions per road segment

### Multi-Objective Optimization
```
TOTAL COST = w_time × norm_time
           + w_distance × norm_distance
           + w_energy × norm_energy
           + w_co2 × norm_co2
           + w_traffic × norm_traffic
```

### EcoRoute Score (0-100)
| Component | Weight |
|-----------|--------|
| Travel Time | 25% |
| Fuel | 25% |
| CO2 | 35% |
| Traffic | 10% |
| Distance | 5% |

### Fuel/Energy Estimation
- **Combustion**: distance × (1/efficiency) × traffic_factor × speed_factor
- **Electric**: distance × (1/efficiency) × temp_factor × speed_factor
- **CO2**: fuel × emission_factor (configurable)

## 🌐 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/locations` | List demo locations |
| POST | `/api/optimize` | Multi-objective route optimization |
| POST | `/api/routes` | Generate routes |
| POST | `/api/predict` | ML prediction for road segment |
| POST | `/api/calculate-emissions` | Emission calculation |
| POST | `/api/simulate` | City impact / What-If simulation |
| POST | `/api/fleet-optimize` | Fleet optimization |
| GET | `/api/analytics` | Analytics dashboard data |
| POST | `/api/ai-explain` | AI explanation for route selection |

## ⚠️ Demo Mode & Responsible AI

> **Important**: This is a hackathon prototype. All values are model estimates.

- ML predictions use **synthetic training data**, not real-world measurements
- Emission factors are **configurable assumptions**
- Route metrics are **simulated/model-estimated** in demo mode
- Real deployment requires **validation with actual traffic and emission data**
- Do not make unsupported claims about exact emissions savings

The application works completely in **Demo Mode** without any API keys. Real providers can be connected via environment variables.

## 🔑 Environment Variables

```bash
# Copy .env.example to .env
cp .env.example .env
```

| Variable | Description | Default |
|----------|-------------|---------|
| `DATABASE_URL` | Database connection string | `sqlite:///ecoroute.db` |
| `DEMO_MODE` | Enable demo mode | `true` |
| `MAP_API_KEY` | Map provider API key | (optional) |
| `WEATHER_API_KEY` | Weather provider API key | (optional) |
| `ROUTING_API_KEY` | Routing provider API key | (optional) |
| `AI_API_KEY` | AI/LLM provider API key | (optional) |

## 📊 Unique Technical Contribution

This project demonstrates:

```
PREDICT → OPTIMIZE → EXPLAIN → SIMULATE → MEASURE IMPACT
```

1. **PREDICT**: ML-based road-segment cost prediction (XGBoost)
2. **OPTIMIZE**: Multi-objective weighted route optimization
3. **EXPLAIN**: Transparent AI explanations with actual calculated values
4. **SIMULATE**: What-If scenarios and city-level impact modeling
5. **MEASURE**: Quantified climate impact estimation

---

**Built for hackathon demonstration** · EcoRoute AI © 2024
