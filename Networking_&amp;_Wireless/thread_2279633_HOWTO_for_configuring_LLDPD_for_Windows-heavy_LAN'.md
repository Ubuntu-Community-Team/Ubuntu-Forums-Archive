---
title: "HOWTO for configuring LLDPD for Windows-heavy LAN's?"
date: 2015-05-25
forum: Networking &amp; Wireless
---

### Post by bcschmerker on 2015-05-25
I am finding few clues for configuring the Link Layer Discovery Protocol Daemon in Ubuntu® 12.04.5 and later LTS.  As of May 2015, I've one LinUX box that shares a Netgear® WNDR4500v2 router with a bunch of 'puters running mostly Microsoft® Windows® 7.0.8001 (Kernel 6.1.7601), with one Win 8.1.11000 (Kernel 6.3.9600) portable thrown in.  None of these Winboxes will detect the Hot Rod gPC™, as it is invisible to their Link Layer Topology Discovery scan.  What I need to do is enough configuration for the gPC™ to show up for a Winbox.

A response that will show, in Network and Sharing Center:
```
The following discovered device(s) can not be placed on the map.  Click here to see all other devices.

hotrodgpc-desktop
```
is sufficient, as I do not expect /usr/sbin/lldpd to act like C:\Windows\SysWOW64\Networks\LLTDIOM.dll (as used in the Microsoft® Windows® Rally64™ Porting Kit).  Users of Debian® Lenny™ had hit-and-miss results with lld2d, so I'd prefer to use an LLDPD solution if one has been worked out.  Thanks in advance.

---

