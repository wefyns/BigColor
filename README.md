## BigColor: Colorization using a Generative Color Prior for Natural Images<br><sub>Official PyTorch Implementation of the ECCV 2022 Paper</sub>

![Teaser image 1](./srcs/teaser_1.png)

**BigColor: Colorization using a Generative Color Prior for Natural Images**<br>
Geonung Kim, Kyoungkook Kang, Seongtae Kim, Hwayoon Lee, Sehoon Kim, Jonghyun Kim, Seung-Hwan Baek, Sunghyun Cho<br>

[\[Paper\]](https://github.com/KIMGEONUNG/BigColor)
[\[Supple\]](https://github.com/KIMGEONUNG/BigColor)
[\[Project Page\]](https://github.com/KIMGEONUNG/BigColor)

Abstract: *For realistic and vivid colorization, generative priors have recently been exploited. However, such generative priors often fail for in-the-wild complex images due to their limited representation space. In this paper, we propose BigColor, a novel colorization approach that provides vivid colorization for diverse in-the-wild images with complex structures. While previous generative priors are trained to synthesize both image structures and colors, we learn a generative color prior to focus on color synthesis given the spatial structure of an image. In this way, we reduce the burden of synthesizing image structures from the generative prior and expand its representation space to cover diverse images. To this end, we propose a BigGAN-inspired encoder-generator network that uses a spatial feature map instead of a spatially-flattened BigGAN latent code, resulting in an enlarged representation space. Our method enables robust colorization for diverse inputs in a single forward pass, supports arbitrary input resolutions, and provides multi-modal colorization results. We demonstrate that BigColor significantly outperforms existing methods especially on in-the-wild images with complex structures.*


### Envorionment

We use python3.8 in _Ubuntu 20.04.2 LTS_ operation system as development environment.
We provide a anaconda environment file for running the code. 
Run the instruction below on your bash prompt.

```
conda env create -f environment.yml
```

### Pretrained Models

The training for BigColor needs some pretrained models and configuration files.
To automatically download the files, we provide a script requiring _gdown_.
Therefore you should install _gdown_ using the script below.

```
pip install gdown
pip install --upgrade gdown
```

After installing gdown, run the command below on your bash propmt for the prerequisite.  

```
./download-pretrained.sh
```

If you want to get a pretrained BigColor checkpoint, also run the command below 

```
./download-bigcolor.sh
```

It is possible to fail to download the file using the bash scripts.
Then use this [link](https://drive.google.com/drive/folders/1nLzgE5WJnxp5WF1dkpa1ts6bZ6tVwtep?usp=sharing) for download using google drive.

Finally, a structure of the files is as follows.

```
BigColor
├── ckpts
│   └── bigcolor
│       ├── args.pkl
│       ├── EG_011.ckpt
│       └── EG_EMA_011.ckpt
├── pretrained
│   ├── config.pickle
│   ├── D_256.pth
│   ├── G_ema_256.pth
│   └── vgg16.pickle

...
```

### Datasets

For training with ImageNet1K, you have to download ImageNet1K training and validation set.
Unfortunately, the validation set is generally not organized for each class lables, that is, _all validation images stored in a directory_. 
So, we provide a arranged validation files based on class lable. 
Use this [link](https://drive.google.com/drive/folders/1nLzgE5WJnxp5WF1dkpa1ts6bZ6tVwtep?usp=sharing)
and download the file: _imageNet_validation_grouping.zip_

As a results, the final directory structure of the data is as follows

```
tree structure

...
```

### Colorization
![Teaser image 2](./srcs/teaser_2.png)

#### ImageNet1K Validation 

inference results available in


```
./scripts/infer.bigcolor.e011.sh
```

#### Real Gray Colorization

```
./scripts/colorize.real.sh
```

#### Multi-modal Solutions

```
./scripts/colorize.multi_c.sh
```

```
./scripts/colorize.multi_z.sh
```

### Citation

```
@inproceedings{Kim2022Bigcolor,
  title     = {BigColor: Colorization using a Generative Color Prior for Natural Images},
  author    = {Geonung Kim,Kyoungkook Kang,Seongtae Kim,Hwayoon Lee,Sehoon Kim,Jonghyun Kim,Seung-Hwan Baek,Sunghyun Cho},
  booktitle = {Proc. ECCV},
  year      = {2022}
}

```
