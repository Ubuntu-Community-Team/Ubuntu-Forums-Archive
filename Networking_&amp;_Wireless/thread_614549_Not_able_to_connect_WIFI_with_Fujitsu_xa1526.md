---
title: "Not able to connect WIFI with Fujitsu xa1526"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by TaaviT on 2007-11-16
Hi! I want to go fully on Ubuntu, but i'm not able to pull away from WINDOWS, when the wireless is not working :mad: 
I've got 2 wireless cards (on is the integrated, but i don't want to use it because it has very low transmitter. Although I don't want to use it in the future, i'm not able to get it to work with Ubuntu 7.10 anyway. It's a SIS 163.
The other device is connected to the USB port. BUFFALO WLI-U2-KG125S. I've searched the forum, tried everything, but it won't work :confused:

I don't know if the FUJITSU computers have any support for Linux? Everything goes around MS? The sound is also making problems. Sound comes out only from the front jack. The speakers are not working. The front panel volume control is also not working. 
The sound output depends on the status when installing. For example, I installed Ubuntu while the headphones where connected to the jack, then only the phones worked. In the second time I unplugged the phones. Then the sound came from the speakers, but not as good as it should be (I'm having a woofer above my laptop, and this didn't work)
I tried to use the latest alsa drivers, but no progress...:popcorn:

Waiting for any response, Taavi

---

### Post by _Stevie_ on 2007-12-22
same here, i cant get it working. i installed ndiswrapper and the device is recognized and everything.
i can even see all the wifis around me, but when it comes to connecting it doesnt work at all.

---

### Post by murmel on 2007-12-22
Doesn't restricted drivers support it?
(Maybe) you could connect your computer to the lan with a cable and try to install it with the Restricted Drivers Manager?

---

### Post by _Stevie_ on 2007-12-22
afaik there is no sis163u linux driver :(

EDIT: i fixed it, i needed to install wicd instead of gnome network manager, since
im using a static ip.

---

### Post by TaaviT on 2008-04-27
I'm still in the trouble. Even tried to change the WiFi adapter to Atheros (taken from Asus Eee PC) and still no luck.
Now I'm back on the SIS163. Graphical ndiswrapper says that hardware is present and all systems up, but nothing, under Network manager there is no wireless available.:(

---

