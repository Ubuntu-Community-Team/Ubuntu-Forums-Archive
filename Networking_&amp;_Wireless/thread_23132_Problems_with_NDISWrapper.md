---
title: "Problems with NDISWrapper"
date: 2005-03-31
forum: Networking &amp; Wireless
---

### Post by cybiant on 2005-03-31
I was able to get NDISWRAPPER to recognize my Dell Latitude D800 Broadcom wireless NIC, but no matter how many times I try to assign the ESSID it won't accept it.  It also detects the card as a 802.11b instead of g.  When I tried the linuxant wrapper it will detect the card correctly and it even obtains an IP, but the system can't route out to the internet and it starts randomly locking up after just a few minutes of uptime.  I've tried everything..even trying the new test version of Fedora Core...but quickly remove and reloaded Ubuntu..atleast with ubuntu it detects 95% of my hardware :-).  Please help me.  I'm trying to learn Ubunutu so I can start supporting Linux systems instead of my day job of supporting Windows systems.

---

### Post by CarlosJHernandez on 2005-04-01
I had similar problems with ndiswrapper the installation wiki at  ndiswrapper.sourceforge.net has been greatly improved and the most important part for me was: **make sure that ESSID is set in output of iwconfig wlan0**. If I saw ESSID: off/any, then no matter what I tried It didn't work.

Other thing was when trying the command iwconfig <my wlan0> essid <name>, name had to be qouted. as in "myroutername", let me know if it works for you.

happy hacking

---

