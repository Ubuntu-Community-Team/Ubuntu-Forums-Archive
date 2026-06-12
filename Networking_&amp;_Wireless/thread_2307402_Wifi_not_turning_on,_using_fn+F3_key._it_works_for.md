---
title: "Wifi not turning on, using fn+F3 key. it works for bluetooth."
date: 2015-12-24
forum: Networking &amp; Wireless
---

### Post by Raj_Nayan on 2015-12-24
tried following:

nvn@nvn-Aspire-5755:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
nvn@nvn-Aspire-5755:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for nvn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
nvn@nvn-Aspire-5755:~$ sudo modprobe wl
modprobe: FATAL: Module wl not found.

what should i do now ?

---

### Post by jeremy31 on 2015-12-24
Do you have internet access with Ubuntu?

---

### Post by Vladlenin5000 on 2015-12-24
> **jeremy31 said:**
> Do you have internet access with Ubuntu?

Most likely not because... > Wifi not turning on (...)

Please use an alternative temporary internet connection (ethernet cable, etc.) in order to perform actions that require internet.

---

### Post by Hadaka on 2015-12-24
Hi, How to load Broadcom-kernel-source with no internet

1. Insert the dvd or usb you used to to load Ubuntu
2. Click the dvd/usb icon to view the files
3. Click **pool** > **restricted** > **b** > **bcmwl** then
4. Drag and drop the **bcmwl** icon to your Desktop
5. Click the dvd/usb icon to view the files again
6. Click **pool** > **main** > **d** > **dkms** then
7. Drag and drop the **dkms** icon to your Desktop

****bcmwl** icon and **dkms** icon should now be on your Desktop.
Open a terminal ctrl/alt/t then COPY and paste one line at a time
```
cd Desktop 
sudo dpkg -i dkms*.deb 
sudo dpkg -i bcmwl*.deb 
sudo modprobe wl
```
boot

---

### Post by jeremy31 on 2015-12-24
I don't know if things have changed lately but after trying an ISO of ubuntu 14.04.2 I found that the version of bcmwl-kernel-source was the wrong version for the kernel.  I do believe that Vladlenin5000 has a prefered version of bcmwl

---

