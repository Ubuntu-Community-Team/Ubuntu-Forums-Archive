---
title: "I hate to do it: Intel 3945 connection issue. No IP address."
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by Tweek84 on 2007-07-20
I just picked up a new laptop and it has the Intel 3945 a/b/g wireless card. I'm running Feisty w/ KDE. 

I've been looking through the many threads regarding the 3945 and haven't found a fix yet. I'm at the point where I may even end up installing Vista just to test the wireless in a windows environment but I'd love to avoid that so I'm turning to the experts!

The access point has no WEP, Mac filtering or other restrictions. I've tested with another laptop and it connects just fine.

Everything "looks" normal to me except I cannot pick up an IP address.

If I use kwifimanager I can see the network fine, I get "Ultimate" signal  but the LAN IP is unavailable. If I attempt to use ifdown/ifup it eventually just tells me that no dhcp offers were received.

```
mcassils@lappy2000:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1b:77:61:ff:0b
Sending on   LPF/eth1/00:1b:77:61:ff:0b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Not sure where to go from here. Thanks in advance!

Edit: I can't figure out how to delete my post, but the issue is resolved:) Thanks anyway!

---

### Post by 5-HT on 2007-07-20
May I ask how you figured it out? I've always run into problems with {k}networkmanager and ipw3945 and use either wifi-radar or a manuall config, but I'd like to switch.
cheers,

---

