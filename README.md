# Automatic oral disease diagnosis



## Network
- The multi-class network is using the modified HRNet-W18, which achieves similar classification performance compared with the [official code](https://github.com/HRNet/HRNet-Image-Classification) while reducing the computation complexity and the number of parameters. 
- The code is a slightly modified version of the official code, by removing the BN&FC layers and changing the number of output channels in the representation head.
- For more details using HRNet, please go to the [official website](https://github.com/HRNet/HRNet-Image-Classification).

### requirement
- Pytorch1.0
- CUDA 10.1
- Numpy
- Cv2
- Scikit-learn
- PyCm

### Data preparation
```bash
python prepare_data/create_dataset.py
```
- Note: This was only tested on Windows 10 system by us.

### Training
- The training is only slight differences (with the same method but different super-parameters) on the original implementation.
- The official pre-trained weights [official website](https://github.com/HRNet/HRNet-Image-Classification) are also used. ( loading by the file of "save_weights/hrnetv2_w18_imagenet_pretained.pth" )
- Prepare the dataset, the structure of files are as follows:

        FOLDER/dataset/
        ├── train
        │  ├── cancer
        │  ├── highrisk
        │  ├── lowrisk
        │  ├── normal
        │  └── ucler
        ├── valid
        │  ├── cancer
        │  ├── highrisk
        │  ├── lowrisk
        │  ├── normal
        │  └── ucler

```bash
python ./tools/train.py
```
- The trained models (on oral dataset) are available at [BaiduYun(Access Code:lyjv)](https://pan.baidu.com/s/17YgQ_BE6tURvZNNG50sPeg)

### Testing
- The trained model should be under ./save_weights/
- The original capturing image (by smartphone camera) should be center-cropped (by create_dataset.py) before the test
```bash
python ./tools/test.py            #predict and print results
```

### Report results
- The results were reported based on test results(test_result.csv), using the backend of PyCM and the Scikit-learn library 
```bash
python ./tools/report_result.py    
```

