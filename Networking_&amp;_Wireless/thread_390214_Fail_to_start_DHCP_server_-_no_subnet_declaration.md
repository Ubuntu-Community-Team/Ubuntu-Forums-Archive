---
title: "Fail to start DHCP server - no subnet declaration"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by MartinJ on 2007-03-21
Hi all,

I'm having difficulty starting the dhcp on my server.  As an overview, the server has one NIC (eth0) and a serial modem.  The NIC is attached to a hub, which is attached to other PCs.  The ubuntu server will be acting as a router, print server, local repository, etc.  DHCP is the last thing on my list.

Here's the excerpt from /var/log/syslog:
> Mar 21 21:40:53 localhost dhcpd: Wrote 0 leases to leases file.
Mar 21 21:40:53 localhost dhcpd:
Mar 21 21:40:53 localhost dhcpd: No subnet declaration for eth0 (0.0.0.0).
Mar 21 21:40:53 localhost dhcpd: ** Ignoring requests on eth0.  If this is not what
Mar 21 21:40:53 localhost dhcpd:    you want, please write a subnet declaration
Mar 21 21:40:53 localhost dhcpd:    in your dhcpd.conf file for the network segment
Mar 21 21:40:53 localhost dhcpd:    to which interface eth0 is attached. **
Mar 21 21:40:53 localhost dhcpd:
Mar 21 21:40:53 localhost dhcpd:
Mar 21 21:40:53 localhost dhcpd: Not configured to listen on any interfaces!


dhcpd.conf looks like this:
```
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

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
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

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
# scout subnet
subnet 192.168.0.0 netmask 255.255.255.0 {
	option domain-name-servers 192.168.0.1;
	option broadcast-address 192.168.0.255;
	option subnet-mask 255.255.255.0;
	option routers 192.168.0.1;
	range 192.168.0.2 192.168.0.254;
	}

```

and /etc/default/dhcp3-server shows:
> INTERFACES="eth0"


Basically, I'm lost and not having much luck finding solutions.

Thanks in advance!

---

### Post by spd106 on 2007-03-21
I've just tried your configuration here on my test network and it works perfectly.

I can only suggest that you check that the eth0 is up and configured properly, i.e. **ip addr** should show something like this excerpt
```
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0c:76:xx:xx:xx brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.1/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::20c:76ff:fexx:xxxx/64 scope link 
       valid_lft forever preferred_lft forever


```
Also make sure you are restarting the dhcp daemon after making changes, i.e. **sudo /etc/init.d/dhcp3-server restart**

---

### Post by MartinJ on 2007-03-21
Thanks for the help.

How should my interfaces file look so that eth0 is active but not looking for another dhcp server?

---

### Post by spd106 on 2007-03-21
Something like this
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

```

---

### Post by MartinJ on 2007-03-21
Thank you very much.

Working correctly

---

### Post by KailasNarendran on 2008-02-03
Thanks!  i had a similar problem. 

i have a 2 interface system i'm turning into a home router.  i didn't have eth2 in my /etc/network/interfaces file.  added it as you described and dhcp server comes up.

thanks again!

---

