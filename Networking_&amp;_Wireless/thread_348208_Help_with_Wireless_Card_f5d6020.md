---
title: "Help with Wireless Card f5d6020"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by shantanut on 2007-01-28
I have installed ndiswrapper succesfully, but can not find the drivers in a zip format for this card.  I also can't find the realtek 8180 driver as several people gave instruction to combine the two drivers.

I installed wifi radar, and it actually does show the correct wireless networks that are available, however I can't connect to them, or double click on them or anything.  I think this means the card is on and detecting, I just can't use it.

Please help!
Thanks,
Shan

---

### Post by Metaljaz on 2007-01-28
If there were native drivers installed when you installed the OS you may have to blacklist
or remove them.
Here is a website that has the realtek 8180 drivers.

[http://www.opendrivers.com/categorycompany/1113/1358/network-realtek-free-driver-download.html](http://www.opendrivers.com/categorycompany/1113/1358/network-realtek-free-driver-download.html)

---

### Post by shantanut on 2007-01-30
I download the 8180 drive, and just tried installing that using the ndiswrapper windows driver utility, but when i chose the .inf file and tried installing it, nothing happened.  It did not add to the list of drivers.  I installed the atmel firmware package, and I can see the wireless networks and how strong of a signal they have on wifi radar, i just can not connect to them.

my friend told me simplymepis is built off of ubuntu and might have support for my card, should i try that?

---

### Post by tturrisi on 2007-01-30
> **shantanut said:**
> I download the 8180 drive, and just tried installing that using the ndiswrapper windows driver utility, but when i chose the .inf file and tried installing it, nothing happened.  It did not add to the list of drivers.  I installed the atmel firmware package, and I can see the wireless networks and how strong of a signal they have on wifi radar, i just can not connect to them.

my friend told me simplymepis is built off of ubuntu and might have support for my card, should i try that?
Something's awry here.
The 8180 drivers are for devices with a Realtek chipset and Atmel is for devices with an Atmel chipset.  What brand and model # card do you actually have?

---

