---
title: "No IPv4 on my eth0?"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by Eran on 2006-10-05
Hi,

After installing a new Ubunto and struggling a bit with the Ethernet card (regular, not wireless), it seems like I have a problem getting an IP address. I believe it is not a DHCP problem.

When I do

$sudo ifconfig eth0

I eventually get something very strange:

eth0      Link encap:Ethernet  HWaddr 00:08:54:DA:07:5A
          inet6 addr: fe80::208:54ff:feda:758/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xe800

Note that the line of inet addr (IPv4 address) is completely missing. As I'm now to Linux, and have nothing else to compare to, it seems to me very strange.

I have tried to renew the DHCP lease by typing:

$sudo dhclient -n

but it times out (all discovery messages are sent, no offers received). I have other computers on the LAN, that have no problem getting a lease from the router. 

Any ideas?

---

