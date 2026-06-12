---
title: "Broadcom 4318 + AMD64 Edgy issues"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by philipt on 2006-11-06
I have a HP Pavilion dv8000 and running Ubuntu Edgy (AMD 64 bit version). I downloaded the 64 bit Broadcom drivers for Windows and extracted them with fwcutter, copied the files to /lib/firmware. So far so good, now the card is detected and it works (bairly), BUT it drops a lot of packages and after a while it stops working and I have to start/stop the card and do some iwlist scan and other magic to bring it up again...

I've also tried the ndiswrapper. The version that came with Ubuntu din't work at all (init errors in the log). I downloaded and tried the latest stable version 2.18. The card is detected in this version and I can find the access point with iwlist scan. But the access point is always Not Assigned and I can't set any of the parameters with iwconfig (like essid, ap, rate), it results in error something like can't set bit...).

I've read numerous tutorials but can't get anything to work. I'm pretty sure this is 64 bit related.

---

### Post by TusharG on 2006-11-07
Follow my tutor posted at:

[http://tusharg.blogspot.com/](http://tusharg.blogspot.com/)

I hope it will work... once you follow the tutor... let me know if you face any issues.

---

### Post by philipt on 2006-11-08
Do you use the 32 bit version of Ubuntu or do you use the AMD 64 version? 

Also, do you use the 32 bit version of the Broadcom drivers or the 64 bit version?

---

### Post by scalofrio on 2006-11-08
I can't set up my broadcom card neither: Broadcom Corporation BCM4306
Help please!!!

Ubuntu 6.10 **amd64**
Broadcom Corporation **BCM4306**

---

### Post by philipt on 2006-11-09
I've talked to the developers in the #bcm-dev channel and they suggested I upgraded the kernel. I upgraded to 2.6.18.2, but the problem still remains...Any help would be appreciated. I have read numerous docs and howtos but the problem still remains.](*,)

---

### Post by aw24 on 2006-11-09
I'm having similar issues with the Broadcom 4318 on my HP/Compaq V2000Z.  I tried installing the 64 bit driver using the fw-cutter tool and it recognized the card and it could find the wireless network briefly.  Then it stopped working, and my wired ethernet quit working too, mouse movement became choppy, and when rebooting it would hang at boot.  I've reinstalled edgy multiple times now.

I've tried all sorts of variations using ndiswrapper and I have yet to even have my wireless interface appear.

Has anyone managed to get the broadcom 4318 working with Edgy x86-64?  If so please help.  It has been a nightmare getting this card to work.

Thanks

---

### Post by ckonrad on 2006-11-09
try out this solution [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102), most people including myself have had success with it, i dont use 64bit but there is some mention of that in the troubleshooting section.

---

### Post by aw24 on 2006-11-10
> **ckonrad said:**
> try out this solution [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102), most people including myself have had success with it, i dont use 64bit but there is some mention of that in the troubleshooting section.

I did try that method on a clean Edgy install.  The install script recommended downloading kernel 2.6.18.1 since kernel 2.6.17-10-generic apparently does not work with this card in AMD64.  However, I had no more luck with 2.6.18.1.

---

### Post by joseth on 2006-11-16
Just got it working on edgy amd64 with bcm4318 (hp dv5020). How did i do this ?? tried many howtos and tips, but only worked after downloading ndiswrapper source and compiling it: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

  Have fun !

---

### Post by philipt on 2006-11-20
What version of Ndiswrapper?

---

### Post by trubblemaker on 2006-11-20
latest source is ndiswrapper 1.28 if you want a quick howto form source check my signature for "ndis from source", it does assume you already have the drivers, lots of howto's will show you how to grab them.  If you dual boot let windows tell you the exaxt file.

---

