---
title: "Problems with setting up routing for OpenVPN"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by dangerjunkie2002 on 2007-02-13
Hi,

I've been trying to install an OpenVPN server on one of my Dapper boxes. I've got the client and server installed and put in a stunnel tunnel over SSH to avoid a restriction on my customer's proxy. 

The client can sign in to the server, exchange HMAC and keys then complete initialization. The client's TAP interface has acquired a valid address from the server's address pool but I can't ping the server (or any other address) on my LAN.

Client tap0 address 192.168.1.30
Server address: 192.168.1.80
Netmask of my network is 255.255.255.0
Gateway of my network is 192.168.1.1

I've put wireshark on the client tap0 and at showed ping ARPing but getting no response. If I turn the loggin verbosity up to 9 on OpenVPN I can see TUN_WRITE entries in the server log at the same times as the ARPs so I think the link is working in one direction. If I ping the client from the server I see no log entries on either the client or server so I think the problem is with the configuration of the TAP or bridge on the server.

My problem is that I need to be careful as I am 2000 miles away from the server and I can only administer it over SSH so if I hose the networking I'm pretty well screwed. I've already had one accident that needed me to get somebody to go to my office and reboot the server so I copied a friend's bash script that logs various things, puts the old /etc/network/interfaces file back then reboots the server. I use the "at" command to schedule this every time I make a change so it gets rolled back if I then can't log in.

I am using a modified interfaces file I got from a friend as follows:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
name Ethernet LAN card
address 192.168.1.80
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 192.168.1.80

#added for OpenVPN
auto br0
iface br0 inet static
	address 192.168.1.80
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	bridge ports eth0 tap0
	gateway 192.168.1.1
	dns-nameservers 192.168.1.1 192.168.1.80
	pre-up /usr/sbin/openvpn --mktun --dev tap0
	pre-up ifconfig eth0 0.0.0.0 up
	pre-up ifconfig tap0 0.0.0.0 up
	pre-up brctl addbr br0
	pre-up brctl addif br0 eth0
	pre-up brctl addif br0 tap0
	ifconfig br0 192.168.1.80 netmask 255.255.255.0 broadcast 192.168.1.255
	post-down ifconfig eth0 0.0.0.0 down
	post-down ifconfig tap0 0.0.0.0 down
	post-down brctl delif br0 eth0
	post-down brctl delif br0 tap0
	post-down brctl delbr br0
	post-down /usr/sbin/openvpn --rmtun --dev tap0


I can provide the openvpn config files if needed.  I'm using the server-bridge directive and tap interfaces.

I've never configured bridges and taps before so I'm sure I've made some silly mistake. I will be really grateful for any help you can give me.

Thanks,
Paul.

---

