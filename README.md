# 🌍 Global Living Wage Feasibility Analysis
⭐ **A Data-Driven Study on Survival Costs, Urban Hurdles, and Economic Sustainability**

---

## 📌 Project Overview
The **Global Living Wage Analysis** investigates the economic feasibility of survival across the globe. By merging the **2026 Global Living Wage Dataset** (covering **217 countries** and **188 cities**) with **World Bank GDP per capita (PPP)** data, I developed a high-precision analysis of **199 nations** with verified economic records.

The core of this project is the **Affordability Index**, which measures the cost of a living wage as a percentage of a nation's GDP per capita to determine where survival is mathematically sustainable.

## 📡 Data Sources
* **Valuing Impact** – [2026 Global Living Wage Dataset](https://valuingimpact.com/all/2026_living_wage_dataset/)
* **World Bank** – [GDP per Capita (PPP) Indicator](https://data.worldbank.org/indicator/NY.GDP.PCAP.CD)

## ❓ Key Research Questions
* **The Urban Gap:** Why is a national minimum wage often insufficient for city dwellers?
* **Family Vulnerability:** How much more do single parents struggle compared to standard households?
* **Economic Growth:** Can a country simply "grow" its way into affordability?

---

## 🧰 Tech Stack & Methodology
* **Data Processing:** <img width="48" height="48" alt="icons8-pandas-48" src="https://github.com/user-attachments/assets/a1a0555b-f15f-4c7d-b2b4-0171fa2df0c9" />
Python (Pandas) for cleaning and for all calculations.
* **Visualization:**<img width="48" height="48" alt="icons8-google-looker-48" src="https://github.com/user-attachments/assets/8da2ecbd-8f79-4ee0-9889-9eb44c06d50c" />
 Looker Studio for interactive dashboards.
* **Economic Modeling:** Created Growth Simulator using parameter-driven logic.

---

## 📊 Core Analysis & Findings

### 1. The Urban-Rural Disparity
My analysis shows that location is a primary factor in survival cost. In many regions, living costs in cities are **50% to 100% higher** than the national median.
> **Key Metric:** The highest observed Urban-Rural gap for a standard family reached **124.6%**.

### 2. The Single Parent Burden
The data reveals a critical social crisis: single-parent households face the highest financial risk.
* A single parent in an urban area requires **56% more income** to survive than a standard two-parent family.
* In high-stress **"Red Zone"** countries, a single parent needs many times the average national income just for basic needs.

### 3. The 0.4 Sustainability Benchmark
I established **0.4 (Living Wage = 40% of GDP per capita)** as the **"Sustainability Line."**
* 🟢 **Green Zone:** Living wage is economically sustainable.
* 🔴 **Red Zone:** Living wage exceeds 40% of GDP, indicating extreme economic pressure.

> **📊 Data Note:** While the initial dataset included 217 countries, this specific affordability analysis and the simulation map focus on **199 countries**. I filtered the data to include only nations with verified World Bank GDP Per capita (PPP) records to ensure the Index remains accurate.

---

## 🎮 Interactive Growth Simulator
I built a simulation map to test how national wealth affects affordability. By using a **GDP Growth Slider (0% to 100%)**, the dashboard recalculates affordability in real-time.

* **At 0% Growth:** 82 countries are affordable.
* **At 100% Growth (Doubling GDP):** 132 countries become affordable.
* **The Insight:** Even after doubling GDP, **67 countries remain in the Red Zone**, proving that growth alone cannot fix the crisis without lowering the cost of living.

### 🧠 Technical Logic (Looker Studio)
The simulator uses a custom logic gate and dynamic parameters to update the map colors in real-time. This allows the user to see the impact of economic growth without refreshing the page.

### **Step 1: The Input (Dynamic Parameter)**
I created a custom parameter to act as a global economic multiplier. This allows the user to simulate hypothetical wealth increases across all regions.
* **Parameter Name:** `GDP Growth %`
* **Data Type:** `Number`
* **Input Range:** `0` to `1` (Representing 0% to 100% growth)


### **Step 2: The Logic Gate**
This field calculates the **Adjusted GDP** and compares it against the **Living Wage** cost. It uses the **0.4 Sustainability Line** to determine if a country's wealth can support basic survival costs.

```sql
/* What-If Affordability Logic */
CASE 
  WHEN ROUND(Std_Family_Urban / (GDP_per_capita * (1 + GDP_Growth_Parameter)), 2) <= 0.4 
  THEN "Affordable" 
  ELSE "Not Affordable" 
END

```
### **Step 3: Binary Mapping (Visual Connection)**
Converted the text-based status into a numerical score (0/1). This allows the Geo Chart to dynamically swap colors (Red/Green) as the user interacts with the growth slider.

```sql
CASE 
  WHEN What-If Affordability = "Affordable" THEN 1 
  ELSE 0 
END


```
## 🏁 Conclusions
My analysis led to three primary conclusions regarding global economic stability:

1. **Geography is a Financial Barrier:** National minimum wages are often ineffective because they do not account for the massive **"cost of survival" gap** in urban areas (reaching up to 124.6% in some regions).
2. **Structural Inequality:** For single parents, a living wage is currently an economic impossibility in the majority of the world without targeted government intervention or subsidies.
3. **Growth is Not a Magic Cure:** The simulation proves that **67 countries** remain in the "Red Zone" even if their wealth doubles. This proves that we must address the high cost of basic needs (housing, childcare) alongside economic growth.

---

## 💡 Strategic Recommendations
* 📍 **Localized Wage Policies:** Shift from "National Minimums" to region-specific wages that account for the unique cost of living in urban centers.
* 🏠 **Targeted Social Support:** Prioritize housing and childcare subsidies for single-parent households to bridge the affordability gap.
* 📈 **Focus on Productivity:** In high-stress "Red Zone" countries, increasing national productivity (GDP per capita) is just as vital as raising wages to make living costs sustainable.

---

## 🚀 How to Use

### 🎞️ Interactive Dashboard
**View the Live Looker Studio Report](https://datastudio.google.com/u/0/reporting/8b6fd8b6-3569-401e-8b30-5789f8e33352/page/p_ayxhdq6z3d)**

*Interact with the GDP Growth Slider and explore the Affordability Index across 199 nations.*

### 📓 Data Analysis & Python Logic
*Run the Analysis: Open in Google Colab https://github.com/sruthi-raajan9/Global-Living-Wage-Analysis/blob/main/Global_living__wage_analysis.ipynb**

*Review the Python (Pandas) code used for data merging, cleaning, and metric calculation.*

---

## 👤 Contact
**Sruthi Raajan** 📩 [LinkedIn Profile](https://www.linkedin.com/in/sruthi-raajan)  
📂 [GitHub Portfolio](https://github.com/yourusername)




