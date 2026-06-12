---
title: "dhcp3-server"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by j.bunce on 2008-08-08
Hi,

I'm having problems with dhcp3 configuration. It doesn't seem to allow CIDR subnets, i.e 10.X.X.X networks with a /22 mask. Anyone know of a fix for this, or an alternative DHCP server?

Cheers

---

### Post by j.bunce on 2008-08-08
Internet Systems Consortium DHCP Server V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

/etc/dhcp3/dhcpd.conf line 133: subnet 10.230.39.0 netmask 255.255.252.0: bad subnet number/mask combination.
subnet 10.230.39.0 netmask 255.255.252.0 
                                       ^
Configuration file errors encountered -- exiting

-- However using a /24 mask - 255.255.255.0 - Works without error. Any suggestions?

---

