# PRAVAH — 3D Traffic Digital Twin & Adaptive Signal Simulator

<div align="center">

  [![3D Simulator](https://img.shields.io/badge/3D_Simulator-Live_WebGL-FF6D00?style=for-the-badge&logo=three.js&logoColor=white)](https://pravah-3d-simulator.vercel.app)
  [![TraffiSense Dashboard](https://img.shields.io/badge/Operations_Dashboard-TraffiSense-00E5FF?style=for-the-badge&logo=vercel&logoColor=black)](https://traffisense-dashboard.vercel.app)
  [![Core CV Engine](https://img.shields.io/badge/Vision_Engine-TraffiSense-blue?style=for-the-badge&logo=pytorch&logoColor=white)](https://github.com/temp-pie1207/traffic-violation-system)
  [![Demo Videos](https://img.shields.io/badge/Demo_Videos-Play_%26_Download-E11D48?style=for-the-badge&logo=youtube&logoColor=white)](https://github.com/temp-pie1207/traffic-violation-system#--demo-videos--benchmark-clips)
  [![Three.js](https://img.shields.io/badge/Three.js-WebGL_Interactive-black?style=for-the-badge&logo=three.js&logoColor=white)](https://threejs.org/)
  [![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

  <p align="center">
    <strong>An interactive 3D WebGL Digital Twin simulating real-time traffic flow across complex Indian 4-way intersections. Evaluates the PRAVAH person-weighted adaptive signal controller against fixed-time cycles, featuring real-time violation triggers and slide-out e-challan inspection drawers.</strong>
  </p>

  <p align="center">
    <a href="https://pravah-3d-simulator.vercel.app"><strong>🚗 Launch 3D Simulation (Vercel) ↗</strong></a> •
    <a href="https://traffisense-dashboard.vercel.app">Operations Dashboard</a> •
    <a href="https://github.com/temp-pie1207/traffic-violation-system">Computer Vision Core</a> •
    <a href="https://github.com/temp-pie1207/traffic-violation-system/tree/main/videos_final"><strong>🎬 Demo Videos & Footage ↗</strong></a>
  </p>

</div>

---

## ✦ System Overview & PRAVAH Algorithm

Traditional traffic signals operate on fixed-time cycles (or Webster formula estimates) that ignore the disproportionate density of mixed traffic in Indian urban corridors.

**PRAVAH (Person-Weighted Adaptive Signal Controller)** dynamically calculates green phase durations based on real-time vehicle passenger weighting:

$$\text{Phase Weight} = \sum_{v \in \text{Approach}} w_v \cdot N_v$$

- **Buses**: $w = 35.0$
- **Auto-rickshaws**: $w = 3.0$
- **Passenger Cars**: $w = 1.5$
- **Two-Wheelers / Bikes**: $w = 1.2$
- **Emergency Ambulances**: Immediate preemptive green-wave corridor override.

In benchmark simulations across 6 scenarios $\times$ 3 random seeds, **PRAVAH achieved 52% lower average vehicle wait time** compared to fixed-time signals, and **37% lower wait time** compared to Webster cycles.

---

## ✦ Interactive 3D Simulator Controls

<div align="center">

| Action | Control | Description |
|:---|:---|:---|
| **Rotate Camera** | `Left Click + Drag` | 360° orbit rotation around the junction center |
| **Pan Scene** | `Right Click + Drag` | Translate viewport across North, South, East, West approaches |
| **Zoom View** | `Mouse Wheel` | Smooth zoom from high-altitude aerial view to bumper-level inspection |
| **Select Vehicle** | `Left Click on Vehicle` | Displays vehicle telemetry: speed, lane, registration plate & infraction status |
| **Inspect E-Challan** | `Click Violation Banner` | Opens glassmorphic evidentiary slip with fine, timestamp, and legal section |
| **Switch Scenarios** | `HUD Scenario Dropdown` | Toggle Red Light Breach, Helmet Violation, Triple Riding, or Ambulance Run |

</div>

---

## ✦ HUD Telemetry Cards

The simulation features real-time glassmorphism HUD overlays:

1. **Top Header**: Real-time simulation clock, junction designation, and active controller mode.
2. **Signal Status Card**: North-South vs. East-West signal lamps with remaining phase countdown timers.
3. **Traffic Overview**: Live fleet census tracking individual cars, auto-rickshaws, bikes, buses, and emergency vehicles.
4. **Active Violation Banner**: Real-time alerts when a vehicle crosses the virtual stop line on red or violates safety norms.
5. **Interactive Vehicle Dossier**: Displays license plate (e.g. `MH 46 AX 4296`), velocity in km/h, lane assignment, and compliance state.
6. **Evidentiary Challan Drawer**: Official e-challan slip rendered with Motor Vehicles Act sections, penalty amount, and high-contrast digital watermark.

---

## ✦ Real-World Benchmark Videos & Test Clips

The companion Computer Vision pipeline repository hosts **8 curated real-world traffic video clips** (1080p / 480p) featuring red-light runners, helmet violations, and CCTV triple-riding footage that drive this simulator's AI telemetry:

<div align="center">
  <table>
    <tr>
      <td align="center"><b>Red Light Detection</b></td>
      <td align="center"><b>CCTV Triple-Riding</b></td>
      <td align="center"><b>Signal State Tracking</b></td>
    </tr>
    <tr>
      <td><img src="https://raw.githubusercontent.com/temp-pie1207/traffic-violation-system/main/videos_final/preview_redlight.gif" width="260" alt="Red Light Jumping"/></td>
      <td><img src="https://raw.githubusercontent.com/temp-pie1207/traffic-violation-system/main/videos_final/preview_triple_riding.gif" width="260" alt="Triple Riding CCTV"/></td>
      <td><img src="https://raw.githubusercontent.com/temp-pie1207/traffic-violation-system/main/videos_final/preview_ai_detection.gif" width="260" alt="AI Signal Detection"/></td>
    </tr>
  </table>

  <p align="center">
    <a href="https://github.com/temp-pie1207/traffic-violation-system/tree/main/videos_final"><strong>📁 Browse, Stream & Download All 8 Demo Video Clips on GitHub ↗</strong></a>
  </p>
</div>

---

## ✦ Architecture & File Structure

```
pravah-3d-simulator/
├── index.html                   # Monolithic 3D WebGL simulator layout & HUD
├── vercel.json                  # Edge static hosting configuration
├── static/
│   ├── js/
│   │   ├── three.min.js         # Three.js 3D rendering engine
│   │   └── OrbitControls.js     # Smooth orbital camera interaction controller
│   └── css/                     # Simulation themes & glassmorphic styling
└── README.md                    # Project documentation
```

---

## ✦ Getting Started Locally

### Prerequisites
- Any modern web browser supporting WebGL (Chrome, Firefox, Safari, Edge)
- Python 3.x (for simple HTTP serving)

### Run Locally

```bash
# 1. Clone repository
git clone https://github.com/temp-pie1207/pravah-3d-simulator.git
cd pravah-3d-simulator

# 2. Launch HTTP server
python3 -m http.server 8080
```

Open **`http://localhost:8080`** to experience the 3D simulation.

---

## ✦ Production Deployment

This project is deployed on **Vercel**:

```bash
npx --yes vercel --prod --yes
```

- **Live URL**: [https://pravah-3d-simulator.vercel.app](https://pravah-3d-simulator.vercel.app)

---

## ✦ Authors & Attribution

- **PRAVAH Algorithm & Research**: Sachin Nair & research team
- **3D WebGL Simulation & Cloud Deployment**: [Naman Kashyap](https://github.com/temp-pie1207)
  - Portfolio: [naman-portfolio-theta.vercel.app](https://naman-portfolio-theta.vercel.app)
  - LeetCode: [Naman_1207](https://leetcode.com/u/Naman_1207/)
  - Email: [namankashyap484@gmail.com](mailto:namankashyap484@gmail.com)

---

## ✦ License

This project is licensed under the [MIT License](LICENSE).
