---
title: "dhclient not working with alias i/f (eth0:1)"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by no_brakes on 2008-10-09
I'm trying to get DHCP on eth0 and eth0:1.  I can't get dhclient to recognise the alias interface eth0:1.

So: "dhclient eth0" works Ok
But: "dhclient eth0:1" produces the errors:

----------------------------------------
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Listening on LPF/eth0/00:1f:29:0e:b7:4d
Sending on   LPF/eth0/00:1f:29:0e:b7:4d
Bind socket to interface: No such device
----------------------------------------

Because I'm trying to get two dhcp leases I've configured the dhcp client identifiers (see dhclient.conf) 

To test I've set 2 reservations on the DHCP server, and if I swap the client-identifer then eth0 will pick up the respective IP addr, so this bit is working.  It just won't do anything with eth0:1, it only works for eth0.

There is a "psuedo" option for dhclient.conf, but it requires a link to an external script, which is getting waaay to deep for me!!

Anyone know how to config dhclient for an alias interface name?!

Thanks!


/etc/network/interfaces
----------------------------------------
auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet dhcp
----------------------------------------

/etc/dhcp3/dhclient.conf
----------------------------------------
request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;

interface "eth0" {send dhcp-client-identifier 1:0:1f:29:e:b7:4d;}
interface "eth0:1" {send dhcp-client-identifier 1:ac:de:48:0:6:1;}
----------------------------------------

---

### Post by silvavlis on 2008-11-28
I'm trying to do exactly the same. I also tried exactly the same :-) and I also didn't succeeded :-(

Please, post the solution if you find it. Of course, I'll post it if I find it first ;-)

---

