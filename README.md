# Sree Vasa Printech — Pro-Flow System

A high-efficiency production tracking and workflow system designed for industrial printing operations. Built for shop floors, this application bridges operators and supervisors through real-time job tracking, machine-level work order routing, and barcode/QR scanner integration.

---

## ⚡ Highlights

- **Hands-Free Scanner Automation**: Global keystroke detection automatically parses incoming barcodes and routes immediately to the appropriate view (Employee Badges vs. Job Cards).
- **Sticky Focus Guarantee**: Pins active cursor focus directly to input fields, preventing dropped keystrokes during rapid shop-floor scanning.
- **Dual Authentication & Input**: Supports fast hardware laser scanners, external scanner input boxes, and device camera QR scanning.
- **Guided 5-Step Operator Flow**: Intuitive workflow for line operators (Auth → Job Selection → Machine Selection → Status Update → Confirmation).
- **Live Production Database Sync**: Directly interfaces with the live backend for real-time status updates and machine work orders.
- **Offline Resilience & Dev Safety**: Built-in mock fallback if the backend is unreachable, plus a `PRINTECH_DEV_MODE` toggle to prevent accidental database writes during training.

---

## 🏗️ Architecture & Tech Stack

| Layer | Technology |
|---|---|
| **Frontend Framework** | React 19 (Vite 6) |
| **Scanner Engine** | `@yudiel/react-qr-scanner` + Hardware Keyboard Wedge |
| **Typography** | Lora (Editorial), DM Sans (UI), DM Mono (Technical Data) |
| **Styling** | Dynamic Inline Styles & Responsive CSS |
| **Backend Integration** | REST API (FastAPI / PostgreSQL) |

---

## 📋 Core Workflows

### 1. Operator Entry (5-Step Progression)
1. **EMP**: Authenticate via employee badge (ID or QR scan, e.g. `EMP0033`). Persists session across scans.
2. **JOB**: Scan or enter 6-digit Job Card number (e.g. `260099`). Automatically queries assigned machines and processes.
3. **MACHINE**: Select designated workstation/machine from the job's work order list.
4. **STATUS**: Set current progress state (`Pending`, `Ongoing`, `Completed`).
5. **DONE**: Immediate confirmation and telemetry log synced back to the server.

### 2. Job Lookup & Timeline
- Search any Job Card number to view current progress percentage, machine assignments, paper/print specifications, and full milestone timeline.

---

## 🚀 Quick Start

### Prerequisites
- [Node.js](https://nodejs.org/) (v18 or higher recommended)
- [Git](https://git-scm.com/)

### 1. Clone & Navigate
```bash
git clone https://github.com/sreevasaa-project/python-backend.git
cd python-backend/printech-app
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Run Development Server
```bash
npm run dev
```
Open **`http://localhost:5173`** in your browser.

### 4. Build for Production
```bash
npm run build
```
Generates an optimized, production-ready build in `printech-app/dist/`.

---

## 🛡️ Development & Safety Mode

To test UI workflows and simulate scans without writing changes to the live production database:

```javascript
// In browser console:
window.PRINTECH_DEV_MODE = true;  // Simulates successful writes
window.PRINTECH_DEV_MODE = false; // Live production writes (Default)
```

---

## 📁 Project Structure

```
printech-app/
├── public/
│   └── vassa-logo.png         # Company branding asset
├── src/
│   ├── main.jsx               # React DOM entry point
│   └── PrintechPro.jsx        # Unified application engine & UI components
├── index.html                 # HTML shell and Google Fonts imports
├── package.json               # Dependencies and build scripts
└── vite.config.js             # Vite configuration
```

---

## 📄 License
Internal proprietary software for **Sree Vasaa Printech**. All rights reserved.
