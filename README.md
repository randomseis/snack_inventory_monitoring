# snack_inventory_monitoring
A snack inventory monitoring model, mainly for Meiji's Hello Pandas biscuit. 

This project uses a fine-tuned YOLOv5 model to detect the (lack of) Hello Pandas from a video stream and using the Gmail API, message correspoding peron to replenish the inventory.

## Features

### Detect Hello Panda in photos
- The model is able to take in a photo or a folder of photos to detect the presence of Hello Panda.


### Detect Hello Panda in video stream
- The model is able to take in a video stream and detect 81 objects (80 from the COCO128 dataset and 1 from our custom Hello Panda dataset)

 ![image info](imgs/demo.gif)


## Installation
Clone repo and install requirements.txt in a Python>=3.8.0 environment, including PyTorch>=1.8.

```bash
git clone https://github.com/randomseis/snack_inventory_monitoring.git #clone
cd aiap-next-research-and-development
pip install -r requirements.txt  # install
```

For e-mail functionality

Change the `.env` file. We recommend using the gmail app password for further privacy. https://support.google.com/accounts/answer/185833?hl=en

```bash
SENDER_EMAIL = "YOUR EMAIL"
GMAIL_APP_PASSWORD = "YOUR GOOGLE APP PASSWORD"
SUBJECT = "YOUR SUBJECT"
RECIPIENTS = "RECIPIENT 1 EMAIL, RECIPIENT 2 EMAIL, ..."
BODY = "YOUR MESSAGE"
```

## Inference with detect.py
`detect.py` runs inferences on a variety of sources and saves resuls to `runs/detect`.

```bash
python detect.py --weights models/yolov5mfinetuned.pt --source 0       #webcam
                                                               img.jpg #image
```
