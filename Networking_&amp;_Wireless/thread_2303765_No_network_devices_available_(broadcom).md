---
title: "No network devices available (broadcom)"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by Riley84 on 2015-11-21
Hello everyone,

Yesterday I bought a:
 
Toshiba Satellite L50-B-1VU
64-bit
Intel pentium N3540

Ubuntu 14.04 LTS was installed on it.

I have no internet access, not from wireless nor ethernet. At the top-right of the screen there is an internet symbol thing which when I click on it says 'No network devices available'.

I have googled and found material on this subject and so-called solved documents (including those stickied on this forum), I have attempted to follow these steps but unsuccessfully. One of my problems is that I do not really know anything about computers so the steps often confuse me, especially when it comes to terminal stuff.

I have been to additional drivers and tried to apply changes when seeing the: 
Broadcom Corporation: BCM43142 802.11b/g/n
This device is not working
Using broadcom 802.11 Linux STA wireless driver source from bcmwl-kernal-source (propierty)
Do not use the device

Apply changes results in nothing; forever delayed.

I've also downloaded bcmwl_6.30.223.248 +bdcom.orig.tar.gz from another computer but I couldn't seem to do anything with it.

I've also tried things like the sudo apt get/install/update etc but I just get failures etc

lspci -nn -d 14e4 results in:
Broadcom Corporation: BCM43142 802.11b/g/n

I've also tried hitting my head against the wall but that didn't work either :)

If anyone suggests something, firstly please assume nothing about my computer knowledge and secondly thank you very much, I do appreciate your efforts.

Rob

---

