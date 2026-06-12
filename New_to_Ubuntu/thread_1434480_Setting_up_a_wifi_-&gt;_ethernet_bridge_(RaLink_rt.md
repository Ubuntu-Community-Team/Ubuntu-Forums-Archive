---
title: "Setting up a wifi -&gt; ethernet bridge (RaLink rt2500)"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Yodastein on 2010-03-20
Hi all,

Setting up my first Linux box and have hit a hurdle.

I have a wireless router/switch that is connected to the internet on the other side of my house. Here in my office I have about 4 machines that I want to set up on a wired network, with an ubuntu box as their server. The server will need to connect wirelessly to the router and bring internet to the wired machines.

I have a Belkin Wireless Desktop G Card installed in my server, this comes up as a RaLink RT2500 card, and finds the rt2500pci driver on the machine. This works fine and connects to my wireless network as a standalone machine, it can see the internet fine. There is also an Ethernet card in the server that works fine if I plug directly into the router.

However when I go to set it up as a bridge, the wireless connection stops working completely. I can't ping or do DNS lookups anymore.

This is the contents of my /etc/network/interfaces file. Any idea what I am doing wrong?

=========================

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Wireless adaptor
auto wlan0
iface wlan0 inet static
address 192.168.1.253
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
wireless-essid xxxxx
wireless-key xxxxx

# Bridge
auto br0
iface br0 inet static
bridge_ports eth0 wlan0
address 192.168.0.100
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255

---

### Post by Yodastein on 2010-03-20
Ok, having a bit more luck with this config file. When it is running my server can still see the internet.

If I run 'brctl showmacs br0' I can see the Mac addresses of machines in both networks, so something is working.

However the packets just aren't getting across the bridge. A machine on the wired network can ping the bridge, but can't ping the wireless router which is across the bridge.

Any tips?
=============
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Ethernet adaptor
auto eth0
iface eth0 inet static
address 192.168.1.100
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.254

# Wireless adaptor
auto wlan0
iface wlan0 inet static
address 192.168.1.253
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
#wireless-mode master
wireless-essid xxxxx
wireless-key xxxxx

# Bridge
auto br0
iface br0 inet static
bridge_ports eth0 wlan0
address 192.168.1.99
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.254

---

### Post by Yodastein on 2010-03-21
I found a (sort of) solution to this. after many hours of trying this I think I'm hitting this issue:

[http://serverfault.com/questions/114657/linux-ethernet-wireless-bridging](http://serverfault.com/questions/114657/linux-ethernet-wireless-bridging)

Basically the wireless router is seeing these MAC addresses come out of nowhere, and is not sure where to return the packet to.

I've given up on bridging the networks, and set up NAT using iptables. I had to put the 2 networks on different IP ranges, but after I added a static route to my wifi router, both sides can see everything on the other side.

---

