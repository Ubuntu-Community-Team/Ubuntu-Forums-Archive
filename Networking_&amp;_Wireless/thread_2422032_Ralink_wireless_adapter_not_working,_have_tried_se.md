---
title: "Ralink wireless adapter not working, have tried several commands"
date: 2019-07-01
forum: Networking &amp; Wireless
---

### Post by lowiqgamer on 2019-07-01
So here are the commands I've tried in terminal, after which I still can't wirelessly connect to my network:

echo "options rt2800pci nohcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
sudo apt update
sudo apt dist-upgrade

After trying these commands, I went ahead and installed pastebinit so I could get my wireless info, which is in this link:
[http://paste.ubuntu.com/p/nS7Dj7Ng9n/](http://paste.ubuntu.com/p/nS7Dj7Ng9n/)

I've also changed the settings in the network mananger according to these images:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=276846&stc=1&thumb=1&d=1487398298[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=276847&stc=1&thumb=1&d=1487398297[/IMG]

Any help would be appreciated, thanks.

---

### Post by praseodym on 2019-07-01
Try this one

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf 5641297-RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
For Bluetooth

```
sudo add-apt-repository ppa:blaze/rtbth-dkms
sudo apt-get update
sudo apt install dkms rtbth-dkms blueman
sudo modprobe -v rtbth 
```
Reboot

---

