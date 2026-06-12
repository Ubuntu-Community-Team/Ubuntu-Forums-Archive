---
title: "[SOLVED] wireless drops connection after a few minutes"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by battledean on 2008-08-27
Hi all

I recently installed 8.04 and an Edimax wireless USB stick (the card uses the RT2571 chipset).  Everything worked straight out of the box and was rock solid.  I set up port forwarding on my router and I could ssh and vnc into my server with no problems at all and stay logged in (from work) all day.

A few days ago I changed routers from the 2Wire 2700 to my Netgear DG384.  At that point my wireless started going screwy.  I changed back to the 2Wire router thinking the netgear was the problem but the wireless is still having the following issues:

After a reboot everything is fine.  Then a few minutes later during transfers across the network, e.g. an update, the connection is dropped. At this point network manager (and now wicd which I installed last night) still think the wireless network is ok.  There's bars on the wireless indicator in my toolbar.  If I reconnect to the wireless network it's fine again for a few seconds then it disappears once more.  If I try pinging my router or forcing dhcp to reconfigure I get nothing.

I've check dmesg and syslog and I can't see anything obvious.

Can someone point me in the direction of where to look?  Is there a debug log for the drivers that I can check to see what's happening?

I spent the last few weeks meticulously configuring Myth, WordPress and Apache on the box so I'm reluctant to wipe it and reinstall.

Any help would be very much appreciated,
Paul

---

### Post by battledean on 2008-08-27
After more reading and fiddling I suspect I am using old drivers and my best bet is to build the RT73 serialmonkey drivers and install those as per [this]("http://ubuntuforums.org/showthread.php?t=400236") post.  I'll report back progress.

---

### Post by battledean on 2008-08-27
That fixed it.  Everything is working fine.  The rt73 installation instructions were spot on and worked exactly as described.

---

