---
title: "Wireless-n (802.11n) Ubuntu Supported Cards?"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by EnterDaMatrix on 2007-07-29
Are there any Ubuntu supported Wireless-n cards? I would prefer PCI, but USB would suffice. Also what router would you reccomend?

---

### Post by EnterDaMatrix on 2007-07-30
Is there any information about these at all? I read that Madwifi has support for the Atheros Xspan, but the only card with that chipset is a PC Card. Is there any PCI at all?

---

### Post by macleod199 on 2007-09-15
> **EnterDaMatrix said:**
> Is there any information about these at all? I read that Madwifi has support for the Atheros Xspan, but the only card with that chipset is a PC Card. Is there any PCI at all?

I'm able to use the DWA-542 D-Link PCI card on Gutsy, but not by default.  I had some luck with using ndiswrapper, but had problems getting it to load on start-up.  I now switched to madwifi, but it's only support in the development version (download via svn and compile).  Recently I had to blacklist ipv6 to get it to connect, though, see:

[http://ubuntuforums.org/showthread.php?t=551325](http://ubuntuforums.org/showthread.php?t=551325)

Note that it won't actually connect in N speeds, though (I don't think there's any support for N at all in any of the wireless projects yet), and I couldn't find any PCI cards that would do the 5 GHz band.

---

