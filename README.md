# Bioinformatics Portfolio — Saima Imran

**M.Sc. Bioinformatics | Data Coordinator | Precision Medicine**

📧 saimaimran4822@hotmail.com | 📍 Gothenburg, Sweden | 🔗 [GitHub](https://github.com/saima-imran)

---

## About This Portfolio

This repository contains three complete bioinformatics analysis projects developed in R using publicly available genomics data from NCBI GEO. Each project demonstrates a full end-to-end data science pipeline including data retrieval, preprocessing, statistical analysis, and publication-quality visualisation — all following FAIR data principles.

The projects span three disease areas relevant to precision medicine and data-driven life science: **psoriasis**, **breast cancer**, and **diabetes mellitus**.

---

## Portfolio Overview

| Project | Dataset | Disease | Samples | Key Output |
|---------|---------|---------|---------|------------|
| 1 | GSE145305 | Psoriasis vs Healthy | 14 | ceRNA network |
| 2 | GSE45827 | Breast Cancer Subtypes | 155 | Subtype classification |
| 3 | GSE15932 | Diabetes vs Normal | 32 | Precision biomarkers |

---

## Project 1 — Psoriasis ceRNA Network Analysis

**Dataset:** GSE145305 | **Platform:** Affymetrix HTA-2.0 + miRNA-4 Arrays

This project is based on my M.Sc. thesis in Bioinformatics at the University of Skövde, Sweden. It investigates the competing endogenous RNA (ceRNA) regulatory network in psoriasis — a chronic autoimmune skin disease — using multi-omics microarray data integrating mRNA, miRNA, lncRNA and circRNA.

### Analysis Pipeline

```
NCBI GEO (GSE145305)
        ↓
Data preprocessing — oligo, RMA normalisation
        ↓
Differential expression — limma, empirical Bayes
        ↓
miRNA target prediction — miRNAtap, miRDip v4.1
        ↓
Network construction — Cytoscape, STRING, cytoHubba
        ↓
Pathway analysis — clueGO
```

### Key Results

| RNA Type | Up-regulated | Down-regulated | Threshold |
|----------|-------------|----------------|-----------|
| mRNA | 86 genes | 10 genes | p<0.05, \|logFC\|>2 |
| miRNA | 75 miRNAs | 48 miRNAs | p<0.05, \|logFC\|>1.5 |

### Hub Genes Identified

| Type | Genes |
|------|-------|
| Hub lncRNA | XIST, NEAT1, KCNQ1OT1, MALAT1, HCG18, NORAD |
| Hub circRNA | DSC2, GAN, HEPHL1, IFI44L, HK1, STAT1 |
| Hub PPI module | CCNB1, DLGAP5, ANLN, KPNA2, STAT1, OAS2, IFI44L, EIF2AK2 |

### Figures

| Figure | Description |
|--------|-------------|
| `01_mRNA_boxplot.png` | Quality control — expression distribution |
| `02_mRNA_volcano.png` | Volcano plot — significant DEGs in psoriasis |
| `03_heatmap_top30_DEGs.png` | Heatmap — top 30 differentially expressed genes |

---

## Project 2 — Breast Cancer Gene Expression Analysis

**Dataset:** GSE45827 | **Platform:** Affymetrix Human Genome Array

This project analyses gene expression differences across five breast cancer subtypes using public microarray data. The analysis focuses on Triple Negative Breast Cancer (Basal/TNBC) versus Normal tissue — one of the most aggressive and difficult to treat cancer subtypes. This project is directly relevant to precision oncology and personalised medicine.

### Cancer Subtypes

| Subtype | Samples | Clinical Significance |
|---------|---------|----------------------|
| Basal (TNBC) | 41 | Most aggressive — no targeted therapy |
| HER2-enriched | 30 | HER2 positive — targeted by trastuzumab |
| Luminal A | 29 | Best prognosis — hormone receptor positive |
| Luminal B | 30 | Intermediate prognosis |
| Normal | 11 | Healthy breast tissue control |

### Key Results — Basal (TNBC) vs Normal

| Direction | Count | Biological Meaning |
|-----------|-------|-------------------|
| Up in Basal | 4,383 genes | Oncogenes, proliferation markers |
| Down in Basal | 1,967 genes | Tumour suppressors, differentiation |
| Total significant | 6,350 genes | p<0.05, \|logFC\|>1.5 |

### Figures

| Figure | Description |
|--------|-------------|
| `01_BC_expression_boxplot.png` | Colourful boxplot — expression by cancer subtype |
| `02_BC_volcano_Basal_vs_Normal.png` | Volcano plot — TNBC vs Normal |
| `03_BC_heatmap_top40_genes.png` | Heatmap — top 40 DEGs across all subtypes |
| `04_BC_PCA_subtypes.png` | PCA — sample clustering by cancer subtype |

### Scientific Insight

The PCA plot reveals clear separation between Normal tissue and all cancer subtypes, with Basal (TNBC) forming the most distinct cluster — consistent with its unique molecular profile and aggressive clinical behaviour. Luminal A and B show partial overlap, reflecting their shared hormone receptor positivity.

---

## Project 3 — Diabetes Mellitus Precision Medicine Analysis

**Dataset:** GSE15932 | **Platform:** Affymetrix Human Genome Array

This project investigates gene expression differences in pancreatic islet tissue between diabetic patients and healthy controls. Identifying key genes dysregulated in diabetes mellitus contributes to biomarker discovery and personalised treatment strategies — a core goal of precision medicine. The dataset includes three patient groups enabling multi-group comparison.

### Patient Groups

| Group | Samples | Description |
|-------|---------|-------------|
| Cancer + Diabetes | 8 | Pancreatic cancer with diabetes |
| Diabetes Only | 8 | Pure diabetes mellitus |
| Normal | 8 | Healthy pancreatic tissue |
| Other | 8 | Additional controls |

### Key Results — Diabetes vs Normal

| Direction | Count | Biological Meaning |
|-----------|-------|-------------------|
| Up in Diabetes | 7,264 genes | Inflammatory, stress response pathways |
| Down in Diabetes | 3,287 genes | Insulin secretion, beta cell function |
| Total significant | 10,551 genes | p<0.05, \|logFC\|>1.5 |

### Figures

| Figure | Description |
|--------|-------------|
| `01_Diabetes_volcano.png` | Volcano plot — Diabetes vs Normal |
| `02_Diabetes_heatmap.png` | Heatmap — top 40 dysregulated genes |
| `03_Diabetes_PCA.png` | PCA — separation of patient groups |

### Precision Medicine Relevance

The large number of significantly dysregulated genes (10,551) reflects the complex molecular landscape of diabetes mellitus. Key pathways affected include insulin signalling, beta cell apoptosis, and inflammatory response — all critical targets for precision diabetes therapy and personalised treatment selection.

---

## Technical Stack

### R Packages

| Package | Purpose |
|---------|---------|
| `GEOquery` | Download datasets from NCBI GEO |
| `oligo` | Read and preprocess CEL files |
| `limma` | Differential expression analysis |
| `pheatmap` | Professional heatmap visualisation |
| `ggplot2` | Publication quality visualisation |
| `ggrepel` | Non-overlapping gene labels |
| `RColorBrewer` | Scientific colour palettes |
| `tidyverse` | Data manipulation and wrangling |

### External Tools

| Tool | Purpose |
|------|---------|
| Cytoscape | Network visualisation |
| cytoHubba | Hub gene identification |
| STRING plugin | Protein-protein interaction |
| MCODE plugin | Module detection |
| clueGO | Pathway enrichment analysis |

### Databases Used

| Database | Purpose |
|----------|---------|
| NCBI GEO | Raw microarray datasets |
| miRDip v4.1 | miRNA target predictions |
| StarBase | miRNA-lncRNA interactions |
| CircBase | circRNA database |
| LncBase | lncRNA-miRNA interactions |
| STRING | Protein-protein interactions |

---

## Repository Structure

```
psoriasis-ceRNA-network/
│
├── 01_psoriasis_analysis.R          
├── 02_breast_cancer_analysis.R      
├── 03_diabetes_analysis.R           
│
├── Thesis_copy_Bioinformatics.pdf   
│
├── Psoriasis figures/
│   ├── 01_mRNA_boxplot.png
│   ├── 02_mRNA_volcano.png
│   └── 03_heatmap_top30_DEGs.png
│
├── Breast Cancer figures/
│   ├── 01_BC_expression_boxplot.png
│   ├── 02_BC_volcano_Basal_vs_Normal.png
│   ├── 03_BC_heatmap_top40_genes.png
│   └── 04_BC_PCA_subtypes.png
│
├── Diabetes figures/
│   ├── 01_Diabetes_volcano.png
│   ├── 02_Diabetes_heatmap.png
│   └── 03_Diabetes_PCA.png
│
└── README.md
```

---

## How to Run

### Requirements
- R version ≥ 4.0
- RStudio (recommended)
- Internet connection

### Installation

```r
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install(c("GEOquery", "oligo", "limma", "Biobase"))

install.packages(c("tidyverse", "ggplot2", "ggrepel",
                   "pheatmap", "RColorBrewer"))
```

### Run Analysis

```r
source("01_psoriasis_analysis.R")
source("02_breast_cancer_analysis.R")
source("03_diabetes_analysis.R")
```

---

## FAIR Data Principles

All three projects strictly follow FAIR data principles:

| Principle | Implementation |
|-----------|---------------|
| **Findable** | All data from NCBI GEO with persistent accession numbers |
| **Accessible** | Raw data publicly available with no restrictions |
| **Interoperable** | Standard formats (CSV, PNG) and documented workflows |
| **Reusable** | Fully reproducible pipelines with documented methods |

---

## Education

| Degree | Institution | Year |
|--------|-------------|------|
| M.Sc. Bioinformatics (60 ECTS) | University of Skövde, Sweden | 2022 |
| M.Phil. Computer Science | University of Lahore, Pakistan | 2011 |
| Master of Computer Science | Bahauddin Zakariya University, Pakistan | 2008 |
| B.Sc. Computer Science, Physics & Statistics | Islamia University Bahawalpur, Pakistan | 2005 |

**Swedish Credential Assessment (UHR):** Degrees assessed equivalent to Swedish Master's in Computer Science — Ref: 322-15001-21

## Certifications

| Certification | Provider | Status |
|---------------|----------|--------|
| Azure AI Fundamentals (AI-900) | Microsoft | Completed |
| Azure Cloud Fundamentals (AZ-900) | Microsoft | Completed |
| Power BI Data Analyst (PL-300) | Microsoft | In Progress |
| Microsoft Learn | Microsoft | Level 6 — 31,825 XP — 20 Badges |

---

## Contact

**Saima Imran**
M.Sc. Bioinformatics | Data Coordinator | Precision Medicine
📧 saimaimran4822@hotmail.com
📍 Gothenburg, Sweden
🔗 [GitHub](https://github.com/saima-imran)

---

## References

**Project 1:**
> Imran, S. (2022). *Comprehensive Analysis of lncRNA and circRNA Mediated ceRNA Network in Psoriasis*. M.Sc. thesis, University of Skövde, Sweden.

**Project 2:**
> GSE45827. Breast cancer gene expression profiling by array. NCBI GEO. https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE45827

**Project 3:**
> GSE15932. Gene expression in pancreatic islets from donors with and without type 2 diabetes. NCBI GEO. https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE15932

