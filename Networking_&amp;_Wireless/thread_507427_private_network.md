---
title: "private network"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by stefansjs on 2007-07-23
I'm trying to configure a direct ethernet connection right now between 2 ubuntu computers.  Both of them are running 7.04 server edition.  Both of them have 2 ethernet interfaces right now, though in the future I only intend on using 3 of the 4 overall connections.  The setup that I would like is to have one computer (call it computer A) connected to the internet/public-ish network (campus network) and connected to the other computer at the same time.  I do not want the other computer (call it computer B)  to be connected to anything but computer A.  This is a very painful process for me right now because I do not intend on using more than one internet connection and 2 cables, but this hardware makes it difficult to work with, since every time I want to connect to a different computer (via SSH) I need to switch the cables around.  Anyways, the problem:
Currently computer A is configured for DHCP on eth0 and statically configured on eth1 with an IP of 192.168.1.102.  The /etc/interfaces file looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#The part that I added myself.  This is the secondary ethernet
#port which is the port on the right, when viewing the computer
#from behind (i.e. connect the left port of this computer to the
#ethernet on the file server
iface eth1 inet static
address 192.168.1.102
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254


I also configured computer B to have the same setup, except that eth1 is statically configured for 192.168.1.101.  The problem is that every time either computer boots it does not bring up eth1 on its own.  I need to bring it up on my own using ifup eth1.  The other problem is that every time I bring up eth1 and disconnect the cable, it seems to forget about it's DHCP'd connection to the public network.  After disconnecting and reconnecting the ethernet cable, i can no longer SSH into it.  Given limited ethernet cables this makes my task an impossible one.
My questions are 
1.  Am i configuring my private "network" (of 2 computers) correctly?
2.  Do I need anything additional to make this network work (router, switch etc.)?
3.  How do I get it to automatically bring up eth1 on boot?
4.  What might be causing my computer to not be found on the network after bringin up eth1?

Thanks

---

