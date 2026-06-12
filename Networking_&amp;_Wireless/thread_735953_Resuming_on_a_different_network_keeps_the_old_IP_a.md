---
title: "Resuming on a different network keeps the old IP address"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by rrwo on 2008-03-26
Originally, when my laptop resumed when connected to a different LAN than it hibernated on, it has the IP address from the old LAN. (I had this problem with Gutsy as well as Hardy.)

Now, it won't even turn the devices back on when resuming at all! 

I checked my /etc/acpi/resume.d/ifup.sh and /etc/default/acpi-support files as compared with Gutsy.  They seem ok, only difference being in Hardy I had HIBERNATE_MODE=shutdown rather than HIBERNATE_MODE=platform. (Changing it to "platform" doesn't fix it.)

Note that I'm using /etc/network/interfaces and not NetworkManager.

---

