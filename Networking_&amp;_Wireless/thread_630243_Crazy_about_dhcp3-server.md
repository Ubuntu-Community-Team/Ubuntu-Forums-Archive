---
title: "Crazy about dhcp3-server"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by ink70 on 2007-12-03
I'm really going crazy with this problem ... Hope someone can help me.
My goal is to build a LTSP server and thin client wit my Ubuntu 7.10 workstation. No luck out-of-the-box as many ltsp how-to promise.
So I decided to go step by step. My first problem suddenly arises building my DHCP server.
Some details of my system: Ubuntu Desktop 7.10, fresh and up- to-date installation.

This is the /etc/network/interfaces file:

________________

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.10.10.1
	netmask 255.255.255.0
	broadcast 10.10.10.255
	network 10.10.10.0

___________________________

This is the /etc/defaults/dhcp3-server file:
__________________________

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"
______________________________



This is the /etc/dhcp3/dhcpd.config file:
_______________________________

#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

subnet 10.10.10.0 netmask 255.255.255.0 {
	range 10.10.10.10 10.10.10.20;
	option routers 10.10.10.1;
	default-lease-time 600;
	max-lease-time 7200;
}
_________________________________




So, let's begin ...

1) Restart nework:
---
root@NFS-Share:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 19169
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:44:6e:2b:92
Sending on   LPF/eth0/00:02:44:6e:2b:92
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.9 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:44:6e:2b:92
Sending on   LPF/eth0/00:02:44:6e:2b:92
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.9
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.9
bound to 192.168.2.17 -- renewal in 268663 seconds.
                                                                         [ OK ]
---



Everything seems ok, my eth0 receives a new IP adress, I can surf the internet. My eth1 get its fixed IP at 10.10.10.1

2) Start dhcp3 server:
---
root@NFS-Share:~# /etc/init.d/dhcp3-server start
 * Starting DHCP server dhcpd3                                           [fail] 
---

ARRRGGGGGHHHHH!!!!! I can't understand why.

3) This is my syslog:
---
root@NFS-Share:~# tail /var/log/syslog
Dec  3 12:27:51 NFS-Share dhcpd: Wrote 0 leases to leases file.
Dec  3 12:27:51 NFS-Share dhcpd: 
Dec  3 12:27:51 NFS-Share dhcpd: No subnet declaration for eth1 (10.10.10.1).
Dec  3 12:27:51 NFS-Share dhcpd: ** Ignoring requests on eth1.  If this is not what
Dec  3 12:27:51 NFS-Share dhcpd:    you want, please write a subnet declaration
Dec  3 12:27:51 NFS-Share dhcpd:    in your dhcpd.conf file for the network segment
Dec  3 12:27:51 NFS-Share dhcpd:    to which interface eth1 is attached. **
Dec  3 12:27:51 NFS-Share dhcpd: 
Dec  3 12:27:51 NFS-Share dhcpd: 
Dec  3 12:27:51 NFS-Share dhcpd: Not configured to listen on any interfaces!
---

Any ideas? Please help ....

---

