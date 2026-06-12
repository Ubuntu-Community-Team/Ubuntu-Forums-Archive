---
title: "access point - ath0 disables eth0 connection"
date: 2005-07-01
forum: Networking &amp; Wireless
---

### Post by skippuff54 on 2005-07-01
hey,

the ubuntu box is going to serve as a wireless access point, and for the past week or so i've been tweaking .conf files, installing drivers and configuring interfaces.

right now, the wired connection eth0 works flawlessly all the time.  ath0, the netgear WG311T, works too, kinda.  (hey, anyone who pulled this up searching for help with madwifi drivers - don't give up!) the xp box i've been using to scan for networks can see the wireless served via ath0, but it can't connect.  and after configuring br0, messing with dhcpd.conf and resolv.conf, the internet connections consistently timeout.

deactivating ath0 gets me back on the internet, like right now.  so essentially, the cards both work, there is a bridge between them, and when ath0 is up, connections always timeout.

these are files that i've been getting to know very well recently:
[COLOR=DarkGreen]
/etc/resolv.conf[/COLOR]

ok, so i just went to post resolv.conf for you and it looks like something wrote over it.  lemme keep searching on that - these are the other two:
[COLOR=DarkGreen]
/etc/dhcpd.conf[/COLOR]

#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
#ddns-update-style interim;

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
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 192.152.2.0 netmask 255.255.255.1 {
#}

# This is a very basic subnet declaration.

#subnet 192.168.1.0 netmask 255.255.255.0 {
 # range 192.168.1.10 192.168.1.20;
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
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.200;
  option domain-name-servers 4.2.2.1, 4.2.2.2, 4.2.2.3;
#  option domain-name "internal.example.org";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
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

[COLOR=DarkGreen]alright, and the /etc/network/interfaces file[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface ath0 inet static
address 192.168.1.5
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-essid shaDe
wireless-mode Master

auto eth0





auto ath0

---------------------------
a couple of questions on this one:  does /etc/network/interfaces need a "auto br0" line?  what about "map ath0"?

finally, what i'm really wondering is why the network relies on the operability of ath0 when it's activated, as the wired connection eth0 is the one that's physically connected to the cable modem?

---

