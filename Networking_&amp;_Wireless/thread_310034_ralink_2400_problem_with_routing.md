---
title: "ralink 2400 problem with routing"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by lesiu1111 on 2006-11-30
Hello,

I have problem with configure my Internet connection in Ubuntu 6.06.

Situation is:

1) By interface ra0 I connect to my Provider's LAN.
2) Then I connect to my Provider's VPN which in Windows gives me Internet Connection, but in Ubuntu no... :(. I think that this is routing table problem.

Command 'ifconfig' give me :

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2288 (2.2 KiB)  TX bytes:2288 (2.2 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:85.219.165.207  P-t-P:85.219.164.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1446  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5504 (5.3 KiB)  TX bytes:3123 (3.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:80:C6:E8:40:11  
          inet addr:10.0.14.254  Bcast:10.0.14.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c6ff:fee8:4011/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462 errors:39 dropped:39 overruns:0 carrier:0
          collisions:97 txqueuelen:1000 
          RX bytes:42988 (41.9 KiB)  TX bytes:49715 (48.5 KiB)
          Interrupt:185 Base address:0x8000

3) To connect to VPN I use 'pptpconfig' tool, but there's no option which could be used by me (I've tried every option) to connect to the Internet.

You are my last chance to have my Ubuntu 'networked'...

---

