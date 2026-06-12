---
title: "high ping times, delays in ssh"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by twofruits on 2007-02-17
I noticed something strange on my 6.10 install today. I was ssh-ing into my ubuntu 6.10 install from my Mac, and ssh was not responsive at all. Push a key and it would display 1 or so second later.

I pinged the Ubuntu laptop from my Mac, with responses like the following :-

PING 10.1.1.21 (10.1.1.21): 56 data bytes
64 bytes from 10.1.1.21: icmp_seq=0 ttl=64 time=1.918 ms
64 bytes from 10.1.1.21: icmp_seq=1 ttl=64 time=1.687 ms
64 bytes from 10.1.1.21: icmp_seq=2 ttl=64 time=1011.117 ms
64 bytes from 10.1.1.21: icmp_seq=3 ttl=64 time=3.063 ms
64 bytes from 10.1.1.21: icmp_seq=4 ttl=64 time=1010.960 ms
64 bytes from 10.1.1.21: icmp_seq=5 ttl=64 time=2.572 ms
64 bytes from 10.1.1.21: icmp_seq=6 ttl=64 time=1010.798 ms
64 bytes from 10.1.1.21: icmp_seq=7 ttl=64 time=2.390 ms
64 bytes from 10.1.1.21: icmp_seq=8 ttl=64 time=809.240 ms

I also tried it from another PC, and it had the same results. I've changed routers & cables with no improvement. It seems to follow a pattern of a low ping time, then a high ping time.

Any ideas what could be wrong or what I could check ?

The laptop is a Toshiba Tecra M5, Dual Core, 2 gig ram (less than 3 months old)

Running Ubuntu 6.10

From ifconfig :-

eth0      Link encap:Ethernet  HWaddr 00:0E:7B:A4:B2:F1  
          inet addr:10.1.1.21  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20e:7bff:fea4:b2f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:926721 (905.0 KiB)  TX bytes:189821 (185.3 KiB)
          Base address:0xcfe0 Memory:ffde0000-ffe00000

---

