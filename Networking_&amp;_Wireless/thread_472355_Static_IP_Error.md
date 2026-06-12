---
title: "Static IP Error"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by dalegribble on 2007-06-13
Hi all,

I'm trying to setup Ubuntu in vmware player.  When I try to bring up eth1 with a static IP address, I get the following error:

SIOCSIFNETMASK: Invalid argument
Failed to bring up eth1.

The setup is similar on my debian server.  I removed the network-manager package, and resolvconf is not installed.  I can ping IP addresses, but not names.  Any help that could be provided would be appreciated.  My /etc/network/interfaces file is listed below:

auto eth1
iface eth1 inet static
address 172.16.0.111
netmask 255.255.255.0
network 172.16.0.0
broadcast 172.16.0.255
gateway 172.16.0.1

Additionally, my /etc/resolv.conf is:

nameserver 172.16.0.1

---

