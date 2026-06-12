---
title: "Another wireless dilemma"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by johnnyhop on 2007-10-06
Since installing Ubuntu 7.04 I've been unable to connect to my neighbor's WPA encrypted router which will connect in Windows and only one of four other Linux distros I've tried.  The issue is likely the Ralink RT2500 chipset.  I've tried four different "this works" found in Ubuntu forums and Ubuntu help pages associated with both WPA encryption and  the chipset but haven't gotten any of them to work.  Recently tried Ubuntu 7.10 Tribe 4 live CD then full install (on separate partition from 7.04) and got this response from Network Manager:  For the first time after loading the ESSID got a drop down menu which actually provided a WPA selection, selected WPA, input the passphrase and selected "connect."  The icon swirled for a short time then the computer froze, keyboard and all as if I was in Windows 95.  Got the same result with Kubuntu 7.10 Tribe 5.  I hope when the final 7.10 version is released this issue is resolved, if not with Network Manager at least with manually configuring /etc/network/interfaces.

Additional comment:  Thumbs up to wvdial, after both GUI's failed it was the answer to dial up Internet

---

### Post by Lambert on 2007-10-07
> **johnnyhop said:**
> Since installing Ubuntu 7.04 I've been unable to connect to my neighbor's WPA encrypted router which will connect in Windows and only one of four other Linux distros I've tried.  The issue is likely the Ralink RT2500 chipset.  I've tried four different "this works" found in Ubuntu forums and Ubuntu help pages associated with both WPA encryption and  the chipset but haven't gotten any of them to work.  Recently tried Ubuntu 7.10 Tribe 4 live CD then full install (on separate partition from 7.04) and got this response from Network Manager:  For the first time after loading the ESSID got a drop down menu which actually provided a WPA selection, selected WPA, input the passphrase and selected "connect."  The icon swirled for a short time then the computer froze, keyboard and all as if I was in Windows 95.  Got the same result with Kubuntu 7.10 Tribe 5.  I hope when the final 7.10 version is released this issue is resolved, if not with Network Manager at least with manually configuring /etc/network/interfaces.

Additional comment:  Thumbs up to wvdial, after both GUI's failed it was the answer to dial up Internet


This is from network manager page.

> 
While the driver supports WPA, it does not use Linux Wireless Extensions for WPA support, which is required for NetworkManager. Note: WPA/WPA2 is working since kernel-2.6.22 with the new Wireless-Stack and the latest rt2x00 CVS version.


gutsy will have 2.6.22, just depends on when they froze and if the changes in the driver will be updated enough. If not you will be able to compile from cvs the latest driver and use network manager.

It's getting there.

---

