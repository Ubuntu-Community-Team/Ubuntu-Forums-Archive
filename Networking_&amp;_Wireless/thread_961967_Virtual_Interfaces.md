---
title: "Virtual Interfaces"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by gen3ric on 2008-10-28
I did a search and found some useful tips, but nothing that exactly helped. I am trying to create multiple virtual interfaces to test dhcp. This is what I have tried:

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:1c:ab:72:82:02

auto eth0:1
iface eth0:1 inet dhcp
hwaddress ether 00:1c:ab:72:82:02

```

This is what happens when I try to bring networking back up:
/etc/init.d/networking restart
```

 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 8152
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1c:ab:72:82:02
Sending on   LPF/eth0/00:1c:ab:72:82:02
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.24.0.18 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1c:ab:72:82:02
Sending on   LPF/eth0/00:1c:ab:72:82:02
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 172.27.84.206 from 172.27.85.253
DHCPREQUEST of 172.27.84.206 on eth0 to 255.255.255.255 port 67
DHCPACK of 172.27.84.206 from 172.27.85.253
bound to 172.27.84.206 -- renewal in 51 seconds.
There is already a pid file /var/run/dhclient.eth0:1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0:1.
   ...done.

```

The whole point of this is so I can script creation of virtual interfaces to scale to the scope of my network. Any advice for creating multiple dhcp virtual interfaces? Thanks.

---

### Post by gen3ric on 2008-10-28
btw, I'm running 8.04 desktop.

---

