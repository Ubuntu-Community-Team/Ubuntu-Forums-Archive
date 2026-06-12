---
title: "dhcp - server help"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by rmmst49 on 2006-08-04
i use kubuntu w/ a verizon evdo card on my laptop.  It is the only internet connection I have.  I have a couple of other pc's, running dsl,mepis and windows.  Since evdo uses the pcmcia slot, my eth0 port is open.  I need to be able to share my laptops internet connection with my other pc's for updates etc.

Right now, the only way i can do it is with windows.  Through windows networking, I set up my laptop to share its internet connection.  All i have to do is have an ethernet cable plugged into my dsl/mepis/windows box, and windows on my laptop with give a dhcp offer to whatever machine it's hooked up to.

I have been trying to get a dhcp3-server going with kubuntu, but I have not been able.  I have tinkered around with the conf file but can't seem to get it working.  When i run

#dhcp3-server restart

i get:

* Starting DHCP server:                                            [fail]




Hopefully someone can help.  I think my problem is that i'm putting the wrong values into my conf file.  Here is my ifconfig and my dhcpd.conf.
Please sugest needed changes, I'm new to networking.

by the way, the evdo card is ppp0
 
#################
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:70.195.43.174  P-t-P:66.174.10.132  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:14368607 (13.7 MiB)  TX bytes:619619 (605.0 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:26:A7:76  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30880 (30.1 KiB)  TX bytes:30880 (30.1 KiB)
################
################
################
# Sample /etc/dhcpd.conf
# (add your comments here) 
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "jetnet";

option ip-forwarding on;

option netbios-name-servers 192.168.1.1;

subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.10 192.168.1.100;
   range 192.168.1.150 192.168.1.200;
}

#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
#ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

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
#subnet 192.168.0.0 netmask 255.255.255.0 {
#  range 192.168.0.100 192.168.0.200;
#  option domain-name-servers 0.0.0.0, 0.0.0.0;
#  option domain-name "70.95.3.171";
#  option routers 192.168.0.1;
#  option broadcast-address 192.168.0.59;
#  default-lease-time 100;
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
################

---

### Post by rmmst49 on 2006-08-04
bump

---

### Post by stormblue on 2006-08-04
have you checked out [this]("http://www.ubuntuforums.org/showthread.php?t=91370&highlight=internet+sharing")

---

