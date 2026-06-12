---
title: "Booted up this morning and no wireless"
date: 2013-10-28
forum: Networking &amp; Wireless
---

### Post by mkstallings1 on 2013-10-28
I currently triple boot Windows XP, Ubuntu 13.10, and Kubuntu 13.10.  I have the Broadcom BCM 4318 wireless card and everything was working just fine on Friday when I shut my laptop off.  This morning, Kubuntu is showing no wireless, while Windows and Ubuntu are working just fine.  I had to install the package "linux-firmware-nonfree" in order to get wireless working the first time.  I'm not really sure where to go from here.

---

### Post by mkstallings1 on 2013-10-28
By the way

[COLOR=#000000]dmesg | grep b43:

[/COLOR][   13.202998] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   13.244050] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   20.324060] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

---

### Post by mkstallings1 on 2013-10-29
I guess this is one of those things that hopefully fixed itself.  This morning, wireless is working fine.  I guess it's solved for now.

---

