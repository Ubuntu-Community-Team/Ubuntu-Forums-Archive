---
title: "Iphone hot spot / Network card interactions"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by jdallara on 2013-09-17
Hello,

  I have my desktop computer running Ubuntu 13.04 connected to the Internet via my Iphone using its personal Hotspot connection via its USB cable.  It is enabled as eth1.  I also have a local LAN via the ethernet card on the desktop which is connected to a switch.  It is enabled as eth0.  The switch also has my printer and laptop connected to it.

Iphone-------->Desktop------->Switch<--------Printer
                                                                                                      <--------Laptop


If I enable the Iphone first, either by plugging it in or through Network Manager, then enable the ethernet card, everything works just fine.  I can access web pages and print them at the same time.  If I disconnect and then re-connect the Iphone (happens often), then I lose web access.  I can still print.  If I disable the ethernet card via Network Manager, I then regain web access.  I can then re-enable the ethernet card and I have printer access again.

Can this interaction be prevented?  I'd like to have the ethernet card connection on all the time because I need the printer access at times when the Iphone is not connected.  The same also happens when I connect the Iphone to the Laptop, I have to disable/re-enable the network card on the laptop to get web access.

Second Question:  Can I get my laptop to connect to the internet via the Iphone given the arrangement as shown, i.e. laptop->switch->desktop->Iphone, or do I need to use a router instead of a switch, or is it not possible?

Thanks in advance,

Jon.

[ATTACH]246311[/ATTACH]

---

