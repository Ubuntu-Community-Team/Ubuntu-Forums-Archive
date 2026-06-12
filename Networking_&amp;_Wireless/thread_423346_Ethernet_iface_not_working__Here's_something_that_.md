---
title: "Ethernet iface not working?  Here's something that might help."
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by j3ff on 2007-04-25
Hello,

Since installing fiesty I've found that my ethernet interface was not working.  It wasn't just a case of selecting it with the network monitor either.   All I had was loopback.

sudo lshw indicated that my ethernet card was detected and the driver was called dmfe

I'll get to the point.  I ran 
```
sudo ifdown eth0
```
and got the following response
```
There is already a pid file /var/run/dhclient.eth0.pid with pid 3706
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:08:a1:17:9e:2e
Sending on   LPF/eth0/00:08:a1:17:9e:2e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
```
I then brought the interface back up with 
```
sudo ifup eth0
```
and got the following output ...
```
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:08:a1:17:9e:2e
Sending on   LPF/eth0/00:08:a1:17:9e:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.31 -- renewal in 32432 seconds.
```

After that eth0 had an ip address and I was on my LAN again.  Problem solved, sort of.  I still don't know why the interface isn't available after boot.  Any further insights would be very helpful on that score.

---

### Post by chili555 on 2007-04-26
Can you verify that in System -> Administration -> Networking under Properties for your wired ethernet connection, the box 'Enable this connection' is checked? Also, in */etc/network/interfaces* is the wording present:```
auto eth0
``` If not you can add it with sudo gedit.

---

