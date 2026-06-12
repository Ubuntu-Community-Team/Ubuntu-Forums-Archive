---
title: "Ubuntu 7.10 on VMWare Workstation"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by eXPeri3nc3 on 2008-02-05
Hi all! I'm using VMWare Workstation, and installed Ubuntu 7.10 in it. Everything's fine so far, until I notice that I can't connect to the internet.

I tried sudo ifdown eth0 and sudo ifup eth0. It manage to make me connected to my modem. I can't access the internet. 

My modem is DHCP enabled, bridged. Ethernet adapter is bridged. The connection in Ubuntu is DHCP controlled.

I tried reading other threads, but others are concerned about making VM work in Ubuntu, not the other way. :(

What should I do? I'm lost. Thanks.

---

### Post by kirsche on 2008-02-05
Do you get an IP address assigned which is in the same subnet as your host system?
Try changing the virtual network to NAT and try to renew your lease again (either ifdown/ifup or dhclient)

---

### Post by eXPeri3nc3 on 2008-02-06
> **kirsche said:**
> Do you get an IP address assigned which is in the same subnet as your host system?
Try changing the virtual network to NAT and try to renew your lease again (either ifdown/ifup or dhclient)

Yes. I tried NAT too, it doesn't even bring me to the modem page. On the other hand, bridge brings me to modem page, but cannot connect to the internet.

I tried something someone posted here in setting the DNS server manually, that failed too.

Help please. Thanks!

---

