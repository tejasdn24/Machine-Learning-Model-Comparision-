Fighter Aircraft Classification using VGG19 and Xception
  This repository contains a deep learning project for classifying eight modern military aircraft types (B2, B21, F16, F22, F35, Rafale, Su57, Tejas) using transfer learning with VGG19 and Xception. The repo        includes training scripts, evaluation code, and result files such as confusion matrices, ROC curves, and per‑class metrics.

- Project Overview
  Multi‑class image classification with 8 aircraft classes.

- Two convolutional neural network models: VGG19 and Xception (transfer learning).

- Evaluation with accuracy, precision, recall, F1‑score, and ROC–AUC at both overall and per‑class levels.

- Setup and Installation
  1. Clone the repository
     
         git clone https://github.com/tejasdn24/Machine-Learning-Model-Comparision-.git
         cd Machine-Learning-Model-Comparision-
     
  3. Create and activate a virtual environment (optional)
     
           python -m venv .venv
     # Windows
         .venv\Scripts\activate
     # Linux / macOS
         source .venv/bin/activate
  5. Install dependencies
  
          pip install -r requirements.txt

- Dataset
  Images are organized in subfolders named after their class labels: B2, B21, F16, F22, F35, Rafale, Su57, Tejas.
  
  Training, validation, and test sets are stored under data/train, data/val, and data/test respectively.
  
  The training scripts assume directory‑based loading (for example, Keras ImageDataGenerator or image_dataset_from_directory).

- How to Run
    1. Train VGG19

            python src/train_vgg19.py
       Typical behavior:
          Loads training and validation images from data/train and data/val.
          Builds a VGG19‑based model with a custom classification head for 8 classes.
          Trains the model and saves:
          Model weights (for example, vgg19_best.h5).
          Training history in results/training_history_VGG19_8classes.xlsx.

    3. Train Xception
       
           python src/train_xception.py
        Typical behavior:
         Uses Xception as the base network.
         Trains on the same dataset and saves:
         Model weights (for example, xception_best.h5).
         Training history in results/training_history_Xception_8classes.xlsx.
       
       3. Evaluate Models
       
               python src/FinalOutput.py
          Loads the saved VGG19 and Xception models.
          Evaluates them on data/test. 
          Writes per‑image predictions to:
          results/test_results_vgg19.xlsx    
          results/test_results.xlsx (Xception)
          
          Generates and saves:     
            Confusion matrices: vgg19ConfusionMatrix.jpg, xceptionConfusionMatrix.jpg              
            ROC curves: vgg19ROC.jpg, xceptionROC.jpg.              
            Annotated prediction grids: vgg19AnnotedImage.jpg, xceptionAnnotedImage.jpg.
           
- Evaluation and Findings
      For each model and each class (B2, B21, F16, F22, F35, Rafale, Su57, Tejas), the project reports:
      Precision, recall, F1‑score, and support derived from the confusion matrices.
      Per‑class ROC–AUC values showing how well each class is separated from the others.      
      Example high‑level observations you can refine:

- Both models perform best on visually distinctive classes such as F16, with high precision, recall, F1‑score, and AUC.
      Performance is lower on under‑represented or visually similar classes such as Tejas and B21, where more confusion and lower recall are observed.

- Limitations and Future Work
      Limited dataset size and class imbalance across aircraft types make it harder to generalize to new images.
      Visual similarity between certain aircraft (similar silhouettes, angles, and camouflage) causes misclassifications.

- Future work: add more data, experiment with stronger architectures (e.g., EfficientNet, ResNet, ViT), apply data augmentation and class‑balanced training, and explore deployment to embedded platforms.


 


