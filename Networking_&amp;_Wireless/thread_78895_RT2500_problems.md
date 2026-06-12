---
title: "RT2500 problems"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by macoute on 2005-10-19
I have some serious problems with a-link wireless card. The card itself is blank, with only mac-address, serialnumber and something else printed on it, but it says nothing about the model. After browsing the Web, I came to conclusion that it is a RT2500-series card.

I followed the instructions in rt2500-howto, but my card doesn't show up in System | Networking as it is supposed to. Lspci doesn't find anything concerning that card. The card is a PCMCIA-card.

lsmod | grep rt2500 says that there is a module installed. But I'm quite near to a newbie, so I don't understand anything about the numbers or anything. The lights in the card do not blink as they are suppposed to do.

I also noticed that in repositories there are something about rt2500, but it is 
possible to make it work that way?

What to try next? Please ask for extra info, I just didn't know what to paste.

Using Breezy in a Fujitsu Amilo A1640-laptop.

---

### Post by gdcondor on 2005-10-19
try to install "module-assistant" and then run it : you'll be able to download the driver compile it and install the module only by browsing through the menus ! i think it supports RT2500 but i tried this method with RT2400 and it was really useful

---

### Post by stevenyu on 2005-10-19
I got a new Asus Motherboard A8V-E which came with an Marvell Chipset (Which I believe is one of the RT2500 or 2400), have anyone in the forum got it working? As far as I know, ndiswrapper + wifi driver from the ASUS will just hang the system when trying to link with the wifi AP.

Does Breezy Badger already have the sourceforge RT2500 driver build in the kernel, or I have to compile my self?

Breezy Badger didn't pick up the onboard wifi device, I have a feeling it might be some other chipset, however <b>lspci</b> is not really given me any information

---

### Post by MeijUbuntu on 2005-10-20
Hello, i have the same problems.

First of all --> I am a newbie at compliling and installing.

I have installed a fresh Breezy on my Desktop. It detected my rt2500 (ra0) device, but did not activated it yet. I can activate it.

But i wan't to install and use WPA. I have read lot's of howto, but all of them failed.

Is there someone out there who has a RT2500 wireless device which it's working with WPA ? And if so, please make a howto from a fresh breezy install so we can all benefit from it.

Thnx

---

