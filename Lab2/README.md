# Lab 2: CNN for Image Classification (PetFinder)

**Prerequisite:** CNN Fundamentals lecture, Lab 1, and Assignment 1
**Submission:** GitHub repo URL and notebook URL on Canvas
**Due:** September 28, 2026 at 12 pm

## A Note on Format

Unlike Lab 1, there is no fill-in-the-blank starter code here. You will write the full model, from data loading through evaluation, yourself. Use the CNN Fundamentals lecture and Lab 1 as your reference for syntax and structure, but the decisions, and the code, are entirely yours this time.

The starter notebook in this folder (`Lab2_CNN_PetFinder_Starter.ipynb`) contains markdown instructions for each section and empty code cells for you to fill in. It is a guide, not a template with answers.

## Getting the Data

The dataset is provided in this folder, in `petfinder_data/`, containing `train.csv` and a `train_images/` folder of photos.

In your Colab notebook, clone your fork to access the data:

```python
!git clone <your-fork-url>
```

Then point your code at the data:

```python
import pandas as pd

df = pd.read_csv("<your-repo-name>/Lab2/petfinder_data/train.csv")
img_dir = "<your-repo-name>/Lab2/petfinder_data/train_images"
```

## Learning Objectives

By the end of this lab, you will be able to:
- Build an image loading pipeline from raw image files, independently
- Design, build, and train a CNN from scratch, with no provided architecture
- Justify every architecture decision using the conventions from lecture
- Diagnose a CNN's fit from its training curve
- Apply a technique from Assignment 1 to improve the model
- Evaluate an image classifier using accuracy and a confusion matrix

## Part A: Load and Prepare the Data

1. Load `train.csv` and inspect it. You need the `PetID` and `Type` columns (`Type`: 1 = Dog, 2 = Cat).
2. Write code that loads each pet's primary photo from `train_images/`, resizes it to a consistent size of your choosing, and normalizes pixel values.
3. Build your `X` (images) and `y` (Dog/Cat) arrays.
4. Split into train and test sets. Decide, and justify, whether you need to stratify this split.
5. Report how many images you ended up with, and whether Dog and Cat are reasonably balanced.

Not every `PetID` will have a matching photo file. Your loading code should skip missing images gracefully rather than erroring out.

## Part B: Build a CNN From Scratch

Design and build your own CNN architecture. There is no template. Decide:
- How many Conv2D and MaxPooling2D layers, and why
- How many filters at each layer, and how that number changes as you go deeper
- What kernel size, and why
- What your Dense classifier head looks like after the Flatten layer
- What output layer and activation fits a Dog vs. Cat task specifically

Write a paragraph justifying every choice, referencing the conventions from lecture.

## Part C: Train and Diagnose

Train your model, plot training vs. validation loss and accuracy, diagnose the fit with specific evidence, and evaluate on the test set.

## Part D: Improve the Model

Choose one path based on what Part C showed:
- **If overfitting:** apply Dropout, Early Stopping, or both
- **If not overfitting:** use Keras Tuner to search at least 2 hyperparameters, maintaining test-set discipline (tuning touches train/validation only, test set touched once at the end)

## Part E: Compare and Evaluate

Report baseline vs. improved test accuracy, fit pattern, and a confusion matrix for the improved model. Discuss which class is misclassified more often and why.

## Part F: Look at Your Mistakes

Display 3 to 5 misclassified images and discuss what they have in common.

## Deliverables Checklist

- [ ] New notebook created, previous labs and assignments left unedited
- [ ] Image loading pipeline built independently, dataset size and balance reported
- [ ] Full CNN architecture designed and built from scratch, with written justification
- [ ] Baseline trained, curves plotted, fit correctly diagnosed
- [ ] One improvement path applied and justified
- [ ] Comparison table and confusion matrix completed
- [ ] Misclassified examples inspected with written observations

## Grading Rubric (100 points)

| Section | Points | Criteria |
|---|---|---|
| A: Data Pipeline | 20 | Correct independent image loading, reasonable resizing/normalization, correct split with justified stratification decision |
| B: Architecture Design | 25 | Complete original architecture, sound written justification referencing lecture conventions, correct output layer for a binary task |
| C: Training and Diagnosis | 20 | Correct training and plotting, accurate diagnosis with specific evidence |
| D: Improvement | 25 | Correct application of chosen technique, clear reasoning for the choice |
| E and F: Evaluation | 10 | Comparison table and confusion matrix completed, thoughtful inspection of misclassified images |

Grading note: since this lab has no template, expect real variation in image size, architecture depth, and filter counts across submissions. Grade on whether the choices are reasonable and justified, and whether the code runs and produces honest results, not on matching any specific reference architecture.
