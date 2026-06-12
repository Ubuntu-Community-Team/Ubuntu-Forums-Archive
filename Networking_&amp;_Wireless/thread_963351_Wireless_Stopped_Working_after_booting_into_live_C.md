---
title: "Wireless Stopped Working after booting into live CD"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by wormser on 2008-10-30
I booted into the RC1 release of Kubuntu to check it out.  When I booted back into my Gusty install my wireless card will not display available networks.  This has happened before and the solution was to boot into XP and connect.  It is like the firmware for the card 'locks' up and Ubuntu is not able to release it.  XP for some reason can.  Any ideas on fixing this within Ubuntu?  Here are some things I have tried and hardware details.

```
03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
```

ifconfig down and up
dhclient
disabled card in GIU
restart networking

---

### Post by wormser on 2008-11-01
I fixed it again by booting into Windows.  It would be nice to know how to fix this with out having to boot into Windows, since I am permanently removing Window soon.  Even though it is fix if you know then answer please post.

---

