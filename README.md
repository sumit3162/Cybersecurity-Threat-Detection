# Cybersecurity Threat Detection Dashboard


## Overview

This dashboard provides real-time monitoring and analysis of cybersecurity threats detected in network traffic. It visualizes the data processed by the machine learning models (Random Forest and CNN) from the Jupyter notebook, offering insights into attack patterns, sources, and characteristics.

## Features

- **Interactive Visualizations**: Network graphs, time series charts, and geographic threat distribution
- **Real-time Monitoring**: WebSocket connection for live threat data updates
- **Threat Analysis**: Detailed examination of attack patterns and sources
- **Model Performance**: Tracking of machine learning model accuracy and metrics
- **Alert System**: Notifications for new threat detections

## Data Sources

The dashboard processes data from:
- AWS VPC Flow logs
- Web Application Firewall (WAF) logs
- Network traffic captures
- Machine learning model outputs

## Installation

### Prerequisites

- Python 3.8+
- Node.js 14+ (for frontend development)
- PostgreSQL or MongoDB
- Redis (for real-time features)

### Backend Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/cybersecurity-dashboard.git
   cd cybersecurity-dashboard/backend
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure environment variables:
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

5. Run database migrations:
   ```bash
   python manage.py migrate
   ```

6. Start the development server:
   ```bash
   python manage.py runserver
   ```

### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd ../frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```

## Usage

1. Access the dashboard at `http://localhost:3000`
2. Login with your credentials (default admin credentials in setup docs)
3. Explore the different dashboard sections:
   - Overview metrics
   - Network traffic visualization
   - Threat time series analysis
   - Geographic threat distribution
   - Machine learning model performance


## Data Model

![Data Model Diagram](data-model.png)

The system processes network traffic data with the following key fields:

- `bytes_in`, `bytes_out`: Traffic volume
- `src_ip`, `dst_ip`: Connection endpoints  
- `src_ip_country_code`: Geographic origin
- `protocol`: Network protocol
- `response.code`: HTTP response codes
- `rule_names`: Detection rules triggered
- `detection_types`: Classification of threats
- `duration_seconds`: Connection duration

## Machine Learning Integration

The dashboard integrates with two trained models:

1. **Random Forest Classifier**
   - Features: Network traffic metrics
   - Accuracy: ~95%
   
2. **CNN Model**  
   - Features: Sequential traffic patterns
   - Accuracy: ~97%

Models are retrained weekly with new data.

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/threats` | GET | List all threat detections |
| `/api/threats/<id>` | GET | Get specific threat details |
| `/api/metrics` | GET | Get dashboard metrics |
| `/api/models` | GET | Get model performance data |
| `/ws/updates` | WS | WebSocket for real-time updates |

## Troubleshooting

**Issue**: Dashboard not updating  
**Solution**: Check WebSocket connection and Redis service

**Issue**: Missing data in visualizations  
**Solution**: Verify database connection and data processing service

**Issue**: Slow performance  
**Solution**: Check database indexes and optimize queries

## License

MIT License. See `LICENSE` for details.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

For additional documentation, see the [docs folder](docs/) in the repository.
