---
title: "Help Wi-fi is not working"
date: 2016-03-17
forum: Networking &amp; Wireless
---

### Post by Austin_mink on 2016-03-17
Hello and i have just installed ubuntu 12.04 i think thats the one and my wi-fi adapter is being regestered but i cant use the wi-fi at all my adapter is a broadcom BCM4318 and i cant get it to work plz help me

---

### Post by Bucky Ball on 2016-03-18
*Thread moved to **Networking & Wireless**.*

Welcome. Please confirm which version you are using. Open a terminal and type:

> lsb_release -a

... or check in Disks. 

There is a wirelessinfo script linked in my signature at the bottom of this post. Please run it and post the output between code tags (there is also a link for how to create them below).

'Can't get it to work' is not really enough information for us to give much help. Please be more specific: what have you tried to get it to work; how is it not working (shows networks but can't connect?); and add any links to things you have tried.

---

### Post by Hadaka on 2016-03-18
Hi, from a working wired connection please open a terminal ctrl/alt/t then
copy and paste one line at a time. The first command may fail, that is ok
continue on with the rest...
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
boot, remove wired connection and test wireless
thanks.

---

### Post by Austin_mink on 2016-03-18
sorry i was wrong it was 13.10 and what i mean its not working that its not showing me any wireless options and when i do iwconfig i get : no wireless extensions for both lines it displays but it does regester the wifi card addapter

---

### Post by Hadaka on 2016-03-18
Hi, Ubuntu 13.10 is no longer supported end of life was July 17, 2014
I suggest you load atleast Ubuntu 14.04

good luck.

---

### Post by Austin_mink on 2016-03-18
im sorry but ubuntu 14.04 is not compataple with my pc its a old dell insperon 2200 and 13.10 was the latest version i could use and it used to work till i reinstalled my coustom os and did not like it so i reverted back and thats when i had the problem

---

### Post by Bucky Ball on 2016-03-18
Try a lighter flavour of 14.04 or 15.10 if Ubuntu won't work on that machine, Xubuntu or Lubuntu, or post a new thread to figure out why it won't work. You're stepping backward into a diminishing world of support by installing and using such an old version (and there are no updates/upgrades, including security ones, so anything we ask you to download to fix this you probably won't be able to).

13.10 was out of support half way through 2014. A year and a half without updates of  any kind. If you're using it I advise keeping the machine offline.

---

### Post by Hadaka on 2016-03-18
Hi, I am responding on a 2005 Dell Inspiron 1300,..40Gig internal hard drive and 1.5gig ram 
running Ubuntu 12.04 LTS ...see attachment. I also boot up to Ubuntu 14.04 LTS with a usb...see screen shot.
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318]..same as yours.
The only reason I am not running 14.04 LTS is simply because why should I ? My 12.04 LTS is still supported and
runs great,as does 14.04 LTS. If you were able to run 13.10 you should be able to run 12.04 and quite possibly 14.04.

[ATTACH=CONFIG]267867[/ATTACH][ATTACH=CONFIG]267868[/ATTACH]

The commands I posted for your broadcom card [14e4:4318] are valid for all ubuntu versions.
see here to verify -> [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by kurt18947 on 2016-03-18
I will echo what others have said - try a different 'flavor'. Lubuntu, Xubuntu & Ubuntu Mate are less demanding of hardware. I have Ubuntu-Mate 14.04 running on a machine that was born running WindowsME (!). Unity and Gnome require higher spec graphics systems.

---

