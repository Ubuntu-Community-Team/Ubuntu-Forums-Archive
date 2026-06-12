---
title: "[SOLVED] Does this mean it should be easy? (Feisty and Linksys WMP54G)"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by leialte on 2007-07-05
I'm not very computer literate, and not linux literate at all, so please bear with me.

I just installed Feisty (7.04) and I have been trying to get my internet to work on my home computer (at work right now). My card (Linksys WMP54G vers. 4) is supposed to be able to work out of the box, and I think it does -- I go to Administrative --> Networking Tools, and it shows up as ra0, and the list of transmitting/receiving numbers are active. I click on configuration, and it's showing my wireless network and gives me a percentage number. Does this mean I just can't remember the wep code correct, or could there be another problem?

---

### Post by lisati on 2007-07-05
From what you have told us, it sounds liketo something potentially useful happening. Have you been able to connect to the internet through your card yet?

---

### Post by ubanchaos on 2007-07-05
well im having the same problem i aslo have a linksys wirless pci adapter(wmp54g) do i need some type of driver

---

### Post by bikeboy on 2007-07-05
> **leialte said:**
> I just installed Feisty (7.04) and I have been trying to get my internet to work on my home computer (at work right now). My card (Linksys WMP54G vers. 4) is supposed to be able to work out of the box,

There is a bit of an issue with Feisty and the chipset your card uses, that makes configuration a bit more tricky. Up on the top right of your screen there should be a network icon, from there you can select manual configuration to disable the system that doesn't work with your card. Hopefully that will fix it, but if not have a read of [this thread](http://ubuntuforums.org/showthread.php?t=465722) or my copy and paste [guide](http://www.vickersf.dyndns.org:8080/blog/2007/07/03/howto-ralink-ubuntu-feisty/)

Hope you get it working. Alas, it's a bit hackish now, but come October it should be really simple out of the box, including WPA and easy switching between wired and wireless networks.

---

### Post by leialte on 2007-07-06
lisati - if you mean connecting through the card, I used to have it operating on windows, but I've yet to get it to work in linux.

bikeboy -- wow, I can understand your tutorial!  Kudos to you! I haven't tried it yet. I'm going to mess with a few more settings, and manually configuring like you mentioned, before I do that. I'll keep you posted (and celebrate with a post on linux when it works!)

---

### Post by leialte on 2007-07-06
Aaaaaand it works! The cause of my problem: I was putting my WEP key in ascii instead of hexadecimal *blush*. That was actually the settings I mentioned messing around with before trying something more difficult. SO! For those wondering, yes it really does work out of the box. You just have to be not-stupid. haha XD Oh, and I was remembering the WEP key wrong too.

It&#347; official:
[IMG]http://i207.photobucket.com/albums/bb105/leialte/Screenshot.png[/IMG]


Now... where do I find an FTP program? ^^

---

### Post by kevdog on 2007-07-06
Sorry to burst your guys bubble but I believe this card is a ra chipset with the rt2500 driver.  Although there is an older driver for this card built-into the system, I believe from the posts of others, feisty requires that the newer seriallmonkey rt2500 driver be downloaded, compiled, and installed in-leiu of the older driver.  Also network manager is not compatible with the ra drivers, so either a manual configuration is needed in the /etc/network/interfaces file, or the GUI version rutilt also needs to be compiled, and installed (its in the serialmonkey download).

So to answer your question -- no its not going to be easy.  If you have never compiled anything before its going to be hard.  If you have the whole process or downloading ,compiling, installing might take 10 minutes.

---

### Post by DO55 on 2007-07-09
my network use WPA not WEB 
i cant connect tom my network because i cant find wpa in the network manager  list  , only i can see WEB

---

### Post by elementskaterbla on 2007-07-10
THIS IS THE SOLUTION!!! YOU DO NOT NEED TO USE NDISWRAPPER!!! update your 7.04 all the way, blacklist the bcm43xxx, take your ethernet off roaming mode and set it to dchp, then make sure that ethernet is UNCHECKED in network manager, take the wireless card off of roaming and set in your essid and such, then make sure it is checked in the network manager, then uncheck it, wait ten seconds and recheck it, reboot your pc and WALAH!

---

### Post by DO55 on 2007-07-11
elementskaterbla


how can i blacklist the bcm43xxx ?

---

### Post by bikeboy on 2007-07-11
That only applies when talking about cards with the Broadcom 43xx chipset, this thread applies to the WMP54G Rev 4, using an rt2500 chipset. The solutions are different, as noted, the issue described here was solved.

---

