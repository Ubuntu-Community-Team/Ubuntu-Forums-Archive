---
title: "Webmin ISC DHCPd 3.0.4 server not working"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by archer007 on 2007-07-30
OS: Ubuntu Ultimate Edition 1.3

I want to have my Ubuntu desktop act as a DHCP server for my XP laptop, and get an ad-hoc LAN going. 

I have configured my two wired Ethernet interfaces, eth0 and eth1, to have a static IP address of 192.168.9.9 and a subnet of 255.255.255.0 . Then, I configured Webmin to use eth0 and eth1 under "Edit Network Interface". 

I configured the subnet as follows:

Network Address: 192.168.9.9
Address Ranges: 192.168.1.5 - 192.168.1.5
Netmask: 255.255.255.0

Then, I clicked "Edit Client Options" and set the following:

Subnet Mask: 255.255.255.0
Default Routers: 192.168.9.9

I saved the subnet and went back to the main screen. Then, [as recommended]("http://doxfer.com/Webmin/DHCPServer"), I clicked Edit Client Options and switched "Dynamic DNS Update Style" to "None"

Then, I attempted to start the DHCP  server, and got the following error:

```
dhcpd self-test failed. Please fix the config file.
The error was:
```

No error type or code was displayed, so I have no idea what is wrong.
Here's the config file:

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
ddns-update-style none;


default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
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
#	}
#}
# Primary Submet
subnet 192.168.9.9 netmask 255.255.255.0 {
	option subnet-mask 255.255.255.0;
	option routers 192.168.9.9;
	range 192.168.1.5 192.168.1.50;
	}

```

Am I doing something wrong?

---

### Post by archer007 on 2007-07-30
Does anyone even have general ideas about this?

---

### Post by xxcite81 on 2007-10-01
I had the same problem too. What i realized is that webmin PID file location was wrong. mine was 
```
/var/run/dhcp3-server/dhcpd.pid
``` but you can check it in the init file by typing ```
sudo gedit /etc/init.d/dhcp3-server
``` and look for dhcpd.pid.

Then all you have to do is to put that location in the module config of webmin for dhcp (Dhcp pid file section). So its actually working but webmin doesnt know that.

---

