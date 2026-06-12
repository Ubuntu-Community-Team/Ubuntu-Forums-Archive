---
title: "TL-WN822N usb wireless adapter not working properly on 14.04 LTS"
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by valdrin-qunaj on 2015-04-12
Hey,

For some reason the usb wifi adapter is not showing my own router but a couple of the neighbours. When i run lsusb i can see it there "The realtek RTL819CU", so why is it not picking up my own router?

---

### Post by chili555 on 2015-04-12
Please obtain a working internet connection, open a terminal and do:
```
sudo apt-get install git build-essential linux-headers-generic
git clone https://github.com/pvaret/rtl8192cu-fixes.git
cd rtl8192cu-fixes
make
sudo make install
sudo modprobe 8192cu
```

Your wireless should now be working.

Please post back your result; we will have a couple of items to clean up once we're certain it's working.

---

### Post by valdrin-qunaj on 2015-04-13
I get the following error when i try to run 

sudo modprobe 8192cu
modprobe: ERROR: could not insert '8192cu': Device or resource busy

---

### Post by chili555 on 2015-04-13
> **valdrin-qunaj said:**
> I get the following error when i try to run 

sudo modprobe 8192cu
modprobe: ERROR: could not insert '8192cu': Device or resource busyPlease try a reboot instead.

---

