---
title: "HP Pavilion dv2313cl Laptop Wireless"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by fjgaude on 2007-05-24
Has anyone successfully installed Feisty on subject laptop and has the wireless working, Broadcom bcm4311 chip?

Thanks for any help.

frank

---

### Post by poision_heart on 2007-05-24
hey i installed feisty on same config comapq laptop with dual boot option but it wireless not detected..n having many dependecy errors in installing other software from internet

---

### Post by fjgaude on 2007-05-24
> **poision_heart said:**
> hey i installed feisty on same config comapq laptop with dual boot option but it wireless not detected..n having many dependecy errors in installing other software from internet
I'm not having any dependency problems, but I think the Network Manager has problem with WEP versus roaming... I can see Access Points but don't connect, can't connect, because I think the NM changes the access as I try to connect.

Don't know what to do about it.

frank

---

### Post by brn on 2007-05-24
I have exactly the same problem.  Compaq Presario with the Broadcom 4311 chipset.  I have been buried in the forums for more than a month trying all the methods (ndiswrapper, fwcutter, etc.) to no avail.  Somewhere I came across a post suggesting that there are certain Broadcom devices, 4311 among them, from which no one has yet been able to extract the firmware.  My machine came with Vista pre-installed and I suspect that the combination of this particular chip along with Vista's very different innards make it an exceptional challenge.  Right now I'm trying to find an affordable wireless miniPCI that works with Linux, forgetting about Vista for which I have no particular use anyway.  Very frustrating.

---

### Post by Niomi on 2007-06-19
Have you gotten your wireless driver working yet? I bought a HP Pavilion dv2313cl yesterday and got the wireless connection working today. The wireless card is a Broadcom 1390 which is also used in some dell laptops. The guide to installing this with ndiswrapper was written for dells, but it worked for me:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

I tried using ndiswrapper with HP drivers and that was a miserable failure.
For the convenience of searchers, I'll also post this in your other thread for these drivers.

---

