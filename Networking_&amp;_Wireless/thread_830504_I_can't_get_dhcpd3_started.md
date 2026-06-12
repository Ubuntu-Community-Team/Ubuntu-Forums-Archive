---
title: "I can't get dhcpd3 started"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by rsepulvedacl on 2008-06-15
Hi.
I've got this message when I try to start the server:
```
 * Starting DHCP server dhcpd3                                           [fail]
```
Then I see the syslog and I see this:
```
Jun 15 21:52:19 servidor dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Jun 15 21:52:19 servidor dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Jun 15 21:52:19 servidor dhcpd: All rights reserved.
Jun 15 21:52:19 servidor dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jun 15 21:52:19 servidor dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Jun 15 21:52:19 servidor dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Jun 15 21:52:19 servidor dhcpd: All rights reserved.
Jun 15 21:52:19 servidor dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jun 15 21:52:19 servidor dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Jun 15 21:52:19 servidor dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Jun 15 21:52:19 servidor dhcpd: All rights reserved.
Jun 15 21:52:19 servidor dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jun 15 21:52:19 servidor dhcpd: Wrote 0 leases to leases file.
Jun 15 21:52:19 servidor dhcpd: 
Jun 15 21:52:19 servidor dhcpd: No subnet declaration for eth1 (0.0.0.0).
Jun 15 21:52:19 servidor dhcpd: ** Ignoring requests on eth1.  If this is not what
Jun 15 21:52:19 servidor dhcpd:    you want, please write a subnet declaration
Jun 15 21:52:19 servidor dhcpd:    in your dhcpd.conf file for the network segment
Jun 15 21:52:19 servidor dhcpd:    to which interface eth1 is attached. **
Jun 15 21:52:19 servidor dhcpd: 
Jun 15 21:52:19 servidor dhcpd: 
Jun 15 21:52:19 servidor dhcpd: Not configured to listen on any interfaces!

```
I've got this thing into my dhcp.conf file:
```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.130;
  option domain-name-servers 200.28.4.129,200.28.4.130;
#  option domain-name "internal.example.org";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.131;
  default-lease-time 600;
  max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
```
And this into my dhcp3-server file:
```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"
```

I've got i386 Hardy installed into my computer. I've got two interfaces (eth0 that's connected to my ADSL router and eth1 connected to a switch for my network). I can't find where to write a subnet declaration. Please help me!
I made this settings before with Gutsy successfully. I don't know what happened now. :(

---

### Post by rsepulvedacl on 2008-06-15
Solved... I had to write these lines into terminal:
```
$ sudo ifconfig eth1 down
$ sudo ifconfig eth1 192.168.0.1 up
```

---

### Post by rsepulvedacl on 2008-06-16
Now I'v got problems with the other PC's into the network. I can't get them with IP address through DHCP.
I want you to see my /etc/interfaces file:
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
```
I connect through PPPoE with eth1...

---

### Post by Iowan on 2008-06-17
> **rsepulvedacl said:**
> I've got this thing into my dhcp.conf file:
```
#
...
# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.130;
  option domain-name-servers 200.28.4.129,200.28.4.130;
#  option domain-name "internal.example.org";
  option routers 192.168.0.1;
  option broadcast-address [COLOR="Red"]192.168.0.131[/COLOR];
  default-lease-time 600;
  max-lease-time 7200;
}
...
```
Kind of a non-standard broadcast address for the subnet mask.  See if it works with 192.168.0.255.

---

