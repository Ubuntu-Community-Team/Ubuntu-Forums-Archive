---
title: "BCM43xx Ubuntu Gutsy"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by csall on 2008-03-08
Just to start off I'm not exactly a newb nor am I an expert, intermediate I guess you could say. I have installed my bcm4318 card numerous times without trouble, but am having a problem now..

I installed Ubuntu 7.10 (Gutsy) Server Edition 64 bit on laptop and installed xfce since it isn't as big of resource hog as gnome or kde.

I have tried installing the bcm43xx-fwcutter utility with no success:

[B]sudo aptitude install bcm43xx-fwcutter

sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh[/B]

My wireless does however show up when I use iwconfig command as eth1. However after I set up the network it always says **access point: Invalid** and I am unable to connect to my network. Also, if I run sudo iwlist scan it comes back with no search results.

Can someone please help me.. I have also tried using ndiswrapper with the 64bit driver for the bcm4318 and blacklisting bcm43xx in /etc/modprobe.d/blacklist with no success. PC doesn't even recognizethe wireless card. Please any help is appreciated. Thank you in adavnce!

---

