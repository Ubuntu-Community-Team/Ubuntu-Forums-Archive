---
title: "network not loading on startup; ubu2004_server"
date: 2020-07-27
forum: Networking &amp; Wireless
---

### Post by Ordes on 2020-07-27
ubuntu server 2004
running on virtualbox
network:
enp0s8  >> virtual host >> IP STATIC
enp0s17 >> NAT 	   >> DHCP	

/etc/network/interfaces 
	# The loopback network interface
	auto lo
	iface lo inet loopback

	# The primary network interface

	# 1. Static Adapter
	auto enp0s8
	iface enp0s8 inet static
	address 192.168.56.105
	netmask 255.255.255.0

	# 2. Dynamic Adapter >>  NAT 
	auto enp0s17
	iface enp0s17 inet dhcp

	# This is an autoconfigured IPv6 interface
	#iface enp0s17 inet6 auto

Problem: 
- on boot the enp0s8 stays down and no IP is assgined.
  - if set manual >> ip addr add 192.168.56.105/24 dev enp0s8 
  - the network starts up without any problems

- was using the same /etc/network/interfaces on server1604 without any problems
- no idea why it is not loading up on startup

txs for help

---

### Post by Ordes on 2020-07-27
Ok.

i already found the problem. 
Seems that /etc/network/interfaces has been replaced by "netplan"

Solution:
i installed "ifupdown" , and interfaces was working correctly.

i probably should read into netplan, to keep up to date

---

