---
title: "Wifi gets slower and eventually disconects"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by kakkuko on 2017-07-02
Hello,

Freshly installed Ubuntu 16.04 and upgraded to latest. Wifi gets slower with time and after a while it disconnects.

This is my paste:
[http://paste.ubuntu.com/25002951/](http://paste.ubuntu.com/25002951/)

Thanks

---

### Post by praseodym on 2017-07-02
Try changing the wireless driver via cable:

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp /firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf 
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot

---

### Post by jeremy31 on 2017-07-03
I would see if disabling power management on wifi fixes this before installing a new driver as too many kernel modules for wifi do not like it
```
sudo sed -i 's/2/3/' /etc/NetworkManager/conf.d/*
```

Reboot

---

