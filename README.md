# COMET: Clinical and Omics Multi-Modal Analysis Enhanced with Transfer Learning
COMET is a machine learning framework that incorporates large, observational electronic health record (EHR) databases and transfer learning to improve the analysis of small datasets from omics studies.
## Overview
This repo contains the code used for the analyses and results presented in our manuscript. Due to HIPAA constraints, we cannot share the EHR data used in our study. The proteomics data for the onset of labor cohort can be found [here](https://datadryad.org/stash/dataset/doi:10.5061/dryad.280gb5mpd). Due to UK Biobank policies, we cannot share the proteomics data from the UK Biobank cohort.
## Repo Organization
There are two folders: Onset of Labor and Cancer. Within each folder, we have Jupyter notebooks used for various aspects of the data processing and analysis. Within the onset of labor folder we have:
- process_EHR_data_full_PT_cohort.ipynb: This notebook contains the code necessary to process EHR data for the pre-training cohort from extracts of OMOP tables to matrices that can be direct inputs to the ML models. This includes the training of the word2vec model to embed EHR codes.
- process_EHR_data_omics_cohort.ipynb: This notebook contains the code necessary to process EHR data for the omics from extracts of OMOP tables to matrices that can be direct inputs to the ML models. This includes the training of the word2vec model to embed EHR codes.
- experiments.ipynb: This notebook contains all other code for experiments and analysis. Most notably, it contains the code for the actual architecture of our models, hyperparameter optimization, actual experiments, and downstream analyses including feature importance computation and visualization of the parameter space in Figure 6.

Within the cancer folder we have:
- process_EHR_data_omics.ipynb: This file contains the queries to pull the patient cohorts and the data necessary to train the word2vec models, and trains the word2vec models for both the omics and pre-training cohorts. This file also contains downstream processing to pull the feature data from the patients in the omics cohort and ultimately saves a CSV containing the person-day embeddings.
- process_PT_data.ipynb: This file contains the queries to pull the feature data from the pre-training cohort and downstream processing to compute person-day embeddings. 
- grouped_embeddings_to_matrices.ipynb: contains code to convert person-day embeddings to feature matrix for RNN input, also computes other inputs for ML (length of sequence based on number of days of data, outcome data, mapping between patient ID and indices in the feature matrix), also contains code used to extract all proteomics data
- experiments.ipynb: This notebook contains all other code for experiments and analysis. Most notably, it contains the code for the actual architecture of our models, hyperparameter optimization, actual experiments, and downstream analyses including feature importance computation and visualization of the parameter space in Figure 6.


