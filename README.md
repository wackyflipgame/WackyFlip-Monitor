# WackyFlip-Monitor

Monitoring & Diagnostics Tools
Logging pipelines, health checks, performance metrics, and error reporting services to keep Wacky Flip running smoothly in production.

---

## 🎯 Overview

`WackyFlip-Monitor` is the **observability backbone** for all [Wacky Flip](https://wackyflip.com) services and games. It provides real-time visibility into system health, user activity, error trends, and performance bottlenecks. This ensures that every flip, jump, and high score happens reliably—24/7.

Use this repository to set up monitoring dashboards, collect logs, and configure alerts for any issues affecting Wacky Flip’s live environments.

---

## 📈 Features

* 📊 **Metrics Collection**
  Track CPU, memory, response times, and custom game performance stats.
* 🪵 **Centralized Logging**
  Aggregate logs from all services (API, Web, Mobile) in a searchable index.
* ❤️ **Health Checks**
  Periodically probe APIs, databases, and CDN endpoints to confirm uptime.
* 🚨 **Error Reporting**
  Capture, categorize, and notify teams of exceptions and crashes.
* 🛡️ **Alerting & Notifications**
  Custom thresholds and Slack/Email notifications for critical events.
* 🧭 **Tracing & Diagnostics**
  Distributed tracing to understand request flow across microservices.

---

## 🗂️ Directory Structure

```
WackyFlip-Monitor/
├── collectors/
│   ├── metrics-collector.js     # Exposes Prometheus-compatible metrics
│   └── log-forwarder.js         # Ships logs to Elasticsearch or Loki
├── probes/
│   ├── api-health-check.js      # Checks API availability
│   └── cdn-check.js             # Verifies asset CDN status
├── dashboards/
│   ├── grafana/                 # Example Grafana dashboards JSON
│   └── kibana/                  # Saved searches and visualizations
├── alerting/
│   └── alert-rules.yaml         # Threshold-based alerts
├── examples/
│   └── docker-compose.yml       # Local monitoring stack example
├── README.md
└── LICENSE
```

---

## ⚙️ Tech Stack

* **Prometheus** – Metrics scraping and storage
* **Grafana** – Visualization dashboards
* **ElasticSearch** – Log indexing
* **Filebeat / Loki** – Log shipping
* **Sentry** – Error tracking
* **Node.js** – Health probes and collectors
* **Docker** – Local testing and setup

---

## 💻 Example Usage

### Run a Health Check Probe

```bash
node probes/api-health-check.js
```

Outputs:

```
✅ API is healthy (response time: 105ms)
```

---

### Expose Metrics Endpoint

```bash
node collectors/metrics-collector.js
```

Accessible at:

```
http://localhost:9100/metrics
```

---

## 📊 Dashboards

This repo includes:

* 📈 Grafana JSON dashboards for:

  * Request throughput
  * Error rates
  * Response latency
  * Active users
* 🔍 Kibana searches for:

  * API errors
  * Authentication failures
  * CDN cache misses

---

## 🛡️ Alerting

Example `alert-rules.yaml`:

```yaml
groups:
  - name: wackyflip_alerts
    rules:
      - alert: HighErrorRate
        expr: job:request_errors:rate5m > 0.05
        for: 2m
        labels:
          severity: critical
        annotations:
          summary: "High error rate detected"
```

---

## 🧩 Integration Targets

This monitoring setup is designed to instrument:

* [`WackyFlip-API`](https://github.com/wackyflipgame/WackyFlip-API) – REST backend
* [`WackyFlip-Web`](https://github.com/wackyflipgame/WackyFlip-Web) – Frontend performance
* [`WackyFlip-Mobile`](https://github.com/wackyflipgame/WackyFlip-Mobile) – Mobile client health
* [`WackyFlip-Stats`](https://github.com/wackyflipgame/WackyFlip-Stats) – Leaderboard usage metrics

---

## 🚀 Quick Start (Local Monitoring Stack)

```bash
docker-compose -f examples/docker-compose.yml up
```

Access dashboards at:

* Grafana: `http://localhost:3000`
* Kibana: `http://localhost:5601`

Default credentials are in `.env.example`.

---

## 🤝 Contributing

We welcome improvements to probes, alert definitions, and dashboards.
Please keep contributions modular and documented.

---

## 🧾 License

MIT License © Wacky Flip Studios
