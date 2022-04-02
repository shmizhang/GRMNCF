
# GRMNCF: Geometrical Relation-aware  Multi-modal Network with  Confidence Fusion for Text-based Image Captioning
## Introduction:
Pytorch implementation  for GRMNCF.  
  
## Installation:
Our implementation is based on [mmf](https://github.com/facebookresearch/mmf) framework, and and built upon [M4C-Captioner](https://github.com/ronghanghu/mmf/tree/project/m4c_captioner_pre_release/projects/M4C_Captioner). Please refer to [mmf's document](https://mmf.sh/docs/) for more details on installation requirements.
## Dataset:
  The original Textcaps dataset is from https://textvqa.org/textcaps/dataset/.  Please download them from the links below and and extract them under dataname  directory:
 (1) [object Faster R-CNN Features of TextCaps](https://dl.fbaipublicfiles.com/pythia/features/open_images.tar.gz)
  
 (2)[OCR Faster R-CNN Features of TextCaps](https://dl.fbaipublicfiles.com/pythia/m4c/data/m4c_textvqa_ocr_en_frcn_features.tar.gz)
 
 (3)[detectron weights of TextCaps](http://dl.fbaipublicfiles.com/pythia/data/detectron_weights.tar.gz)
  
  
  Following [CNMT's dataset](https://github.com/wzk1015/CNMT), we use it to build our model.
  At last, our data directory (*/home/username/.cache/torch/mmf/data/datasets/dataname/*) structure should look like this:
  
  |-m4c_textvqa_ocr_en_frcn_features
  
  |-open_images
  
  |-----detectron_fix_100
  
  |-imdb
  
  |-----imdb_train.npy
  
  |-----imdb_val_filtered_by_image_id.npy
  
  |-----imdb_test_filtered_by_image_id.npy
  
## Running the code:

(1) to train the grmncf model on the TextCaps training set:
CUDA_VISIBLE_DEVICES=0,1 mmf_run datasets=cnmtdata \
    model=grmncf \
    config=projects/grmncf/configs/grmncf_defaults.yaml \
    env.save_dir=./save/grmncf/defaults \
    run_type=train_val
    
 
    
    
   
## Annotation:
  split_dataset.py:                   split the train, valid and test sets.     
  vae.py: bayesian Learning part.  
  Yelp_social_relation.py (Equation.11 Fij):  compute the  the friendship similarity in Yelp dataset.  
  geographical_correlation_level.py (Equation.12):  compute the geographical correlation level between POIs.
