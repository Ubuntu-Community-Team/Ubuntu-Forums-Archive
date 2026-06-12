---
title: "Huawei E220"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by redbook4574 on 2010-05-19
I know this has been asked many times before but I have forgotten the answer,

How do I stop the E220 loading the virtual cd=rom every time it is plugged in ???


Thanks in advance

---

### Post by hipocrita20 on 2010-05-25
apt-get install usb-modeswitch):P

---

### Post by bumanie on 2010-05-25
You need either:
1. These two packages
usb-modeswitch-data_20100127-1_all.deb
usb-modeswitch_1.1.0-2_i386.deb

or 

2. The current development kernel from [here]("https://wiki.ubuntu.com/KernelMainlineBuilds") 

Both worked with my E620, but the latest kernel 2.6.32-22-generic does too.

---

### Post by philinux on 2010-05-25
sudo first > **hipocrita20 said:**
> apt-get install usb-modeswitch):P



Also see the General Help Sticky.

---

### Post by hipocrita20 on 2010-05-25
> **philinux said:**
> sudo first 



Also see the General Help Sticky.


sorry! yes..sudo first
but you can install those packages with Synaptic too..if you prefer

---

