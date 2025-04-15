# Assignment 4: Monitoring & Logging (Prometheus & Grafana)

## 🎯 Objective
Set up monitoring and logging for a sample web application using **Prometheus** and **Grafana**.

---

## ✅ Deliverables

- Steps to configure monitoring/logging tools
- Screenshots of the dashboards
- Alert setup for critical issues

---

## 🔧 Setup Instructions

### 1. Deploy a Sample Web App (Flask Example)
```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello from Flask!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

### 2. Install Prometheus on Azure VM
```bash
wget https://github.com/prometheus/prometheus/releases/download/v2.45.0/prometheus-2.45.0.linux-amd64.tar.gz
tar xvf prometheus-2.45.0.linux-amd64.tar.gz
cd prometheus-2.45.0.linux-amd64
```

Update `prometheus.yml`:
```yaml
scrape_configs:
  - job_name: 'flask-app'
    static_configs:
      - targets: ['localhost:5000']
```

### 3. Install Grafana
```bash
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
```

### 4. Connect Prometheus to Grafana
- URL: `http://localhost:9090`

### 5. Create Dashboard and Alerts
- Visualize metrics such as `http_requests_total`, `cpu_usage`, and memory
- Set alerts for CPU > 80%

---

## 📸 Screenshots
See `/screenshots/` folder for UI and alerting setup.