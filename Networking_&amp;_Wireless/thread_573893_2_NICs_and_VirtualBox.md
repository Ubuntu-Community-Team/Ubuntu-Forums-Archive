---
title: "2 NICs and VirtualBox"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by RayVad on 2007-10-12
This is the situation i like to configure for my system to run VirtualBox:

Got 2 NICS in my system on which i like to have 1 configured for the system itself and 1 to use as the bridging NIC for VirtaulBox.
The OS that should be running in VirtaulBox will have an IP in the same subnet as the system NIC.

Eg. 
ETH0: 192.168.6.4 subnet 255.255.255.0 broadcast 192.168.6.255

ETH1: ? but i need something like br0 to tap0. So it needs some bridging.

Then on the VirtualBox, the client OS will have an IP like:
192.168.6.5 subnet 255.255.255.0 broadcast 192.168.6.255

How does ETH1 needs to be configured to get this up and running?
So that i will have ETH0 (Ubuntu) and the VirtualBox client in the same subnet?


This is my etc/networks/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.6.4
netmask 255.255.255.0
gateway 192.168.6.1

#auto eth1

iface eth1 inet static
address 192.168.6.10
netmask 255.255.255.0
gateway 192.168.6.1

#Bridging on eth1
auto br1
iface br1 inet static
address 192.168.6.10
netmask 255.255.255.0
gateway 192.168.6.1
        bridge_ports eth1 vbox1

#Tap interface eth1
auto vbox1
iface vbox1 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        down ifconfig $IFACE down
        tunctl_user ray



Regards,
Ray

---

### Post by RayVad on 2007-10-14
Enyone can give me a clue about routing for two NICs on the same LAN?

---

