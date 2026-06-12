---
title: "Need Help finding a new Router."
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by Shibblet on 2015-06-22
I am looking to buy a new router.  What I need in this router would be both Wireless N (5ghz) and G (2.4ghz).

There are about 16 devices that use my current router, I am using MAC filtering.  What I need is to have some of these devices connect to the Wireless N, with full bandwitdth, the rest of these devices connecting to the Wireless G, and are allowed limited bandwidth.

Is there a router out there that can do this?  I am currently running a Linksys E1500 with DDWRT Firmware.  This will allow me to limit the bandwidth (connection speed), but only to "all" wireless devices.

Thanks

---

### Post by bcschmerker on 2015-06-22
As it turns out, Linksys®/Cisco® has two models usable for upgrade from the E1500 that can take open-source firmware right off the bat:  The WRT-1200AC (867 Mbps @ 5 GHz) and WRT-1900AC (1.3 Gbps @ 5 GHz), both of which use ARM CPU's and external antennae.  Don't know what capabilities the stock firmware (compatible with Apple® Mac OS® X 10.6-up and Microsoft® Windows® 6-up) has for the kind of band-specific throttling, but either should be able to handle Ubuntu® Core 15.04-up for ARM, which permits maximum options for the serious webmaster.

Both meet IEEE 802.11a/g (2.4 GHz) and 802.11b/n/ac (5 GHz) right off the bat and come equipped with a 4-port Ethernet switch for the LAN and one each USB 3.0 and USB 2.0/eSATA ports.  A hardware-option module, the SE4008 WRT 8-Port Gigabit Ethernet Switch, expands the wired capacity of either above router.

---

