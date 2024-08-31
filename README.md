# Sales Forecasting for a Retail Company

![featured](https://github.com/pabloelt/sales-forcasting-for-a-retail-company//blob/main/00_Imagenes/featured.jpg?raw=true)

##### Table of Contents 
* [Introduction](#introduction)
* [Objectives](#objectives)
* [Project results](#project-results)
   * [Recommended actions from EDA](#recommended-actions-from-eda)
   * [Lead segmentation model](#lead-segmentation-model)
   * [Predictive lead scoring model](#predictive-lead-scoring-model)
* [Project structure](#project-structure)
* [Instructions](#instructions)

<div align="justify">
 
## Introduction

The client for this project is a large retailer based in the United States. The company has identified issues in its warehouse operations, leading to losses and stock-outs for several products. The objective is to implement a forecasting model using artificial intelligence algorithms to predict the appropriate stock levels for at least the next 8 days. This initiative aims to enhance operational efficiency and increase the company’s profitability.

 * [See a technical explanation of the project here](https://pabloelt.github.io/project/project6/)

## Objectives

The primary objective is to develop a forecasting model utilizing a set of machine learning algorithms to predict sales for the next 8 days at the store-product level. These algorithms are trained using the extensive three-year history available in the retail company’s SQL database, employing massive modeling techniques to ensure accuracy and reliability.

## Project results

### Recommended actions from EDA

Several insights have been uncovered through the exploratory data analysis. The main actionable initiatives are summarized below.

1. With the current information collected by the company, it is challenging to determine whether intermittent demand is due to stock-outs or simply zero demand for the product. Therefore, it is highly recommended to track warehouse data closely.

2. To optimize sales and reduce warehouse costs, implementing a forecasting model based on machine learning algorithms can be highly effective. A bottom-up approach, starting at the product level, is particularly recommended in this context.

3. Discounts have proven to be quite successful, especially for product 090, which is the top seller. It may be worthwhile to apply this strategy to other products and evaluate the overall impact.

4. Saturdays and Sundays show the highest sales volumes, presenting an opportunity to develop targeted strategies and campaigns.

5. Special days like Thanksgiving, Labor Day, and Easter generate significant sales. These occasions should be thoroughly analyzed, and marketing strategies should be developed to enhance the company’s profitability.


### Sales Forecasting model

In this project, we have developed a robust recursive forecasting model based on a set of machine learning algorithms for sales prediction. This model analyzes each product-store combination individually and tailors the algorithm to predict demand for the next 8 days. LightGBM, with standard hyperparameters, was identified as the best option for predictive performance. The model was tested with new data from December 2015, yielding satisfactory results, with a mean absolute error of approximately 4.73.

This forecasting model will help to reduce warehouse costs and stock-outs, significantly boosting the company's performance and profitability.


## Project structure

* 📁 00_Imagenes: Contains project images.
* 📁 01_Documentos: Contains basic project files:
  * <mark>retail.yml</mark>: Project environment file.
  * <mark>FaseDesarrollo_Transformaciones.xlsx</mark>: Support file for designing feature transformation processes.
  * <mark>FaseProduccion_Procesos.xlsx</mark>: Support file for designing final production script.
* 📁 02_Datos
  * 📁 01_Originales
    * <mark>Leads.csv</mark>: Original dataset.
  * 📁 02_Validacion
    * <mark>validacion.csv</mark>: Sample extracted from the original dataset at the beginning of the project, which is used to check the correct performance of the model once it is put into production.
  * 📁 03_Trabajo
    * This folder contains the datasets resulting from each of the stages of the project (data quality, exploratory data analysis, variable transformation, ...).
* 📁 03_Notebooks
    * 📁 02_Desarrollo
      * <mark>01_Set Up.ipynb</mark>: Notebook used for the initial set up of the project.
      * <mark>02_Calidad de Datos.ipynb</mark>: Notebook detailing and executing all data quality processes.
      * <mark>03_EDA.ipynb</mark>: Notebook used for the execution of the exploratory data analysis.
      * <mark>04_Transformacion de datos.ipynb</mark>: Notebook that details and executes the data transformation processes necessary to prepare the variables for the models.
      * <mark>05_Modelizacion para No Supervisado.ipynb</mark>: Notebook for modeling the unsupervised Kmeans algorithm used to perform lead segmentation.
      * <mark>06_Preselección de variables.ipynb</mark>: Notebook used to make a selection of the final variables to be entered into the models.
      * <mark>07_Modelizacion para Clasificacion.ipynb</mark>: Notebook for modeling the predictive lead scoring model. It contains the model selection, the hyperparametrization, the selection of the optimal discrimination threshold, and the evaluation of results.
      * <mark>08_Preparacion del codigo de produccion.ipynb</mark>: Notebook used to compile all the quality, transformation, and variable selection processes, as well as the final model and execution and retraining processes. It is used to create the final retraining and execution pipes that condense all the aforementioned processes.
      * <mark>09_Codigo de reentrenamiento.ipynb</mark>: Notebook to retrain the model with new data when necessary.
      * <mark>10_Codigo de ejecucion.ipynb</mark>: Notebook to execute the final model and obtain the results.
* 📁 04_Modelos
  * <mark>pipe_ejecucion.pickle</mark>: Pipe that condenses the final trained model as well as all necessary prior data transformations.
  * <mark>pipe_entrenamiento.pickle</mark>: Pipe that condenses the entire training process. It can be used to retrain the model with new data when necessary.
  * <mark>optimal_disc_threshold.pickle</mark>: Contains the value of the optimal discrimination threshold of the model that maximizes the company's ROI. It is used by pipe_ejecucion.pickle and is updated when re-training the model with pipe_entrenamiento.pickle.
* 📁 05_Resultados
  * <mark>Resultados del proyecto.ipynb</mark>: Notebook summarising the insights and KPIs improvements achieved from the exploratory data analysis as well as from the execution of the scoring and lead segmentation machine learning models.
  * <mark>Codigo de ejecucion.py</mark>: Python script to execute the model and obtain the results.
  * <mark>Codigo de reentrenamiento.py</mark>: Python script to retrain the model with new data when necessary.
  * <mark>variables_finales.pickle</mark>: Names of the final features pre-selected for the input of the predictive model.

## Instructions

The project should be run using the same environment in which it was created.

* Project environment can be replicated using the <mark>leadscoring.yml</mark> file, which was created during the set up phase of the project. It can be found in the folder <mark>01_Documentos</mark>.
* To replicate the environment it is necessary to copy the <mark>leadscoring.yml</mark> file to the directory and use the terminal or anaconda prompt executing:
  * conda env create --file leadscoring.yml --name project_name

On the other hand, remember to update the project_path variable of the notebooks to the path where you have replicated the project.
