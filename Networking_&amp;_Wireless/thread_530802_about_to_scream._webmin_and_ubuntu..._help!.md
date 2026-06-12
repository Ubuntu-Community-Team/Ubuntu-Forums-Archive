---
title: "about to scream. webmin and ubuntu... help!"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by skylord23 on 2007-08-20
Ok. so i have ubuntu 7.04 and webmin 1.360. i am trying to setup this box to be a router
with my ubuntu box i can get online, view pages via links and ping out to sites.
i configured the second nic via emacs /etc/network/interfaces to produce a static ip.
i then installed dhcp3-server.
i configured my server via webmin
```
option domain-name "192.168.5.1";
option broadcast-address 192.168.5.255;
option subnet-mask 255.255.255.0;
option routers 192.168.5.1;
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
ddns-update-style none;

option domain-name-servers 192.168.5.1;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

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
# sadf
subnet 192.168.5.0 netmask 255.255.255.0 {
	option domain-name-servers 192.168.5.1;
	option broadcast-address 192.168.5.255;
	option subnet-mask 255.255.255.0;
	option routers 192.168.5.1;
	range 192.168.5.2 192.168.5.10;
	host asda {
		option domain-name-servers 192.168.5.1;
		option domain-name "192.168.5.1";
		option broadcast-address 192.168.5.255;
		option subnet-mask 255.255.255.0;
		option routers 192.168.5.1;
		hardware ethernet 00:13:d4:10:a0:fb;
		fixed-address 192.168.5.5;
		}
	}

```

that is the full config file for the dhcp server in webmin. the really annouying thing is that the computer on the network recievs the 192.168.5.5 ip addy i assign it so i know the dhcp server is assigning the address. i am unable to ping out on that machine nor view any pages. i have tried 4 different machines(by this i mean 4 actual computers with fresh installs on each) and multiple different NICs on each machine.
what am i missing? i have also configured linux firewall to allow connections as discribed in this walk through:[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)
as well as trying to just allow all traffic no matter where it is going.

PLEASE help i am going insane with this

---

### Post by jakev383 on 2007-08-20
I haven't used Webmin in years....
Anyway, try this:
sudo echo "1" > /proc/sys/net/ipv4/ip_forward

---

### Post by skylord23 on 2007-08-20
> **jakev383 said:**
> I haven't used Webmin in years....
Anyway, try this:
sudo echo "1" > /proc/sys/net/ipv4/ip_forward

this says permission denied without asking for password. is there any other program i can use to accomplish my goal? i want to create a router with this linux box. pretty simple task i thought.

---

### Post by dmizer on 2007-08-20
first of all, a word of extreme caution ... be sure that your webmin is **_not_** accessable from the internet.  it's painfully easy to crack because it's only password protected.  also, you're better off with a hardware firewall like a router instead of exposing your server to the net.  unless you really NEED extremely fine tuning of your routes (as with HUGE networks, or if you have a need for restricting/monitoring certain kinds of traffic across the gateway - as with a corporate environment), there's no reason for wasting an entire machine on gateway duty.  plus, having a linux box as your gateway is extremely high maintenence.

here's a good firewall setup for internet connection sharing.  i have used this on several machines:
[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28sharing%29%7C%28connection%29%7C%28internet%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28sharing%29%7C%28connection%29%7C%28internet%29)

before following that howto, be sure to remove any webmin firewall configuration you may have previously attempted.

---

### Post by skylord23 on 2007-08-21
well the reason i want to do this is because i want to host apache server and file server from this machine and also my router at home keeps dropping out. so i figured i would config a spare machine here to act as the router and also file/web servers. 
i will try that walk through you posted when i get home. is there another way to do what i am trying to accomplish? there has to be some way to just host a router via this box.

---

### Post by jakev383 on 2007-08-22
> **skylord23 said:**
> well the reason i want to do this is because i want to host apache server and file server from this machine and also my router at home keeps dropping out. so i figured i would config a spare machine here to act as the router and also file/web servers. 
i will try that walk through you posted when i get home. is there another way to do what i am trying to accomplish? there has to be some way to just host a router via this box.

I do the same thing, but I use CentOS on mine.  Not 100% how to do it all with Ubuntu....  I imagine that the iptables stuff would be the same.  This is a script that is pretty close to what I use for the firewall:
[http://www2.gsu.edu/~usgkssx/firewall.html](http://www2.gsu.edu/~usgkssx/firewall.html)

---

