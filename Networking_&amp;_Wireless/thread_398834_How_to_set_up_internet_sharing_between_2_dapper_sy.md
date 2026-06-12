---
title: "How to set up internet sharing between 2 dapper systems?"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by akshay_jp on 2007-04-01
hi,

this is my network configurations on the PC connected to internet directly

Eth1 (connects to internet)
IP : 192.168.1.100
NetMask : 255.255.255.0
Gateway : 192.168.1.1
DNS : 61.1.96.69

Eth0 (connects to the other dapper machine)
IP : 192.168.201.150
NetMask : 255.255.0.0
Gateway : (left blank)
DNS : (left blank)

this is the network configuration on the PC in LAN, connected to the above pc

Eth0 : 192.168.201.151
NetMask : 255.255.0.0
Gateway : 192.168.201.150 (ip address of the former pc)
DNS : 192.168.201.150

now the big question , how do i make the PC on Lan access internet , through the PC connected to internet??

can anyone please put up the procedure? (or a link thereof)

Is it necessary to run a proxy on the machine connected to internet?

Some friend of mine suggested that i run a proxy on one , and i installed SQUID, but i messed up big time,
now i cant connect to internet from that PC also

kindly help!!!

Regards
Akshay

---

### Post by solar george on 2007-04-01
Install firestarter on your internet connected computer.  It's config has an option to enable internet connection sharing.

---

