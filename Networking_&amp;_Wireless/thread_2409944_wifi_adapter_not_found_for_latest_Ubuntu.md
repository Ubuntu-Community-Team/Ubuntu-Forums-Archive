---
title: "wifi adapter not found for latest Ubuntu"
date: 2019-01-08
forum: Networking &amp; Wireless
---

### Post by kutay on 2019-01-08
So I set up ubuntu for the first time today and everything   seems to be in order however it says no wifi network connected. I have   this Ubuntu as a dual boot and my wifi works perfectly at Windows. 

I'm not really able to set up ethernet either to the linux so any online   solution would have to be somehow incorporated into a usb. I have  tried various techniques from other forums, but all to no avail. 

My driver is    Broadcom BCM43142 802.11 bgn Wi-Fi Adapter

Thank you for your time

---

### Post by coffeecat on 2019-01-09
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2019-01-09
I suspect that when we know the result of three terminal commands, we'll know the solution. Please run and post:```
sudo modprobe wl
rfkill list all
sudo dpkg -s bcmwl-kernel-source
```

---

### Post by kutay on 2019-01-09
Sorry for the late reply, I just woke up. 

```
  
kutay@kutay-550-077c:~$ sudo modprobe wl
[sudo] password for kutay: 
modprobe: FATAL: Module wl not found in directory /lib/modules/4.15.0-29-generic
kutay@kutay-550-077c:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
kutay@kutay-550-077c:~$ sudo dpkg -s bcmwl-kernel-source
dpkg-query: package 'bcmwl-kernel-source' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

---

### Post by chili555 on 2019-01-09
The correct driver for your device is bcmwl-kernel-source. It can, with some patience, be installed using the installation USB from which you installed Ubuntu. Please check here: [https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949](https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949) Note that my answer there refers to an SD card, but the process is the same with USB.

Post back if you get stuck or need additional guidance.

---

### Post by kutay on 2019-01-10
Works perfectly. Thanks!

---

### Post by chili555 on 2019-01-10
Awesome! Glad it's working. Have fun!

---

