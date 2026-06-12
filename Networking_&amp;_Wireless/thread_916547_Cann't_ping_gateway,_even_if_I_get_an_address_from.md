---
title: "Cann't ping gateway, even if I get an address from it"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by halllv on 2008-09-11
Hi, everyone

Using DHCP to get a address from the gateway.. it's work well. but I cann.t ping that gateway, which give me an address. so I cann't connect internent. 
why this happen?

/etc/inti.d/networking restart

There is already a pid file /var/run/dhclient.eth0.pid with pid 6113
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:17:30:61:ec
Sending on   LPF/eth0/00:16:17:30:61:ec
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 211.68.71.4 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:17:30:61:ec
Sending on   LPF/eth0/00:16:17:30:61:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 59.64.158.124 from 59.64.156.1
DHCPREQUEST of 59.64.158.124 on eth0 to 255.255.255.255 port 67
DHCPACK of 59.64.158.124 from 59.64.156.1
bound to 59.64.158.124 -- renewal in 4695 seconds.

ping 59.64.156.1 
there is no respond.

---

### Post by halllv on 2008-09-11
Maybe I know the reason...
I shut down the computer one hour, then start it..
it work now.. I think maybe my IP address expired, but why I restart my computer or restart the networking that is no use, untill I shut down total for a while..

---

### Post by SecretCode on 2008-09-11
The DHCP server could be set to ignore pings. That doesn't mean you won't be able to access the internet. If you can get an IP address via DHCP but still not access the internet there is some other reason.

---

