---
title: "Internetworking"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by chrisdavid_175 on 2008-01-24
I've been using linux for a while but I'm still not that very good with it. I'm stumped trying to get computers to talk across networks.

Setup:
I have two networks - 192.168.1.0/24 and 192.168.15.0/24. On both of the networks, there is a system with two NIC's with IP addresses 192.168.1.1 and 192.168.15.2. I have set /proc/sys/net/ipv4/ip_forward = 1. On the 192.168.15.0/24 network, I have the router, 192.168.15.1, to the Internet.

I'd like to get hosts on the 192.168.1.0/24 network to talk to the hosts on the 192.168.15.0/24 network but I can't seem to get them to ping each other. I understand that using iptables and the masquerade option can allow hosts on 192.168.1.0 to talk to hosts on 192.168.15.0. But then I'd have to use port forwarding for them to talk in reverse.

Is there a way to get them to talk without using MASQUERADE?

---

### Post by hahahan on 2008-01-25
Chrisdavid_175,

Here: [http://tldp.org/HOWTO/IP-Masquerade-HOWTO/index.html](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/index.html) you find usefull information on how to set up MASQUERADING on a linuxbox.

Regards.

---

