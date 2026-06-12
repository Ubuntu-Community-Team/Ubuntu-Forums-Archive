---
title: "Wireless internet in Ubuntu 7.10"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by eajohnson on 2008-02-17
So i've got myself a nice little problem here.

I've got Ubuntu 7.10 installed and am having problems getting wireless internet to work. I have used multiple how-to guides on the forums here for broadcom chipsets.  Also tried installing NDISwrapper using smackywentz's guide and to no avail.   I'm using a dell 1450 wireless USB adapter.  The kicker is that i can get wireless to work just fine in XP SP2 (which i dual boot) and wired works.  After i disconnect from wired or occasionally when i boot up, the wireless will work for a couple minutes before it craps out on me.  Any suggestions?

And here's the message i get from dmesg:


 686.178225] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  686.193848] eth1: Initial auth_alg=0
[  686.193856] eth1: authenticate with AP 00:15:05:ee:0a:e1
[  686.393221] eth1: authenticate with AP 00:15:05:ee:0a:e1
[  686.593030] eth1: authenticate with AP 00:15:05:ee:0a:e1
[  686.792844] eth1: authentication with AP 00:15:05:ee:0a:e1 timed out
[  688.095652] eth1: Initial auth_alg=0
[  688.095662] eth1: authenticate with AP 00:15:05:ee:0a:e1
[  688.295425] eth1: authenticate with AP 00:15:05:ee:0a:e1
[  688.495229] eth1: authenticate with AP 00:15:05:ee:0a:e1
[  688.695038] eth1: authentication with AP 00:15:05:ee:0a:e1 timed out
[  799.699194] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  799.701511] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  800.453657] usb 5-7: USB disconnect, address 2
[  810.319769] eth0: no IPv6 routers present


Thanks in advance,

EAJ

---

