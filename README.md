# kaldi-installation
Instructions to install Kaldi in Linux environment


## Prepare
```
sudo apt install g++ zlib1g-dev libtool subversion libatlas3-base cmake automake autoconf sox ffmpeg unzip gfortran python2.7
sudo ln -s -f bash /bin/sh
```

## Download
```
git clone https://github.com/kaldi-asr/kaldi.git kaldi --origin upstream
```

## Install tools

```
cd kaldi/tools
./extras/check_dependencies.sh
touch python/.use_default_python
sudo bash ./extras/install_mkl.sh

make -j 32
chmod 755 openfst-1.7.2

./extras/install_srilm.sh
./extras/install_irstlm.sh
```

## Install Kaldi
```
cd ../src/
```

## No GPU
```
./configure --shared --use-cuda=no
```

## GPU
```
./configure --shared --use-cuda=yes --cudatk-dir=/usr/local/cuda-11.1
```
or
```
./configure --shared --use-cuda=yes --cudatk-dir=/home/xxx/cuda-11.1
```
```
make clean
make depend -j 32
make -j 32
```
## Update
```
cd kaldi
git status
git pull upstream master
```
