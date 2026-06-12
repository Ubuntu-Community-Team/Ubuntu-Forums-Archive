---
title: "wireless for ubuntu on macbook"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2008-04-25
hi there,
I have a macbook and i have ubunu on it as well as mac OSX. The problem is that the wireless card is being detected during boot up i.e i can see it listed when i do lspci. However when i go to the gui for the network set up the wireless connection is not listed.I guess this means that the driver is not being loaded due to it not being present at all.
My wireless card is (listing from lspci):Atherons(might be atherlos) communuations AR5418. Does anyone know the right driver for this card and also how to install it and get the wireless configured correctly and up and running.Thankx in advance

---

### Post by dstew on 2008-04-25
Look in System --> Administration --> Restricted Drivers Manager and see if there is a driver or HAL for that card. If so, enable it.

---

