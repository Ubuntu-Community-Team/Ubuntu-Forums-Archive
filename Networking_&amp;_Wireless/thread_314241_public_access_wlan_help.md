---
title: "public access wlan help"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by shimmyshack on 2006-12-07
Hi,

The street i'm in has loads of guest houses, with migrant workers, and they get charged loads for internet access, in the spirit of Ubuntu I want to allow free access.

(ifconfig output at bottom)
I have latest xubuntu, internet is via
 eth0 (0.7) on LAN, gateway 0.1. 
The box also has
 eth1 (2.7), gateway 0.1 

A wireless AP is 2.10 gateway 2.7

So far so good, people can connect and get on, however I want to: 
*rate limit the connection 512kb/s (the lowest my AP allows is 1Mb/s so I want to use ubuntu to do the bandwidth shaping)
*protect my ubuntu box from wireless users
*restrict ports so no file sharing.

Note, I don't want to run squid. I simply want to use iptables etc... to limit the rate of the connection.

I have available: iproute2 (iproute), shaper, cbq.init-v0.7.3, firestarter, and shorewall.

Please can someone take me through some steps to achieve this?

I have followed other how-tos but they are never quite compatible, for instance [http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html#AEN60](http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html#AEN60) gets me as far as "Download cbq.init-v0.6.2 and put it in /etc/rc.d/", but I dont have rc.d, instead I have rc0.d ... rc6.d.

Thank you for anything you can suggest.



-----ifconfig output ------------

eth0      Link encap:Ethernet  HWaddr 00:03:47:8B:6E:FD  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe8b:6efd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1490  Metric:1
          RX packets:297861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:102298593 (97.5 MiB)  TX bytes:19725484 (18.8 MiB)

eth1      Link encap:Ethernet  HWaddr 00:14:BF:5D:BC:CC  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe5d:bccc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:135884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150162 errors:34 dropped:0 overruns:0 carrier:38
          collisions:0 txqueuelen:1000 
          RX bytes:16896317 (16.1 MiB)  TX bytes:63170292 (60.2 MiB)
          Interrupt:11 Base address:0xd800

---

