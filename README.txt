## PARSE DATA ## 

1) CMD: 
- download raw data at: https://github.com/shiehn/chord-melody-dataset
- save raw data as: ./CMD/dataset/abc...
- run command: python3 process_data.py --dataset CMD 

outputs:
1) saves npy files for the parsed features (saved directory ex: ./CMD/output/~) 
2) saves train/val/test batches (saved directory ex: ./CMD/exp/train/batch/~)
3) saves h5py dataset for the train/val/test batches (saved filename ex: ./CMD_train.h5)
---------------------------------------------------------------------------------------------
## TRAIN MODEL ## 

1) STHarm 
python3 trainer.py [dataset] STHarm
2) VTHarm 
python3 trainer.py [dataset] VTHarm
3) rVTHarm  
python3 trainer.py [dataset] rVTHarm 

* [dataset] -> CMD

outputs:
1) model parameters/losses checkpoints (saved filename ex: ./trained/STHarm_CMD)

---------------------------------------------------------------------------------------------
## TEST MODEL ## 
python3 test.py [dataset] [song_ind] [start_point] [model_name] [device_num] [alpha]

* [dataset] -> CMD 
* [song_ind] -> index of test files 
* [start_point] -> half-bar index ex) if you want to start at the 1st measure: start_point=0 / at the second half of the 1st measure: start_point=1
* [model_name] -> STHarm / VTHarm / rVTHarm 
* [device_num] -> number of CUDA_DEVICE
* [alpha] -> alpha value for rVTHarm / if not fed (different model), ignored

outputs:
2) saves generated(sampled) MIDI / GT MIDI (saved filename ex: ./Sampled__*.mid, ./GT__*.mid)
