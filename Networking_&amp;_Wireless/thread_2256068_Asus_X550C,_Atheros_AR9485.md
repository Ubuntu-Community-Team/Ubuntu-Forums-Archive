---
title: "Asus X550C, Atheros AR9485"
date: 2014-12-09
forum: Networking &amp; Wireless
---

### Post by Andrei_Radu on 2014-12-09
Hello. I have recently installed Ubuntu 14.04(dual-boot with Win 8) on my Asus X550C. The Wifi does not work. The card is Qualcomm Atheros AR9485. I have read from the forums that I have to install something but for that I need access to the internet through an ethernet cable. I only have access to WiFi but no cables. I tried looking for a driver to copy onto a stick and then apply it in Ubuntu but can't find any. Also in the top bar, right side where the network sign is the option to ''Enable WiFi'' is disabled (can't click on it).  What options do I have of installing the drivers for my network card without any access to the internet (only in windows). Thanks. Sorry if I have not been very clear with the question. I'm new to this.

---

### Post by jeremy31 on 2014-12-09
Sounds like you have a hard block on your wifi, in terminal enter ```
rfkill list
``` to see
If you also have kernel driver asus_nb_wmi```
lsmod | grep asus_nb_wmi
``` there is a fix ```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```
Reboot and see if the FN+ combo will enable the wifi

---

### Post by Andrei_Radu on 2014-12-10
Hi jeremy31. It worked. Thank you so much. I've been searching the forums for a while now.

---

