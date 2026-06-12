---
title: "Yet Another Broadcom Wireless Help Seeker"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by rizlmilk on 2008-04-03
Okay, I have gotten fed up with Windows and have decided to make every comnputer I own run Linux. Only problem I have is my laptop. It's an HP Pavilion ze4900. I have tried literally every tutorial posted in the past two years on these forums, and not a single one has worked for me. I once got the wireless light on and I could detect wireless networks, but couldn't connect to them. Once I restarted the machine it wouldn't even detect the networks anymore. I am on Gutsy right now.

Running "lspci | grep Broadcom" produces this: 

"02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)"

Any help is greatly appreciated.

---

### Post by pseudo-random on 2008-04-03
Look into airodump and wpa_supplicant. Even if you don't get things up straight away, those programs will put you on the right path to becoming a wifi guru.

---

### Post by rizlmilk on 2008-04-03
I enabled the firmware for my wireless card under Restricted Drivers. The blue light now comes on again, but there are no networks detected. So the wireless card essentially doesn't work past the blue light. Does anyone know what is needed now in order to detect wireless networks?

Again, thanks in advance.

---

### Post by kamasabi on 2008-04-03
have you tried restarting the network service?

sudo /etc/init.d/networking restart

Also, there should be an installer for that chip, I have the same one.  Lemme see if I can find it....I'm currently using the 8.04 beta, and enabling it from the restricted drivers manager fixed my problem.

---

### Post by kevdog on 2008-04-03
You should have no problem connecting with that card.  I have the same chipset exactly and have used both the restricted drivers as well as ndiswrapper along with the bcmwl5 window's XP drivers.  My card is a Linksys WPC54GS.

---

