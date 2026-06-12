---
title: "wireless card, graphics driver (wl)"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by imerkat on 2008-07-10
I have a Broadcom corporation BCM4310 wireless network card in my dell inspiron 1526 (laptop). My computer have Ubuntu hardy 8.04, when I do the update I reboot my laptop, when the laptop start up, I saw that I don't have wireless conection and my ati accelerated graphics driver is in use but the other driver wl not in use, excuse me for my bad English, I'm beginner, for that I want detail answers. thankshttp://ubuntuforums.org/images/smilies/icon_sad.gif

---

### Post by jrasmussen0 on 2008-07-10
It sounds like your graphics card is working, maybe you want to make sure the 3D component is working.

For the wireless, right-click the Wireless Manager in the upper right corner and choose "Edit Wireless Connections"  My icon is really close to the sound icon.

---

### Post by imerkat on 2008-07-10
No my laptop say that I don't have wireless card, that mean that I cant edit wireless connection, thanks

---

### Post by sejoLesqui on 2008-07-10
> **imerkat said:**
> No my laptop say that I don't have wireless card, that mean that I cant edit wireless connection, thanks

Simply update your Ubuntu distribution using a wired connection.
There are some updates that will fix your problem. 

Regards

---

### Post by imerkat on 2008-07-10
yes, I'm using a wired connection but where I can find that updates to fix the problem of my wireless card?

---

### Post by imerkat on 2008-07-10
thanks for the help I don't know how that fix but now is working , thanks sejoLesqui and thanks jrasmussen0.

---

### Post by smalldog on 2008-07-18
I had purchased a dell computer one week ago. It is bundled with a broadcom BCM4310 mini-pci wireless card. It works perfectly under the Vista with both non-encrypted and encrypted condition. 

I install the Ubuntu 8.04 to the laptop computer. The wireless card only work  under non-encrypted condition. It shows the hardware driver wl is "In use". However, I have no way to enable the wireless card working under encrypted condition. I have tried using ndiswrapper instead of wl, but its also only working under non-encrypted condition.  

Does anyone success using the encrypted wireless communication under Ubunut 8.04 with BCM4310. Thanks a lot

---

### Post by corwinspyre on 2008-07-19
I believe the default networking tool doesn't have support for encryption. You should install wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

