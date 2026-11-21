# HABITAT IQ
> **"See the threat. Predict the risk. Protect the habitat. Stay connected."**  
> *Forest Intelligence, Wildlife Protection & Space-Service Resilience*

A mission-grade, AI-powered forest intelligence and operational planning platform built for **ASTRA 2026**, hosted by **ANTERiX Club at VIT Bhopal**.

HABITAT IQ fuses multi-spectral orbital Earth observation data from Indian Space Research Organisation (ISRO) satellites with the ground operational reality of forest officers, wildlife biologists, and disaster response teams. It features a full-spectrum **Live Satellite Map** as its centerpiece, linked directly to an 11-module command deck and an AI field assistant.

---

## 🛰️ ISRO Data Foundations

In compliance with project requirements, all telemetry streams and environmental data are attributed strictly to authoritative ISRO portals:

1. **Bhuvan** (`NRSC · ISRO`) — High-resolution Indian Earth Observation imagery, cadastral forest layers, and active forest fire alerts from Forest Survey of India (FSI) feeds.
2. **MOSDAC** (`SAC · ISRO`) — Meteorological & Oceanographic Satellite Data Archival Centre providing INSAT-3D/3DR thermal infrared anomalies, atmospheric moisture, rainfall estimates, and cyclone surge tracking.
3. **VEDAS** (`SAC · ISRO`) — Visualisation of Earth observation Data and Archival System specialized in vegetation index (NDVI/EVI) time series, forest canopy density, and terrain slope stability modeling.
4. **Bhoonidhi** (`NRSC · ISRO`) — National Remote Sensing Centre open data gateway delivering calibrated synthetic aperture radar (SAR) backscatter from EOS-04 (RISAT-1A) and digital elevation models (DEM).

*Note: Where live programmatic API access requires closed government intranet credentials, HABITAT IQ runs on high-fidelity synthetic telemetry modeled precisely on ISRO orbital parameters, sensor resolutions, and RFC 5050 DTN protocols.*

---

## 🗺️ Live Satellite Map (The Centerpiece)

The centerpiece of HABITAT IQ is a full-width interactive map powered by Leaflet, configured for ISRO Bhuvan imagery:

### 1. Default Satellite Mode & Graceful Fallback
- **Satellite Mode by Default**: Opens in high-resolution satellite imagery.
- **Bhuvan WMS Configuration**: Tile URL and API token are isolated in [`map-config.js`](map-config.js).
- **Graceful Fallback**: If no Bhuvan API token is set or if Bhuvan endpoints are behind intranet firewalls, the map automatically displays a gentle notification banner (`"Using fallback basemap (not ISRO)"`) and switches to an open satellite basemap so the page **never looks broken or blank**.

### 2. Basemap Switcher
- **Satellite** *(Default)*: High-resolution Earth observation surface imagery.
- **Terrain**: Topographic contours and digital elevation models.
- **Plain**: Clean, high-contrast cartography for field planning.

### 3. Environmental Layer Overlays (With ISRO Badges & Legends)
- 🌲 **Forest Cover Density**: Multi-tier canopy boundary polygons (*Source: VEDAS*).
- 🔥 **Active Fire Hotspots**: Real-time thermal anomaly pulses with Fire Radiative Power (*Source: MOSDAC*).
- ⚠️ **Threat Alerts & Clearings**: Encroachment, timber theft, and embankment breach markers (*Source: Bhuvan*).
- 🦌 **Wildlife Corridors & Choke Points**: Active animal migration pathways with monitored pinch points (*Source: Bhuvan / VEDAS*).
- 🌊 **Flood / Landslide Hazard Zones**: Low-lying waterlogged floodplains and steep slope saturation zones (*Source: MOSDAC / Bhoonidhi*).
- 🛰️ **Upcoming Pass Footprint**: Real-time Low-Earth Orbit ground track and sensor swath cone (*Source: Bhoonidhi*).

### 4. Interactive Map Tools
- **Ground Telemetry Inspector**: Clicking any point on the map opens an earthy popup displaying coordinates, eco-zone classification, localized risk score (0–100), nearest threat distance, and next satellite pass window. Includes a one-click button to populate the Field Report form at those coordinates.
- **Measure Tool**: Click two or more waypoints on the map to calculate linear distance in kilometers and nautical miles.
- **Draw AOI (Area of Interest) Risk Calculator**: Draw a bounding box anywhere on the map to compute estimated surface area, mean NDVI, localized threat count, and composite vulnerability index.
- **Time Slider ("Before / Now")**: Compare historical 2024 baseline conditions against 2026 telemetry.
- **Auto-Refresh Simulation**: Simulates a live telemetry ping every 5 minutes with a pulsating green status dot.
- **Collapsible Intel Side Panel**: Sits alongside the map showing active region summaries, threat quick-jump buttons (clicking any alert immediately flies the map to that spot), and pass countdowns.

---

## 🌿 11 Integrated Interactive Modules

1. **Forest Health Monitor**: 12-month NDVI vegetation index time-series line chart (Chart.js) with 5-year baseline comparison, canopy cover percentage, 12-month delta, and plain-language ecological health diagnosis.
2. **Threat Detection**: Active alerts for thermal fire hotspots, flood inundation, illegal encroachment, and canopy dieback with severity (Low / Medium / High), date, GPS coordinates, and SOP directives. Clicking an alert flies the map directly to it.
3. **Wildlife Habitat Analysis**: Ecological corridor connectivity indices, fragmentation diagnostics, and focal species status profiles (Bengal Tiger, Indian One-Horned Rhino, Asian Elephant, Lion-Tailed Macaque, Nilgiri Tahr).
4. **Disaster Risk Assessment**: Multi-hazard 0–100 vulnerability score dials for Forest Fire, Flood, Drought, and Landslide, accompanied by an explicit, transparent *"Why This Score?"* explanation citing satellite sensor telemetry.
5. **7-Day Risk Forecast**: Predictive trend projection plotting rising or falling vulnerability over the next 7 days, complete with radar confidence ratings and operational weather warnings.
6. **Satellite Contact Planner**: Dynamic timeline of upcoming ISRO Low-Earth Orbit (LEO) satellite passes (EOS-04 / RISAT-1A SAR, Resourcesat-2A, Cartosat-3, Oceansat-3, INSAT-3DR) displaying start times, pass durations, maximum elevation angles, signal quality, and bandwidth capacities.
7. **Field Report Scheduler & Transmitter**: Digital dispatch terminal where rangers author incident reports with GPS locks and data payloads, automatically synchronizing dispatch with optimal upcoming satellite contact windows, with a live `Transmit Now` simulation.
8. **Space-Service Resilience & Disruption Simulator**: Interactive toggle simulating severe space weather or atmospheric storm fade. Automatically shifts the transmission queue to Delay-Tolerant Networking (RFC 5050 Bundle Protocol) via secondary narrowband S-band store-and-forward relays, visualizing an atmospheric storm cloud directly on the map.
9. **Alerts Centre**: Searchable, filterable real-time incident queue with one-click guard dispatch acknowledgment.
10. **Report Export (Field Operational Briefing)**: One-click export modal that generates an authentic, print-optimized operational briefing sheet suitable for printing or saving as a PDF (`window.print()`).
11. **Multi-Reserve Region Selector**: Reactive dropdown switching between 5 distinct Indian ecological regions:
    - **Sundarbans Biosphere Reserve** (West Bengal — Mangrove Delta & Tidal Surges)
    - **Kaziranga National Park** (Assam — Alluvial Floodplains & Rhino Migration)
    - **Western Ghats: Wayanad / Nilgiris** (Kerala/TN — Shola Montane & Landslide Hazards)
    - **Jim Corbett National Park** (Uttarakhand — Sal Deciduous & Thermal Fire Anomaly)
    - **Bandhavgarh National Park** (Madhya Pradesh — Dry Bamboo & Drought Stress)

---

## 🤖 Context-Aware AI Chatbox ("Ask HABITAT IQ")

Accessible via the floating beacon at bottom-right across the application:
- **Grounded Intelligence**: Analyzes live telemetry from the active region, active risk scores, threats, and satellite pass timetables.
- **Controls the Map Directly**: Ask it to *"Fly to Kaziranga"*, *"Show me fire hotspots in Corbett"*, or *"Switch to satellite view"*, and it commands the map in real time!
- **Action Triggers**: Can switch regions directly, toggle space-service disruption simulation, and explain vulnerability metrics from natural language prompts.
- **Suggested Question Chips**:
  - *"Which region has the highest fire risk today?"*
  - *"When is the next satellite pass for Kaziranga?"*
  - *"Reschedule my report because of an outage"*
  - *"Explain this risk score"*
- **Honest Fallback**: Refuses hallucinations and clearly states boundaries if asked questions outside geospatial forestry telemetry.


---


## 🚀 How to Run Locally

Because HABITAT IQ is built with standard HTML5, CSS3, Leaflet, and modern vanilla JavaScript, there are **no build steps, node_modules, or package managers required**.

### Option A: Direct Open
Open the project directory in File Explorer:
`C:\Users\Sonu Yadav\.gemini\antigravity\scratch\habitat-iq`  
Double-click `index.html` to open it directly in Chrome, Edge, Safari, or Firefox.

### Option B: Local Web Server (Recommended)
From your terminal in this directory:
```bash
# Using Python 3
python -m http.server 8000
```
Open `http://localhost:8000` in your browser.



## 🏆 Hackathon Credits
- **Event:** ASTRA 2026 Hackathon
- **Host:** ANTERiX Club, VIT Bhopal University
- **Theme:** Space Technology, Forest Intelligence & Disaster Resilience
- *Built overnight at ASTRA 2026.*

---

## Screenshots

![Interface](<Screenshot 2026-11-22 040109.png>)
![Map](<Screenshot 2026-11-22 040130.png>)
![Analysis](<Screenshot 2026-11-22 040140.png>)
