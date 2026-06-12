---
title: "samba ethernet w98 usb"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2005-11-09
I have an adsl modem router with one ethernet port and one usb port. Ubuntu is on the ethernet, Windows 98 is on the usb. Both access the internet with no problem. I can ping both machines from the other one. However I cannot get samba to work I have tried all the installation methods mentioned in the forums plus applying all the advice from samba site.

I am wondering if samba cannot work because of the usb connection.

Any IDEAS

---

### Post by mips on 2005-11-10
That is plausible.

The USB is actually not using Ethernet protocol. The Win98 PC is most likely running PPPoE client on the machine and only communicates with the DSLAM in the exchange.

If you installed a small switch/hub and connected the router and both PC's via ethernet you should have joy.

---

