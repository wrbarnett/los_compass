# 🧭 LOS Compass

<img width="256" height="256" alt="Screenshot 2026-04-07 103922" src="https://github.com/user-attachments/assets/7c785ac2-c61c-43c4-9011-fe413a7fb4c3" />

<img width="256" height="256" alt="Screenshot 2026-04-07 104018" src="https://github.com/user-attachments/assets/8a40f8fd-3fc8-455a-897d-da16ea696291" />

<img width="256" height="256" alt="Screenshot 2026-04-07 104100" src="https://github.com/user-attachments/assets/be55663b-dc0f-44e0-9982-c9e1f9caa6eb" />

**Turn LOS insights into action.**

LOS Compass is a lightweight hospital operations analytics app that identifies excess length of stay (LOS), benchmarks performance, and prioritizes actionable opportunities to improve throughput and reduce readmissions.

Built using **Streamlit**, it works with simple CSV uploads—no EMR integration required.

---

## 🚀 What It Does

LOS Compass helps you answer:

- Which encounters are exceeding expected LOS?
- Which DRGs and service lines are driving delays?
- Which patients should we act on today?
- Where are readmissions occurring?

---

## 📊 Core Features

### 🔍 LOS Benchmarking
- Calculates expected LOS using DRG-based medians
- Compares observed vs. expected LOS
- Computes LOS variance and O/E index

### 📈 Operational Insights
- DRG-level performance analysis
- Service line summaries
- Total excess patient-days

### ⚡ Priority Discharge List
- Ranks encounters using:
  - LOS variance
  - Readmission status
  - ICU / ventilation flags
- Generates actionable worklists

### 🔁 Readmission Analysis
- 30-day readmission rate
- Integrated into prioritization scoring

### 📥 Exportable Outputs
- Analyzed encounter dataset
- DRG summary
- Service line summary

---

## 📁 Input Data

### Required: Encounter Dataset (`app_input_v1.csv`)

One row per hospital encounter.

#### Required Columns

| Column | Description |
|------|-------------|
| patient_id | Unique patient identifier |
| encounter_id | Unique encounter ID |
| admit_datetime | Admission timestamp |
| discharge_datetime | Discharge timestamp |
| los_days | Length of stay (days) |
| readmit_30d_flag | 30-day readmission flag |
| age | Age at admission |
| sex | Patient sex |
| admit_source | Admission source |
| discharge_disposition | Discharge location |
| drg_type | DRG type (APR / HCFA) |
| drg_code | DRG code |
| drg_desc | DRG description |
| drg_severity | DRG severity subclass |
| drg_mortality | DRG mortality subclass |
| service_line | Mapped service line |
| icu_flag | ICU exposure (0/1) |
| icu_los_days | ICU LOS |
| vent_flag | Ventilation exposure (0/1) |
| vent_days | Vent duration |
| charlson_index | Comorbidity score |

---

### Optional: Benchmark Dataset (`benchmark_v1.csv`)

If not provided, LOS Compass will automatically compute benchmarks from the uploaded data.

| Column | Description |
|------|-------------|
| drg_type | DRG type |
| drg_code | DRG code |
| drg_desc | DRG description |
| drg_severity | DRG severity |
| expected_los_days | Median LOS |

---

## 🧠 How It Works

1. Upload encounter-level data
2. Load or compute DRG-based LOS benchmarks
3. Calculate:
   - Expected LOS
   - LOS variance
   - O/E index
4. Generate:
   - Patient-level prioritization
   - DRG summaries
   - Service line insights

---

## 🏥 Use Cases

- Hospital throughput optimization
- Length of stay reduction initiatives
- Case management prioritization
- Value-based care performance
- Readmission reduction programs

---

## ⚙️ Tech Stack

- Python
- Pandas
- NumPy
- Streamlit

---

## 📌 Notes

- Designed for **CSV-based workflows** (no EMR integration required)
- Uses **MIMIC-IV-derived schema** as a proxy for real EHR data
- Benchmarking is **DRG-based**, not payer-derived GMLOS

---

## 🧭 Roadmap (Future Enhancements)

- Predictive discharge date modeling
- Readmission risk modeling (feature attribution)
- Discharge barrier classification
- Real-time EMR integration (FHIR / API)
- Role-based worklists (case manager, physician)

---

## 👤 Author

Built for hospital operations, clinical analytics, and data-driven quality improvement.

---

## 📄 Data Attribution & Use

This application uses the MIMIC-IV dataset provided by PhysioNet.

Dataset License: Use of the data is strictly governed by the PhysioNet Restricted Health Data Use Agreement 1.5.0.

No Data Distribution: In accordance with the DUA, no raw or derived MIMIC-IV data is hosted in this repository. Users must obtain their own access credentials via PhysioNet.

Johnson, A., Bulgarelli, L., Pollard, T., Gow, B., Moody, B., Horng, S., Celi, L. A., & Mark, R. (2024). MIMIC-IV (version 3.1). PhysioNet. https://doi.org/10.13026/kpb9-mt58
