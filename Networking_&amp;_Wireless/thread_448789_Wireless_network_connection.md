---
title: "Wireless network connection"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by KMW on 2007-05-19
Using a D-Link 614+ router and a D-Link 520+ wireless card.

In lspci, the card is seen as acx and size is 98564 and used by 0

in ifconfig -a, lo shows Link encap, inet addr, Mask, inet6 addr, RX and TX packets,. Then in wlan1 with HWaddr, inet6 addr, RX and TX packets and Interrupt,. wlan1 ava, Link encap, HWaddr, inet addr, Bcast, Mask,  Inrerupt.

iwconfig, I am getting an error,
Error for wireless request "Set ESSID" (8B1A): Set failed on device wlan ; no such device

dhclient wlan1, am getting Listening on, Sending on, DHCPDISCOVER
No DHCPOFFERS received. No working leasesin persistant database - sleeping  

Got this far with help from a friend on another forum but he is a CentOS user and I'm a newb.

---

### Post by KMW on 2007-05-20
Anyone any ideas?

Just as a test I removed the wireless card and installed a 3Com nic. Rebooted and immediately had an internet connection and was able to access the Windows network though the Windows PCs would not see the Ubuntu system.

So it has to be a connection setup problem. Maybe with the SSID?

---

### Post by KMW on 2007-05-23
Finally resovled after 2 weeks work.
Thanks for the replys.
Good luck,

---

