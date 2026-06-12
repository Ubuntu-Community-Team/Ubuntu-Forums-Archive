---
title: "New to Ubuntu and Linux, can't make wireless connection with Linksys WMP54G"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by DetroitMike on 2007-04-28
I bought a new desktop a while back and have put both Ubuntu 7.04 and SimplyMEPIS 6.5 on the old desktop--800mhz Athlon P3-type machine.  The machine is in a room that has no cable connection, but with my Netgear router I connect successfully with a P4 laptop running XP.  So I checked the Ubuntu forum page for supported wireless cards--https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported--and bought a Netgear WG311.  I ordered it from the web and the version 3 model came, not the version 2 model described at Supported.  It contains a Marvell chipset.  I had no success even after using ndiswrapper to load the Windows driver.  After speaking with my brother, a long-time Linux person, I returned the card and bought a Linksys WMP54G instead.  This has a Ralink RT2561 chip in it.  The one on the WirelessCardsSupported site is version 4 and the one I found is 4.1, but I figured it would be close enough.  (As I said, I'm new to this.)

In Ubuntu, the operating system recognized it and loaded the proper driver, not an invalid one.  It was detected as ra0 just as stated in the Ubuntu wiki.  However, I still had no connection.  I turned on my Windows laptop to examine what it said about access.  It says it has direct access to the internet--no auto-detect proxy settings, no automatic nor manual proxy detection.  The manual proxy section is grayed out with localhost 127.0.0.1 in the No proxy for field.  In Ubuntu the choices are Static IP Address, Automatic Configuration (DHCP), or Local Zeroconf network (IPv4 LL).  I put in 127.0.0.1  as a static address.  In System Monitor the Network History graph shows activity, receiving 1.1-1.5KB/s and sending nothing.  Still no internet.  Any ideas?

THANKS!!!!!!

---

