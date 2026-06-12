---
title: "OvisLink - CardBus PC Card troubles on Xubuntu"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by kainen on 2007-04-14
So I have decided to make the leap into using Linux by playing around with it on my old laptop. Since it is rather old I went with Xubuntu (6.10 Edgy Eft) and so far it looks and feels great. The only problem I have now is getting my wireless internet to work. I have a WPC32 - 802.11b Wireless 32bit CardBus PC Card made by OvisLink. I searched around a few threads and topics to see what could be done and eventually found my way here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

Hoping that was all there was too it I downloaded the proper driver, and installed it with ndiswrapper as the directions told me too. Everything worked except one command near the end:

> gksudo gedit /etc/modules

It told me it couldn't identify the command 'gedit' but otherwise everything worked. After everything was done the Act light started blinking, however the green Link light did not, and I have been unable to access the internet on my laptop yet. I obviously did something, just not enough and was wondering what I missed.

Please keep in mind I have never used Linux before in my life and this is all a learning experience for me. Any help would be greatly appreciated.

---

### Post by Brendantb on 2007-04-14
Hi, 

I'm not familiar with ndiswrapper: I took the easy way out and bought a pc card that is well supported out of the box. However, looking at your code, I think that gedit is a text editor found only in the Ubuntu distro. The equivalent in Xubuntu is "nano." That guide is written for Ubuntu, so you have to adapt it a bit for Xubuntu.

---

### Post by kainen on 2007-04-14
Ah, thank you. I knew it was a Ubuntu guide, but I figured it would be similar enough for me to use. Good to know the equivalent command in Xubuntu. I'll try it out and see what happens.

---

### Post by kainen on 2007-04-14
No good, I still can't figure it out. Hopefully it's something simple and I don't need to purchase a new card.

---

