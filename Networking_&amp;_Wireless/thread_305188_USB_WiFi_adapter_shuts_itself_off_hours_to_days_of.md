---
title: "USB WiFi adapter shuts itself off hours to days of working flawlessly"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by johnnabn on 2006-11-22
I was able to configure my usb wifi adapter without much problem, using ndiswrapper and the dellnic driver I downloaded from Dell's website.  It works as it should most of the time.  However, the device shuts off between several hours and a day or so.  The light goes out, and all network activity is lost.  When I try to remove the ndiswrapper module, rmmod refuses, claiming it is use.  I don't see anything relevant in the logs, but I don't honestly know where or what to look for.  Rebooting the computer solves all problems.

I also know that the devices works fine, without any spontaneous shut offs, in Windows.

I would appreciate any help on the matter.

Thanks

---

### Post by wieman01 on 2006-11-22
What router & wireless device have you got?

---

### Post by johnnabn on 2006-11-22
the router is a motorola WR850G and the wireless card is a Dell Wireless 1450 usb dual band.

---

### Post by wieman01 on 2006-11-22
I had the same problem a while ago (Linksys - ndiswrapper) and I have read many other posts complaining about the same thing with regard to "ndiswrapper". The solutions are manifold... Apparently this is a bug, your card disconnect & won't reconnect until you reboot.

My remedy was to reduce the default "beacon interval" (router setting) from 100 to something below 20. Others had to disable mixed mode (wireless B & G) in their router. I guess that you will have to mess around with your wireless settings a bit & test your system. I don't think there is a off-the-shelf solution out there.

---

### Post by johnnabn on 2006-11-22
The router was already broadcasting in G only, and i justed dropped the beacon rate from 100 to 15.  Are there any side-effects of this?  I'll update on how the wifi card fares.

Thanks for the help.

---

### Post by wieman01 on 2006-11-22
It's fine to reduce the "beacon interval", however, this is a mere workaround, no real solution to your problem. This merely does away with the symptoms (network disruption).

That said, the only drawback this may have is that the performance of both your network & your PC goes down the drain, if you set the "beacon interval" too low. But you will notice immediately, a value above 10 should not be a problem.

_**EDIT:**_
Keep us posted...

---

### Post by johnnabn on 2006-11-24
Its been running for about 2 full days now, no problems.

Thanks a lot for the help.

johnnabn

---

