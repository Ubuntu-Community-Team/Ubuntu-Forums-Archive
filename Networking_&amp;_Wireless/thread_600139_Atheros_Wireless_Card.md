---
title: "Atheros Wireless Card"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by gerowen on 2007-11-01
I'm using a Toshiba Satellite laptop that came with Windows Vista Home Premium.  Always being a fan of Linux, but being out of the community for a little while, I decided to try out the latest Ubuntu since I just got this laptop.  It seems to run very well, with a few nice touches.  However I'm having the same old issue I've always had with Linux on laptops, my wireless card.  This new restricted drivers thingy seems to be detecting my wireless card and using a proprietary driver for it, however when I tried installing wifi radar it doesn't detect any networks around me and I know there are quite a few.  Also none of my network utilities seem to be detecting my wireless card.  Help please?

[http://i2.photobucket.com/albums/y45/dudeman41465/wirelesscard.png](http://i2.photobucket.com/albums/y45/dudeman41465/wirelesscard.png)

---

### Post by kevdog on 2007-11-01
Do you know if your atheros card is acutally supported using madwifi??  I would first check the madwifi site to confirm if someone has had success with your card since the madwifi drivers do not support all Atheros chipsets (ndiswrapper takes care of the rest)

---

### Post by gerowen on 2007-11-02
Alright, found out that [my card](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG) is supported, but I've never used this so I'm going to have to screw around with it and see what I can get going.

---

### Post by gerowen on 2007-11-02
Alright, according to the readme that came with madwifi after I've done a make and make install and modprobe ath_pci when I run iwconfig it should list two new wireless devices it created, one of them being a placeholder and the other loaded with the information about my actual card.  It didn't create the devices though.  I've never used madwifi before, can somebody help me out?

---

### Post by kevdog on 2007-11-02
Please post lshw -C network -- and FYI the restricted drivers within Synaptic that you can download are the madwifi drivers.  The only advantage of downloading and compiling from source is that you get a newer version (I did this since I wanted the newest features).  Some people dont want to go through the trouble.

---

