---
title: "Is IP_ADVANCED_ROUTER enabled in Ubuntu Server kernel image?"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by deejaylinux on 2007-01-17
Hi forum,

My question is about routing in Ubuntu Server.

I like to set up my Ubuntu Server box acting as a router. The machine has two interfaces:

eth0 - wired card connected to 192.168.2.0 network.
eth1 - wireless card connected to 192.168.1.0 network, which has access to the Internet through 192.168.1.1 gateway.

The only think I want to do is redirect all traffic from eth0 to eth1. No filter. No NAT. Only routing.

I set 1 in the file /proc/sys/net/ipv4/ip_forward, but still it is not working. The route table is this:

192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.1
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.3
default via 192.168.1.1 dev eth1

All help would be appreciated.

Thanks in advanced and regards

---

