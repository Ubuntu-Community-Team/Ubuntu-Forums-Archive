---
title: "[Gutsy] WMP54Gv2, Ndiswrapper, Zyxel Prestige Router Rebooting under load"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by xequios on 2008-02-15
Hi,

ADSL Modem with Wireless Router: Zyxel Prestige 660HW-D1
24Mbit ADSL2+, DHCP, WPA(1)

Only device on router is this PC with Linksys WMP54Gv2 using NDISWRAPPER, WICD and wpa_supplicant

Linux: Fresh install of Gutsy

The Problem

Most of the time the WLAN is working flawlessly, however it seems if I download at very high speeds the wireless connection is dropped and the router reboots itself.

This same hardware has been running 100% flawlessly under XPsp2 for many months, I have never seen the router reboot itself under even the most intense bandwidth usage...

Anyone got an idea as to how a wireless connection can cause a router to reboot itself?

---

### Post by mrsteveman1 on 2008-02-15
Thats quite some problem, it's difficult to diagnose problems like that because the real problem lies in the router (otherwise nothing would be capable of rebooting it remotely). There isn't anything i can think of that would be able to cause a router to reboot itself other than heat or high load, or perhaps an odd bug in the router.

I would suggest that you perhaps connect another wireless access point to the modem and disable the internal wireless on the zyxel just to see if that changes things.

---

### Post by xequios on 2008-02-15
Thanks for the reply :-) I see by your sig you must know a thing or two about networking! I came to the same conclusion as you but I thought I'd at least throw a line out here in the hope that someone else knows something I don't that could shed some light on this. At the moment its not too much of a problem, more an annoyance, and if and when I can get the hardware I will try another router/AP.
I have been in the IT industry for over 10 years in varying fields but this is my first really serious adventure into the land of Linux so I feel a little lost at times, but so far this has been the most enjoyable linux experience and I really think I am close to ditching windows!

---

### Post by mrsteveman1 on 2008-02-15
It may be that this router has a known issue that causes it to fail and reboot.

It might also be worth it to login to the routers telnet interface and check its logs. The password should be the same as the webinterface.

---

### Post by xequios on 2008-02-15
I just had a quick go with the telnet to see what I can do but I don't really know what I'm doing in there and didn't get far! I also had a quick look for some new firmware but it is using the latest and I am always wary of flashing stuff :-)

My best bet is to try another device or failing that re-arrange my apartment and ditch the wireless,

---

