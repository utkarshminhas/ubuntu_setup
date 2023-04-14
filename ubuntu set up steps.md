ubuntu set up steps
# installing snap packages
```
sudo snap install code --classic
sudo snap install discord
```
# installation through apt
```
sudo apt install git -y
sudo apt install solaar -y
sudo apt install gcc -y
sudo apt-get install g++ freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libglu1-mesa libglu1-mesa-dev -y
sudo apt-get install libfreeimage3 libfreeimage-dev -y
``` 
python is already installed

# cuda pre installation steps
```
sudo apt-get install linux-headers-$(uname -r)
```
- select  commands from here to remove the outdated signing key
    - https://docs.nvidia.com/cuda/cuda-installation-guide-linux/#ubuntu
```
sudo apt-key del 7fa2af80
```

# actual installation steps
- go to nvidia cuda toolkit downloads page, BUT MAKE SURE to SELECT the right version(at the time I made thism it was 11.8 for me, as per tensorflow and pytorch docs)
    - enter the deets anually here
        - https://developer.nvidia.com/cuda-downloads
    - pre filled deets as per my preferences
        - https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local
## I am pasting the commands here from above for my own convenience
- <b>but while installing at some farway future, go to the page and get the commands from there instead of copying them from here</b>
- Download Installer for Linux Ubuntu 22.04 x86_64
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
```
```
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
```
```
wget https://developer.download.nvidia.com/compute/cuda/12.1.0/local_installers/cuda-repo-ubuntu2204-12-1-local_12.1.0-530.30.02-1_amd64.deb
```
```
sudo dpkg -i cuda-repo-ubuntu2204-12-1-local_12.1.0-530.30.02-1_amd64.deb
```
```
sudo cp /var/cuda-repo-ubuntu2204-12-1-local/cuda-*-keyring.gpg /usr/share/keyrings/
```
```
sudo apt-get update
```
```
sudo apt-get -y install cuda
```

# post installation steps
- https://docs.nvidia.com/cuda/cuda-installation-guide-linux/#post-installation-actions
    - <b> set the correct cuda version(the version which you installed in your PC) in the command below</b>
  
```export PATH=/usr/local/cuda-11.8/bin${PATH:+:${PATH}}```
- [13.2.1. Install Persistence Daemon](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/#install-persistence-daemon)

``` /usr/bin/nvidia-persistenced --verbose ```
- 13.2.3.1. Verify the Driver Version
```
cat /proc/driver/nvidia/version
```
# cloning the cuda samples repo
```
cd ~/Desktop
git clone https://github.com/NVIDIA/cuda-samples.git
```
