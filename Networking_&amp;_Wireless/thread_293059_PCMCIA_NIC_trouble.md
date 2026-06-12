---
title: "PCMCIA NIC trouble"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by dhollema on 2006-11-04
I'm having trouble getting a D-Link 690-txd PCMCIA NIC working on a Panasonic Toughbook laptop.  This is a wired card.  Works fine on a windows machine, all hardware is fine.  My 2 ubuntu desktops have no trouble getting on my LAN or accessing the internet.

ifconfig shows eth0 to be present, kernel module seems to be loading fine (8139too) but not sure.  ifconfig shows no IP address.  I think the problem is that my DHCP server (d-link router) is not assigning me an IP.  I tried setting the IP to static to no avail.  sudo dhclient times out on DCHPDISCOVERY and shows network sleeping...

I need help on what to do next...

Thanks,

Dave

---

