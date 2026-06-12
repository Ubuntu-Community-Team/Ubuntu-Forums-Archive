---
title: "DHCPd &gt;&gt; Checking Client Status"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2008-01-31
Dear all,

I had build an Access Point with Linux and it is working. Client able to connect to it and obtained IP address via DHCPd. 

But my problems now is, how to monitor the status of which PC/clients that connected to my access point. Like commercial wifi router, it able to know which clients that connect to the router with their IP and machine name, 

How to actually viewing or obtaining the connected clients status?

Please help. Thanx.

---

### Post by Yhetti on 2008-01-31
You can do this a couple ways.  In /var/lib/dhcpd[3-server]/ (or around there, depending on your config) is a file called "dhcpd.leases".  That can tell you most everything you need to know. 

If you need something more 'realtime', the ARP table will have the MAC address and the IP address that are connected.  

arp -an

Will give you currently active MAC and IP addresses.  You can then pull the Windows name using

nmblookup -A <ipaddr>

Which is part of the samba-common package,

Using the combination of those two, you can develop a script pretty quickly to display it.  In Perl or whatever.

---

### Post by Paris Heng on 2008-01-31
Yes, thank man, I get it. 

*/var/log/messages*

Jun 31 12:38:19 elrond dhcpd: DHCPDISCOVER from 00:e0:d3:82:a6:ad via ath0
Jun 31 12:38:20 elrond dhcpd: DHCPOFFER on 10.0.20.10 to 00:e0:d3:82:a6:ad via ath0
Jun 31 12:38:20 elrond dhcpd: DHCPREQUEST for 10.0.20.10 from 00:e0:d3:82:a6:ad via ath0
Jun 31 12:38:20 elrond dhcpd: DHCPACK on 10.0.20.10 to 00:e0:d3:82:a6:ad via ath0

*/var/lib/dhcp/dhcpd.leases *

I also found some solution, installed **udhcpd**, issued **dumpleases**, to view all the connected client with their MAC addr and IP addr.

---

### Post by Paris Heng on 2008-01-31
Solved and delete this thread please.

---

### Post by miguelito on 2008-03-17
thanx!, i have the same problem, trying to listing client dhcp



:guitar:

---

