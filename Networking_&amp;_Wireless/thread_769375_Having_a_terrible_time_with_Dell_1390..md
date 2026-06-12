---
title: "Having a terrible time with Dell 1390."
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by parkar on 2008-04-26
Ok I have read so many tutorials and this forum but I just can't get it to work.

I'm using Hardy Heron on my Dell e1705 but after trying the built in software to make it work as well as just using ndiswrapper and the terminal, I still do not have wifi. If I use a wired connection, everything works just fine.

So right now, I have a fresh install of Hardy and later on I can try a few things out on it. So anyone with the 1390 Wlan or e1705, if you could explain to me how you got your wifi working in Hardy that would be greatly appreciated as I really don't want to turn away from Linux. 

I'm loving everything else about it but this is putting a damper on everything.

---

### Post by drw777 on 2008-04-28
I feel your pain!  I'm a developer but a newbie to Ubuntu/Linux after 2 decades on Windows.  I have tried with ndiswrapper, ndiswrapper blacklisted and just using the new b43 driver and I cannot get wireless to work.

If I use ndiswrapper and the Windows XP 1390 driver then I can connect to any unsecure wifi but nothing that has security.  I followed this thread [http://ubuntuforums.org/showthread.php?t=769603](http://ubuntuforums.org/showthread.php?t=769603) and now my wifi card is enabled but does not see any of the half-dozen wireless networks in the building.

The learning curve on a new OS is pretty steep when one cannot get the basic peripherals to work.

Help please!

---

### Post by drw777 on 2008-04-28
I'm up and running!  This post is going over wireless.  I stayed with the b43 and no ndiswrapper.  Configured the SSID manually and it was working.  I get no indication that the wireless is working (task bar icons, etc) but it now connects.  Hope that helps.

---

