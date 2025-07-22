# AVSS_TAISC
### **Experiment Reproduction Guide**

This guide provides clear and efficient instructions for reproducing our experimental results. All operations should be executed from the root directory of the dataset: `./AVA_Dataset`.

#### **Process Overview**

This experiment consists of three core steps. To save you time, we provide pre-computed files for the first two, most time-consuming steps (Data Preprocessing and Model Training). You can skip directly to **Step Three** to quickly verify the final results.

---

#### **【Step One】Data Preprocessing: Generating Image Captions**

* **Objective:**
    To use a Vision Language Model (VLM) to generate corresponding text descriptions (captions) for every image in the dataset (both training and test sets).

* **Execution Scripts:**
    * `Step 1.1 - VLM_gt-train.ipynb` (for the training set)
    * `Step 1.2 - VLM_gt-test.ipynb` (for the test set)

* **Output Files:**
    * `road_train_with_captions.csv`
    * `freeway_train_with_captions.csv`
    * `road_test_with_captions.csv`
    * `freeway_test_with_captions.csv`

* **【⚡️ Fast Track / Important Note】**
    This step is extremely time-consuming, requiring over **72 hours** on an NVIDIA GeForce RTX 3080 GPU. **We strongly recommend skipping this step** and using the four `.csv` files already provided in the dataset.

---

#### **【Step Two】Model Training**

* **Objective:**
    To train a model capable of scene classification based on images. This process uses a two-stage training strategy with **5-fold cross-validation** to ensure model robustness.
    1.  **Stage 1:** Freeze the model's backbone and train only the classifier head.
    2.  **Stage 2:** Unfreeze the entire network and perform fine-tuning based on the results of Stage 1.

* **Execution Script:**
    * `Step 2 - VLM_5X3_2.ipynb`

* **【⚡️ Fast Track / Important Note】**
    Model training also requires significant time and computational resources. For your convenience and quick verification, we have provided all the trained model weights. **We recommend downloading the weights directly and skipping to Step Three.**

* **Weight File Download Link:**
    * [Google Drive Download Link](https://drive.google.com/drive/folders/1273DVXNg-JpLvEWh72g19IJhmXj0kn86?usp=drive_link)

---

#### **【Step Three】Running Inference: Reproducing the Final Results**

* **Objective:**
    To load the pre-trained model weights and run predictions on the test set to quickly reproduce our experimental results.

* **Execution Script:**
    * `Step 3 - VLM_(rw).ipynb`

* **Procedure:**
    1.  **Download Weights:** Download the model weights folder from the link provided in **Step Two**.
    2.  **Place Weights:** Move the entire downloaded folder, `output_pytorch_MultiWindow_20250710_131200`, directly into the `./AVA_Dataset` root directory.
    3.  **Prepare Caption Files:** Ensure the test set caption files from **Step One** (either generated or provided), `road_test_with_captions.csv` and `freeway_test_with_captions.csv`, are in place.
    4.  **Run Script:** In the `./AVA_Dataset` directory, execute this Jupyter Notebook (`Step 3 - VLM_(rw).ipynb`) to get the final prediction results.

#### **Notes**

* Please re-confirm that all commands are executed from the `./AVA_Dataset` root directory.
* Before running any script, we recommend checking its internal file path settings to ensure they match your environment's configuration.
* If you encounter any issues during the reproduction process, please feel free to contact us.
