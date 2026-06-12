---
title: "DHCP3-Server - peer holds all free leases"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by terazen on 2008-02-18
Hi,
I'm using DHCP3-Server package on Ubuntu 7.04 release and getting the below error.  I've searched the web for a couple hours with no success.   It seems like a pretty common thing but no sites I found had a fix posted.

Feb 18 10:18:00 name0 dhcpd: DHCPDISCOVER from 00:11:02:c5:6b:f4 via 172.27.6.1: peer holds all free leases

What happened was I tried moving from a windows server to linux using redundant dhcp servers.  It worked fine from Saturday until this morning and it started getting this error on both servers even though only 2/3 of the leases are in use.  I have about 12 scopes and maybe 400 devices which all worked except this 1 desktop!  To fix this user I had to remove redundancy on the primary and disable dhcp on the secondary. 

Please help!  I'd hate to have to put dhcp on dual windows boxes to get redundancy back!

T.

---

### Post by sublimespot on 2008-02-18
Ive got the exact same error on a pair of servers. Had to disable the redundancy for the time being until this bug is fixed.
We also had the problem where it was assigning a new IP to nodes every time they restart! 

Our pair of servers have 70,000 IPs with 35,000 active leases.

---

### Post by terazen on 2008-02-19
Hrmm.. Well if it's a bug I guess I'll get a pair of windows boxes set up.

Could I subscribe to a mailing list somewhere to be notified when the bug is fixed?

---

