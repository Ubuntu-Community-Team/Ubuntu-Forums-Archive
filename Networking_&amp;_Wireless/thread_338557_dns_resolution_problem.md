---
title: "dns resolution problem"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by nonamesir on 2007-01-14
Hello,

I installed ubuntu server under vmware and I wanted to setup static IP + opendns for dns

My /etc/network/interfaces looks like this:
> 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.136.128
        netmask 255.255.255.0
        network 192.168.136.0
        broadcast 192.168.136.255
        gateway 192.168.136.1

and /etc/resolv.conf looks like this:

> 
search localdomain
nameserver 208.67.222.222
nameserver 208.67.220.220


prepend domain-name-servers 208.67.222.222, 208.67.220.220;


I'm unable to ping outside sites.

Any idea as to what is going on?

Thanks

---

