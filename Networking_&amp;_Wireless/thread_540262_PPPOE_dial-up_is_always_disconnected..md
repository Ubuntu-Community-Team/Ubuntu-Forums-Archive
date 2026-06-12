---
title: "PPPOE dial-up is always disconnected."
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by amumu on 2007-09-01
I'm using Ubuntu7.0.4, and configure PPPoE function via "pppoeconf", and everything is set by default.
Now my connection is disconnected for a while, and through the Syslog, I found DHCP client re-did something, any idea?

My Log:
Sep  1 21:47:38 qinfeng-laptop pppd[14959]: Plugin rp-pppoe.so loaded.
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: pppd 2.4.4 started by qinfeng, uid 1000
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: PPP session is 9404
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: Using interface ppp0
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: Connect: ppp0 <--> eth0
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: PAP authentication succeeded
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: peer from calling number 00:0F:CD:EA:DA:16 authorized
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: replacing old default route to eth0 [192.168.1.254]
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: Cannot determine ethernet address for proxy ARP
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: local  IP address 58.34.122.219
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: remote IP address 218.1.60.247
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: primary   DNS address 202.109.14.5
Sep  1 21:47:38 qinfeng-laptop pppd[14961]: secondary DNS address 202.96.209.133
Sep  1 21:52:38 qinfeng-laptop dhclient: DHCPREQUEST on eth0 to 192.168.1.254 port 67
Sep  1 21:52:38 qinfeng-laptop dhclient: DHCPNAK from 192.168.1.254
Sep  1 21:52:38 qinfeng-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Sep  1 21:52:38 qinfeng-laptop dhclient: DHCPOFFER from 192.168.1.254
Sep  1 21:52:38 qinfeng-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep  1 21:52:38 qinfeng-laptop dhclient: DHCPACK from 192.168.1.254
Sep  1 21:52:38 qinfeng-laptop dhclient: bound to 192.168.1.50 -- renewal in 1694 seconds.

---

### Post by amumu on 2007-09-01
Up, nobody knows?

---

