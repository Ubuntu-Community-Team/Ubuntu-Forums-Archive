---
title: "IPv6 static IP ID"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by geohei on 2014-03-10
Hi.

My IPv6 ID (last 64 bit) of Ubuntu 12.04 4 Server a static since every reboot changes.

1. Can I avoid this?
2. If not, how can I make it static, knowing that the prefix which the provider assigns to my router changes.

The reason for all this is, that I have port forwardings assigned in the router to this machine. The router requires (of course) to enter the ID of the server for the traffic to be properly rerouted. If the server reboot changes the IPv6 ID of the server, I have to manually adapt the port forwarding setting inside the router ... which is not really what I want.

Any ideas?

Thanks,

---

### Post by Iowan on 2014-03-10
I haven't dealt with IPv6,  but the most common solutions for IPv4 addresses are to manually set a static address outside the DHCP server's range (but still inside the subnet), or set up the DHCP server (router) to issue a static lease, based on MAC address.

---

### Post by geohei on 2014-03-10
Yes, I know IPv4 mechanisms to make the IP static, but IPv6 with changing prefix is far more complicated since prefix needs to be combined with ID or /etc/network/interfaces only defines the ID, which I don't know.

---

### Post by geohei on 2014-03-11
This solves the problem: [http://wiki.ubuntuusers.de/IPv6/Privacy_Extensions](http://wiki.ubuntuusers.de/IPv6/Privacy_Extensions)

Disabling the privacy extension (/etc/sysctl.d/10-ipv6-privacy.conf - net.ipv6.conf.all.use_tempaddr = 0) does the job!

---

