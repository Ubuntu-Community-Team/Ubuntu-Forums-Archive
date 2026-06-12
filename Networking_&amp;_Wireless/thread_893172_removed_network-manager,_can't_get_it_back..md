---
title: "removed network-manager, can't get it back."
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by LeftyAce on 2008-08-18
Hi all,

Short version: I removed network-manager and network-manager-gnome and now  I can't get them back (because I can't get a working network connection without them).  To complicate matters, I have a Thinkpad x61 which has no cd drive.

I'm dual booting XP, and can connect to the net and download stuff, which I can then open off the ntfs partition through ubuntu.  Can anyone help me get my networking working again?  

The reason I removed them in the first place was I'd been having issues with my wireless connection periodically resetting, and read that network-manager could be the cause.  I installed wifi-radar, but it sees my network SSID with zero signal strength, and can't connect. (EDIT: zero signal even when I'm standing right under one of the APs, so distance from AP to laptop is approx. 3 feet).

I'm trying to connect to a campus-wide wifi network, and in windows, I can see the different APs (6 of them within the 80% range) and pick which one I want.  In Ubuntu I never had that option, it just shows me one "network".  wifi-radar does the same.

Any help much appreciated!

---

### Post by LeftyAce on 2008-08-18
SOLVED!  Based on a recommendation in another thread, I installed wicd (by downloading the .deb in windows) and it works great.  Shows individual access points, where network-manager never did.  I'll see whether it has the intermittent dropping issue or not.

---

