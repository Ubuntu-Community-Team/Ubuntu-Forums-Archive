---
title: "prism v ndiswrapper"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by pakku on 2007-09-04
On XP I stuck a usb adapter in, it said, new device recognized, then churned a bit while it found drivers from somewhere and then it actually started to work!  Does this not happen in Ubuntu?

I have read a lot of stuff about prism and ndiswrapper and not fully able to understand what is difference.  is prism the native drivers for wireless adapter in linux?
does prism make drivers for all the various cards?  who is intersil?

i understand that ndiswrapper uses xp drivers, so ndiswrapper is not a driver in its own right.

 so is the sequence that I try prism first (using wlan-ng driver) and then if my device is not listed in the prism database I go for ndiswrapper?

 I have the directions for wlan-ng, which indicates that these are not installed by default.

In fact it says this 
'The Prism2 chipset was one of the first wireless devices to work in linux. Unfortunately, that means that it never became part of the wireless tools infrastructure that was being developed at the same time and does not work in the same way as all the other wireless cards. It cannot be configured like other wireless devices and must be done "by hand".'

I don't understand this- what is the wireless tools infrastructure?  how are other wireless devices configured?  Does Ubuntu recognize any kind of wireless device automatically?

---

### Post by kevdog on 2007-09-04
Prisms are difficult chipsets.  To the best of my knowledge the easiest way to get them working are using the ndiswrapper/windows drivers.  Some have used the prism54.org drivers, however I think they are still "experimental".

---

### Post by pakku on 2007-09-05
OK- so you are saying Prism is the chip, ie the semi conductor.
Tx

---

### Post by kevdog on 2007-09-05
Its the logic inside the microchip.

---

### Post by pakku on 2007-09-05
> **kevdog said:**
> Its the logic inside the microchip.
Yes, I had an interesting morning rooting about and finding information on what a chipset is and how Intersil sold the prism chipset to Conexant.
Looks like many different manufacturers (D-Link, Acer etc) have used the prism chipset inside their adapters and presumably are continuing to do so.  The old one was Prism2 which was for 11b devices and the wlan-ng is the driver for these.

Looks like Conexant continues to make prism chipset, the latest is the Conexant PRISM GT™ chipset.  And some group called [www.prism54.org](www.prism54.org) make linux drivers for these devices as well.

---

### Post by kevdog on 2007-09-05
From my understanding the prism54 drivers are still considered "experimental" and require a lot of different compiling steps.  I enjoy compiling from scratch, but the more I read about the process, the more pain in the A$$ it seemed.  Plus it didnt seem there was any guarantee of WPA working in the end result.  

Based on this I usually recommend ndiswrapper/win xp drivers.  Im still uncertain however if this solution supports WPA, however its a lot easier to get going and working.  

If you know anything more Id be glad if you would share the information.  It would be welcome knowledge to me and the community as a whole, particularly if you are able to compile and get the drivers working with reproducible steps.

---

