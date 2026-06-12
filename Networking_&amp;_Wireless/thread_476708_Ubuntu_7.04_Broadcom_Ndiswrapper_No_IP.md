---
title: "Ubuntu 7.04 Broadcom Ndiswrapper No IP"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by bobby.hawk on 2007-06-17
Hello,

I've installed Ubuntu 7.04 from scratch on my Dell Latitude D400. The install went great but I've really struggled to get Wireless working. Out of the box my internal Wireless card did not work. I have a Broadcom chipset 4306. Digging around I found a great doc on the Ubuntu help site.
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)

I went through the install procedure for ndiswrapper and that seem to work fine.
I can now click on the networking icon at the top of my screen and see my wireless router by name but it will not connect and get an IP address.

bhawk@D400:~$ iwlist eth1 scanning

eth1 Scan completed :
Cell 01 - Address: 00:0C:41:4B:84:B6
ESSID:"bigrouter"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:62/100 Signal level:-56 dBm Noise level:-96 dBm
Encryption keyff
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
Extra:atim=0

bhawk@D400:~$ dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

Anyone have an idea why I'm getting Permission denied?

Bob

---

### Post by whtriced on 2007-06-17
Try the second command again using "sudo"

---

