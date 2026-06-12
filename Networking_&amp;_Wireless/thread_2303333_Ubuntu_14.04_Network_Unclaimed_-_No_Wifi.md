---
title: "Ubuntu 14.04 Network Unclaimed - No Wifi"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by Fasial_Kanji on 2015-11-18
Hello 

I'm having trouble connecting to the internet. My computer does not have and Ethernet port and when i check the network connections icon on the taskbar, I get the "no network devices available" message. After reading multiple posts I noticed the "network unclaimed" message when running [COLOR=#000000][FONT=Ubuntu Mono]lspci, but im not sure how to reclaim it.

Thank You [/FONT][/COLOR]

---

### Post by ajgreeny on 2015-11-18
Let's see the output of ```
cat /etc/modules
``` as I suspect ath9k is not loaded and may need adding to the list that shows there.

---

### Post by Fasial_Kanji on 2015-11-18
Hi
This is the output: 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc

---

### Post by jeremy31 on 2015-11-18
See if wifi works after ```
sudo modprobe ath9k
```

---

### Post by Fasial_Kanji on 2015-11-18
I get the following error:
modprobe: FATAL: Module ath9k not found

---

### Post by jeremy31 on 2015-11-18
Reboot and press the SHIFT key during boot until the GRUB menu appears, select Advanced Options for Ubuntu and select a older kernel to boot to and see if the wireless works

---

### Post by ajgreeny on 2015-11-18
Strange!  That ath9k driver has been included in the 3.13 kernels since the beginning and should certainly be available with the 3.13.0-67 that you're running at present, so I am a bit bamboozled.

Which version of ubuntu are you using with which DE; unity, xfce, lxde?  I am not sure why that would make any difference, but I am just trying to get a full picture of what might be going on here.

---

### Post by Fasial_Kanji on 2015-11-18
Perfect, it's working now!!! Thank You for your help. Just one last follow up, does this mean i always need to boot through the GRUB menu or will it save the current settings?

---

### Post by jeremy31 on 2015-11-18
I think you might have a corrupt kernel somehow, hopefully the next time you update the system you will get the 3.13.0-68 kernel and won't have to use the grub menu

---

### Post by Fasial_Kanji on 2015-11-18
> **ajgreeny said:**
> Strange!  That ath9k driver has been included in the 3.13 kernels since the beginning and should certainly be available with the 3.13.0-67 that you're running at present, so I am a bit bamboozled.

Which version of ubuntu are you using with which DE; unity, xfce, lxde?  I am not sure why that would make any difference, but I am just trying to get a full picture of what might be going on here.

i'm using ubuntu unity version 14.04. I've previously had no problems with my wifi, but I did install TensorFlow earlier in the day and noticed the problem once I began training the sample net.

---

### Post by ajgreeny on 2015-11-18
I have no idea what TensorFlow is nor why it should affect your system's wifi, but I have been using 3.13.0-68 for a few days now, so you may need to run ```
sudo apt-get dist-upgrade
``` for that to be added on your system as well.

---

### Post by Fasial_Kanji on 2015-11-19
Yes, once i regained internet access I did an upgrade and everything seems to be back to normal. Thank you to everyone for your help.

---

