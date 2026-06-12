---
title: "Problem with Internet connection"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by habaria on 2008-05-16
Hi I am new in here and I will really appreciate it if anyone can help me out.
I have been struggling for a few days to connect kubunto 8.04 to the internet. I don't have a router and I use a cable modem.
The thing is that I get connected I get an IP address. I even called the ISP technical support and they can see me as connected. But I can't use Firefox or even ping.
this is what I get:

habaria@habaria-desktop:~/Public/cable/scripts$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:17:bb:dc:b3
          inet addr:172.22.210.182  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::216:17ff:febb:dcb3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:201831 (197.1 KB)  TX bytes:8701 (8.4 KB)
          Interrupt:23 Base address:0x6800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:77.127.201.190  P-t-P:212.199.26.110  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:870 (870.0 B)  TX bytes:46 (46.0 B)




habaria@habaria-desktop:~/Public/cable/scripts$ ping [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (213.57.1.13) 56(84) bytes of data.

--- [www.google.com](www.google.com) ping statistics ---
112 packets transmitted, 0 received, 100% packet loss, time 111006ms


Thanks

---

### Post by Iowan on 2008-05-16
I'm a bit confused by settings for eth0 and ppp0. What address does your ISP show you as having - the eth0 (172.22.210.182) or the ppp0 (77.127.201.190 P-t-P:212.199.26.110)? It's possible you may need to "turn off" one or the other.

Or... maybe it's supposed to work that way, and I'm REALLY confused.

---

### Post by habaria on 2008-05-16
The ip address that windows shows me is the 172...
 
Thanks for helping :)

---

