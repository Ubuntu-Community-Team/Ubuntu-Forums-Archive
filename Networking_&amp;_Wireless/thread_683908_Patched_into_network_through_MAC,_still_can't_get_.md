---
title: "Patched into network through MAC, still can't get online"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by motion parallax on 2008-01-31
I couldn't get on to my school network since they use the Odysseus client or the alternate SecureW2.  I called the IT center and had them register my MAC address directly.  

The network appears on my network list when I'm in range (didn't do that before the register).  Network Manager says I'm connected, but no programs can access the internet.  They just "load" indefinitely.  I tried a ping command from the terminal, but no results came.  

Instructions from my school to use this on Windows:

Input SSID
Make sure Open is in the Network Authentication: box
Make sure disabled is in the Data encryption: box

Thanks for any help.

---

### Post by motion parallax on 2008-01-31
Output of dhclient:

Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by motion parallax on 2008-02-02
Bump

---

### Post by motion parallax on 2008-02-04
Bump

---

