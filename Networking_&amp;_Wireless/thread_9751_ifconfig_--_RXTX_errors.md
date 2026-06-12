---
title: "ifconfig -- RX/TX errors"
date: 2004-12-31
forum: Networking &amp; Wireless
---

### Post by spb on 2004-12-31
Hi,  

I'm having problems getting a samba server to work on my ubuntu machine.  From what I've read from newsgroups I believe that there may be a problem with my NIC.  

Also I find that I can ping from my Mac to the linux machine faster than I can ping from the linux machine to the Mac.  

When I run ifconfig eth0 I find RX and TX errors (lines 5 and 6):  

eth0      Link encap:Ethernet  HWaddr 00:C0:F0:6D:3F:C8
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:f0ff:fe6d:3fc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:979631 errors:3 dropped:131071 overruns:0 frame:0
          TX packets:1029966 errors:4 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000
          RX bytes:175912499 (167.7 MiB)  TX bytes:348046143 (331.9 MiB)
          Interrupt:5 Base address:0xd000

I'd like to know if others see these types of errors or if my NIC card is damaged.  

Thank you,
sb

---

