---
title: "D-Link DWL-G510 not working after kernel update! Help please!"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by BuRn_sLuG on 2008-03-01
Hey guys,

I have compiled and installed the latest kernel (2.6.24.3) following the guide from the "Master Kernel Thread", and can boot into the kernel fine. I am using Ubuntu 7.10, with all the latest updates installed. I do receive one error booting up though, and that is something along the lines of "Starting Avahi error mDNS/DNS-SD [fail]", but the kernel will still load and I can still do everything in Ubuntu fine (except the main problem of wireless not working).

I used ndiswrapper following the guide from [this thread](http://ubuntuforums.org/showthread.php?t=564419), and the wireless works perfectly in the 2.6.22-14-Generic kernel (posting  from it). The wireless card is a D-LINK DWL-G510 and uses a Ralink RT61 chipset (as I use the rt61.inf off the cd that came with the card). 

The wireless does not work at all in the new kernel though, clicking on the network manager in the top right of GNOME results in "SIOCFLAGS error: No such device" showing up. The device still shows  up in hardware information in the new kernel, so I believe it can see it :S. When I  go into Network settings there is only a "modem connection", and I do not have a 56k lol.

It is probably worth noting that when I compiled the new kernel I included support for the ralink cards in the wireless section, but the card will not work in either kernel without ndiswrapper, and will not work at all in the 2.6.24.3 kernel, so that did not appear to work/help at all haha.

Any help with this would be awesome guys!

Thanks

---

### Post by BuRn_sLuG on 2008-03-02
Bump, anyone?

---

### Post by BuRn_sLuG on 2008-03-02
Solved for now hopefully;

[Link](http://forums.debian.net/viewtopic.php?t=21519&start=0&postdays=0&postorder=asc&highlight=&sid=31b550856490ea2450ee406856447923)

---

