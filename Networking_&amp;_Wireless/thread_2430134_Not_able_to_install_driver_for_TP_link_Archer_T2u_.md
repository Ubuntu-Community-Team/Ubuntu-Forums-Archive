---
title: "Not able to install driver for TP link Archer T2u on Ubuntu 18.04"
date: 2019-10-28
forum: Networking &amp; Wireless
---

### Post by darwinclown on 2019-10-28
I recently switched from windows to Ubuntu and not able to use tp link adapter

```
>lsusb
Bus 001 Device 005: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 003: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 008: ID 093a:2532 Pixart Imaging, Inc. 
_*Bus 002 Device 011: ID 2357:011f  *_
Bus 002 Device 002: ID 413c:2113 Dell Computer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I also tried steps mentioned in 
[https://ubuntuforums.org/showthread.php?t=2358876&page=2&p=13787798#post13787798](https://ubuntuforums.org/showthread.php?t=2358876&page=2&p=13787798#post13787798)

but even after doing everything and rebooting the system adapter doesn't seem working. 


```
> lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic
```

The adapter is named as 
TP-Link Archer T2U AC600 Wireless Wi-Fi Dual Band USB Adapter on Amazon.

after trying multiple askubuntu posts and articles and getting frustrated on tplink for not providing good support for this! I decided to post here for help.
Its disheartening why the official website has video guide for windows and mac but not for linux. 
Please help me
Thanks for your time.

---

### Post by praseodym on 2019-10-28
Try this one
```

sudo apt install git dkms build-essential
git clone https://github.com/jeremyb31/rtl8812au-1.git
cd rtl8812au-1
sudo ./dkms-install.sh
```
From here: [https://askubuntu.com/questions/1149117/tp-link-ac600-archer-t2u-nano-driver-for-ubuntu-18-04](https://askubuntu.com/questions/1149117/tp-link-ac600-archer-t2u-nano-driver-for-ubuntu-18-04)

First uninstall the other one

---

### Post by darwinclown on 2019-10-28
I tried that too since that comes first in the google search. Didn't work.
Moreover, it says [B]T2U with ID 2357:011e 

[/B]However as you can see above for mine it is 
**Bus 002 Device 011: ID 2357:011**_*f*_  
**f** instead of **e**

---

### Post by jeremy31 on 2019-10-29
```
cd rtl8812au-1
sudo ./dkms-remove.sh
git pull
sudo ./dkms-install.sh
```
Reboot

---

### Post by darwinclown on 2019-10-29
Its working now. 

Thank you so much :D

---

### Post by waltdom on 2019-12-07
thank [**[COLOR=#C61919][B]jeremy31**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1924242"), work perfect Device  AC600 Wireless Dual Band USB Adapter Archer T2U in S.O Linux Mint 19.2 Tina

---

### Post by cawchapin on 2019-12-28
> **praseodym said:**
> Try this one
```

sudo apt install git dkms build-essential
git clone https://github.com/jeremyb31/rtl8812au-1.git
cd rtl8812au-1
sudo ./dkms-install.sh
```
From here: [https://askubuntu.com/questions/1149117/tp-link-ac600-archer-t2u-nano-driver-for-ubuntu-18-04](https://askubuntu.com/questions/1149117/tp-link-ac600-archer-t2u-nano-driver-for-ubuntu-18-04)

First uninstall the other one

Thanks Praseodym, just moved house now I am completely free of ethernet cables!  :KS:P

---

