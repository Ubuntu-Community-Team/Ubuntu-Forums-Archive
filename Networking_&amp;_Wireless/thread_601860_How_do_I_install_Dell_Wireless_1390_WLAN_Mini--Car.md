---
title: "How do I install Dell Wireless 1390 WLAN Mini--Card?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Xora on 2007-11-03
Ok go easy on me, I know there are other topics similar to this one but I get lost in them. 
Ok here is my system specs--

I have a dual boot of Linux Gusty Gibbon and Windows XP.
My hard drive is partinioned so that each operating system has 35 gigs.

My Network adapters are --
1394 Net Adapter
Broadcom 440x 10/100 Intergrated Controller
Dell Wireless 1390 WLAN Mini-Card

Processor --
Intel Core Duo CPU T2350 @ 1.86GHz

My Video Card --
NVIDIA GeForce Go 7300

And I have --
2.0 G Ram

Any thing else you need to know just ask :)
So heres the thing I would really appreciate it if you would go slow and explain things. I would really like to understand whats going on. I love linux and I'm going to try to understand as much as I possibly can.

Which reminds me any suggestions of what I should read or any online companions so I can understand Linux just let me know. 


All is appreciated,
Antonio

---

### Post by kevdog on 2007-11-03
Read this post for the basics:
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

Then since you have a broadcom card, follow the post written by jamie jackson listed at the bottom of the thread to install drivers for your broadcom card (ndiswrapper/winxp drivers)

---

### Post by Xora on 2007-11-03
Ok, thank you. I will let you know how I do with it. I really do appreciate the help.

---

### Post by Xora on 2007-11-03
Im lost in it I get to
Next create and place your Window's wireless driver into ~/driver:
Code:
cd ~
mkdir driver
cd driver
Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
Code:
sudo ndiswrapper -i *****.inf




And well I just dont know

---

### Post by lathanial on 2007-11-13
Hi Xora,
I just followed the HowTo below on my Dell laptop. I works very well as I had to use it when
I installed 7.04 and after installing 7.10. You should read through all of if first. You will probably need the install CD. If you do, when the HowTO tells you to reboot remember to remove the CD. Many thanks to paperdiesel!!!

[http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+wlan](http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+wlan)

lathanial

---

