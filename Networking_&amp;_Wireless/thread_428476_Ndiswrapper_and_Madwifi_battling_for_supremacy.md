---
title: "Ndiswrapper and Madwifi battling for supremacy"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by kpjoyce on 2007-04-30
I'm trying to get ndiswrapper to work for my atheros 5211 pci wireless NIC.
Everything seems to go well, but the installed windows driver (net5211.inf) doesn't want to work.
The system pauses now during startup while configuring network interfaces.  It says that something called rename_netif (or similar) is unable to change the device name to ath0.  That tells me that there is still some remnant of Madwifi hanging around.
I've blacklisted the modules ath_pci, ath_hal, ath_rate_sample, and wlan.
Where is this rename command hiding?
Thanks

---

### Post by kpjoyce on 2007-04-30
Ndiswrapper is working for me now.  Yeah, baby.  I found a newer version of the windows driver that I didn't know about.
So my issue is no longer critical.
But network config during boot up is still slow, and my wireless device is called ath0, so there is still some part of madwifi somewhere.  So if you have any thoughts ...
Thanks

---

