---
title: "telling the network card what it is..."
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by Forlornity on 2007-02-19
Hi, I have a network card running on the RTL-8139/8139C/8139C+ (rev 10) chipset, so it works out of the box of course. Problem is, I managed to install an RT61 wireless card on my Ubuntu Machine, and doing so has stopped the machine from recognizing anything on eth0 or any interface other than ra0. It could just be that I'm an id107 and know nothing about linux. Could someone help me either find out what it IS recognized as or help me tell the machine to recognize it as eth0.

Thanks, Forlornity

---

### Post by Forlornity on 2007-02-19
Change of mind, I'm trying to set up DHCP on my machine, it's connecting to a network using ra0 the subnet it's connecting to is 192.168.1.0, I want it to assign to the subnet 192.168.2.0
the dhcp server can't find eth0 when look for it although it's defined in /etc/network/interfaces
I don't know if any of this makes sense, I'm a complete nublet, so any help is much appreciated. 

Thanks, Forlornity

---

### Post by Xappe on 2007-02-19
for a start, post the output of

```
ifconfig
```

here.

---

### Post by Forlornity on 2007-02-19
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:B8:9F:8A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x8f00 

i believe that's the relevent section, but the dhcp still won't find it, my dhcp server config file reads:
#ddns-updates on;
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't


# default-lease-time 600;
# max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

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
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.100 192.168.2.200;
  option domain-name-servers 202.188.0.133, 202.188.1.5;
  option domain-name "tm.net.my";
  option routers 192.168.1.1;
  option broadcast-address 192.168.2.255;
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

any thoughts?

---

### Post by Forlornity on 2007-02-19
Bump.
Anyone able to help?

thanks, Forlornity

---

### Post by Forlornity on 2007-02-21
rebumpified, Anyone got any thoughts?
Anyone at all?
Please?

---

### Post by gradedcheese on 2007-02-21
> **Forlornity said:**
> Change of mind, I'm trying to set up DHCP on my machine, it's connecting to a network using ra0 the subnet it's connecting to is 192.168.1.0, I want it to assign to the subnet 192.168.2.0
the dhcp server can't find eth0 when look for it although it's defined in /etc/network/interfaces
I don't know if any of this makes sense, I'm a complete nublet, so any help is much appreciated. 

Thanks, Forlornity

dhclient will ask for an IP address via broadcast, so any DHCP server on any subnet can reply, and whoever replies supplies the IP address it uses.  If I understand you correctly, you have two DHCP servers running somewhere?

---

