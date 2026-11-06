# London Borough of Waltham Forest: Public Asset Management & Accessibility Analysis

An end-to-end local authority GIS project evaluating public asset distribution, walkability catchments, and service coverage gaps across the London Borough of Waltham Forest using QGIS LTR and British National Grid standards.

---

## Project Overview

Local authorities require data-driven evidence to optimize capital expenditure (CapEx) for municipal infrastructure. This project models pedestrian catchment zones for public transport (bus stops) and public health/waste infrastructure (litter bins) to identify underserved residential areas.

### Key Objectives
* **CRS Standardisation**: Process all spatial data natively in **EPSG:27700 (OSGB36 / British National Grid)**.
* **Catchment Modelling**: Generate 400m (5-minute walk) bus stop buffers and 250m litter bin accessibility zones.
* **Service Gap Analysis**: Isolate residential infrastructure deficit zones using spatial difference overlays.
* **Data Quality Control**: Enforce topological consistency (`must not overlap`) and geometry checks.
* **Deliverables**: Multi-layer GeoPackage database, CSV gap registers, and a 4-page publication-ready map portfolio.

---

## Spatial Analysis Methodology

1. **Data Ingestion & Preparation**: Sourced vector features from OpenStreetMap (Geofabrik), Ordnance Survey OpenData, and ONS Geography. Clipped features to the Waltham Forest administrative boundary.
2. **Buffer Catchments**:
   * **Bus Stops**: 400m dissolved buffer (pedestrian transit catchment).
   * **Litter Bins**: 250m dissolved buffer (municipal waste catchment).
3. **Difference Overlay**: Extracted unserviced residential land use polygons by subtracting catchment buffers from residential zones.
4. **Quality Assurance**:
   * Executed QGIS **Geometry Checker** to fix duplicate nodes and self-intersections.
   * Applied QGIS **Topology Checker** (`must not overlap` across service gap layers).

---

## Project Structure & Deliverables

```text
waltham-forest-gis-analysis/
├── README.md                                         # Project summary & technical documentation
├── 01_GIS_Database/
│   └── WF_GIS_Database.gpkg                          # GeoPackage database (EPSG:27700)
├── 02_Map_Outputs/
│   └── Waltham_Forest_Asset_Accessibility_Portfolio.pdf  # 4-Page Cartographic PDF Portfolio
├── 03_Data_Register_Exports/
│   ├── WF_Bus_Stop_Service_Gaps.csv                  # Bus stop deficit attribute table
│   └── WF_Litter_Bin_Service_Gaps.csv                # Litter bin deficit attribute table
└── 04_Documentation/
    └── QA_Report.md                                   # Geometry & topology validation log
