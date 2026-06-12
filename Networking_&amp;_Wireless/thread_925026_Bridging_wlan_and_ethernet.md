---
title: "Bridging wlan and ethernet"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by yudelevi on 2008-09-20
Hey Guys,

I want to connect eth0 (wired) to eth1 (wireless).
I've been trying to bridge my two interfaces using bridge-utils as following

[INDENT]ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
ifconfig brctl up
dhclient br0
[/INDENT]
after dhclient the device receives an IP from eth1, and computer can use eth1's internet connection. wireshark shows Ethernet packets from eth1 on eth1 interface (broadcasts in eth1's LAN). 
the 2nd device (connected via eth0) can not find the gateway connected via eth1, it sends ARP reqs for the gateway IP but it doesn't get any ARP reply.

Any ideas :-)?

Thanks,
Daniel

---

### Post by huwnet on 2008-09-20
I've had a similar problem for quite awhile (although I'm using Debian etch and not Ubuntu)

The only suggestion I found was that the wireless driver didn't support mac spoofing and so ebtables was suggested although I could never get this to work.

Would be interested in hearing any other possible solutions.

---

### Post by yudelevi on 2008-10-22
I actually solved this a few weeks back using a different way.
I've installed firestarter, allowed IP Routing and set a default gateway on the 2nd interface to be that interface's IP.
Same from 2nd network gateway.
After that all I had to do is to setup the routing tables properly and now it works like a charm.

The problem has something to do with MAC spoofing on the wireless lan interface, making bridges impossible.

---

