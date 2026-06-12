---
title: "Can't activate bcm4312"
date: 2018-09-07
forum: Networking &amp; Wireless
---

### Post by setayo on 2018-09-07
Been trying to connect to wifi however hit many roadblocks, I've installed driver packages such as b43, b43-fwcutter, bzip2, wget, net-tools and libc-dev 
I am using Kubuntu 18.04 i386
The only way I've been able to install packages is via the website on my phone and then transfer via usb, any help would be greatly appreciated!
Chipset BCM4312 PHCID (think thats the right way round) [14e4:4315]

UPDATE: Thanks to westie457 and paseodym for the solve...
Download: [https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)
Type in console:
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
Then reboot
Type into console:
sudo apt remove --purge bcmwl-kernel-source
sudo modprobe -rfv wl
sudo apt install firmware-b43-installer
sudo modprobe -rfv b43
sudo modprobe b43

OPTIONAL to make wireless run automatically on startup:
(if you dont have gedit) Type in console: sudo apt-get install gedit
Type in console: sudo gedit /etc/modprobe.d/blacklist.conf
Find 'bcm43' near bottom and put '#' infront
save file and you're done

---

### Post by westie457 on 2018-09-07
Have you seen this one place for about 98% of all broadcom wireless chips. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by chili555 on 2018-09-07
Post #15 here shows how to download one file and install the required firmware. [https://ubuntuforums.org/showthread.php?t=2361632&highlight=b43.zip](https://ubuntuforums.org/showthread.php?t=2361632&highlight=b43.zip)

---

### Post by setayo on 2018-09-07
Westie457 - going through this tutorial is difficult because ive just found out i cannot connect via wired ethernet either.. when i look into it, it turns out the default wired ethernet setting is routed via my wireless card id (enp2s0) its almost like its been setup as a virtual machine to run wireless through a wired link to the wireless card.. :/

EDIT: ignore the bit about wired going through network card ^^^ im a plum and misread the script shown in konsole :3 it clearly says enp2s0 is my ethernet port and doesnt give a logical name for network card

Chili555 - im sorry but going through that post didnt get me anywhere :(

---

### Post by chili555 on 2018-09-07
Did you download the b43.zip package on your phone and transfer it? What did you try next? Where did iit go wrong?

---

### Post by westie457 on 2018-09-07
Ignore any 'file not found' errors and any 'package not installed' errors.
With the cable connected open a terminal copy and paste one at a time the following commands remembering to hit enter for each one.```
sudo apt remove --purge bcmwl-kernel-source
sudo modprobe -rfv wl
sudo apt install firmware-b43-installer
sudo modprobe -rfv b43
sudo modprobe b43
```
If wireless has not come to life after 30 seconds, remove the cable and reboot.

---

### Post by chili555 on 2018-09-07
I believe it is firmware-b43-installer. I also believe that the OP doesn't have an internet connection available.

---

### Post by jeremy31 on 2018-09-07
Take a try at [https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978)

---

### Post by westie457 on 2018-09-07
Thanks for the correction chili555, post has been edited accordingly.

---

### Post by praseodym on 2018-09-08
Download this file somehow and save it in your "Downloads" folder

[https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Installation
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by setayo on 2018-09-08
thanks everyone, sorry I've been off a while, I'll go through all these methodically and I'll update this with screenshots as to how this goes so long as I'm not pulled away or distracted by shiny objects :D

EDIT: tried praseodym's tar.gz file and it has at least stopped it throwing red flags about the wireless cards lack of firmware, however I'm not able to connect to any wifi haven't tried wired yet, I've set up a wifi connection through the system settings it just won't connect, the screenshot of the batch install fail I'm not to sure what triggered it but took a screenshot anyway

EDIT2: after doing this and following instructions from westie357 I am able to connect to wifi thanks to everyone I'm so glad to get it sorted lots of love to all! :D <3

---

### Post by westie457 on 2018-09-09
Glad it is working and thanks for marking this thread 'solved'.

---

