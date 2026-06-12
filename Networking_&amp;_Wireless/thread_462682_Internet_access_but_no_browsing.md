---
title: "Internet access but no browsing"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by OzRob on 2007-06-02
I have installed 6.10 and am unable to access web pages using Firefox.
If I try to access [www.google.com](www.google.com) (for example) I will eventually get a Timed out message.
I have a standalone machine accessing the internet through D-Link DSL-502T router modem.
Below is my ifconfig:
rob@blackie:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:00:03:C5  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::214:85ff:fe00:3c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12246 (11.9 KiB)  TX bytes:139383 (136.1 KiB)
          Interrupt:217 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:676 (676.0 b)  TX bytes:676 (676.0 b)

If I ping google it seems to respond fine. (See below)

rob@blackie:~$ ping -c 10 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (72.14.253.103) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=1 ttl=241 time=197 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=2 ttl=241 time=198 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=3 ttl=241 time=197 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=4 ttl=241 time=195 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=5 ttl=241 time=195 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=6 ttl=241 time=196 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=7 ttl=241 time=194 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=8 ttl=241 time=195 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=9 ttl=241 time=195 ms
64 bytes from [www.google.com](www.google.com) (72.14.253.103): icmp_seq=10 ttl=241 time=195 ms

--- [www.google.com](www.google.com) ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9021ms
rtt min/avg/max/mdev = 194.232/196.008/198.128/1.241 ms

A traceroute to google doesn't work although it does make 6 hops before ending with no reply.

---

### Post by OzRob on 2007-06-03
Issue fixed. It was related to ipv6
I went into Firefox. put in 'about:config'
filtered by ipv6.
Set network.dns.disableIPV6 to true and away we go.

---

