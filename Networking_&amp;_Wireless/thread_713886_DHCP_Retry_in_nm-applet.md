---
title: "DHCP Retry in nm-applet?"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by jallard on 2008-03-03
i'm running an up-to-date 7.10 system on my desktop at work with a single, direct wired connection to our networ, and I had problems with this system riding through a DHCP outage.  This past Friday our IT guys performed some maintenance on the DHCP server, it was down for several hours, and then came back online.  My desktop had been on the entire time, but the following morning, after many hours of the DHCP server being back online, it had no IP address.  I checked my dhclient.conf settings and retry had been left at the default, which the man page tells me should be five minutes.  When I rebooted the computer, it immediately recovered and received an address (the same one as I had before the DHCP downtime).

Is there a different place to set retry for nm-applet?  Or else, is there something else going on?

Cheers,

Jim

---

