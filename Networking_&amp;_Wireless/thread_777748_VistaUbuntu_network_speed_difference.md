---
title: "Vista/Ubuntu network speed difference"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by darco on 2008-05-01
I saw a thread re: the difference of network speed between Ubuntu and Vista but I cannot locate it.

In Vista running a speedtest I get a whopping 16-25mbs of d/l speed. I have 16mb comcast connection. When I run the same test in Ubuntu HH I get  a measly 5mb download. I have disabled IPV6 and running "ip a | grep inet6" confirms it. I know its not the flash website thats reporting the low speed results because when I d/l via usenet it also seems to cap at 5mb. I am not using the built in FW and I am connected directly to a Linkysys router. I am still using Wubi but that shouldnt be causing any network issue.

Pinging doesnt seem to be an issue

darco@darco-desktop:~$ ping comcast.net
PING comcast.net (216.148.227.202) 56(84) bytes of data.
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=1 ttl=52 time=12.6 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=2 ttl=52 time=11.9 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=3 ttl=52 time=11.6 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=4 ttl=52 time=14.2 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=5 ttl=52 time=12.2 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=6 ttl=52 time=11.9 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=7 ttl=52 time=12.5 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=8 ttl=52 time=16.4 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=9 ttl=52 time=12.2 ms
64 bytes from [www.comcast.net](www.comcast.net) (216.148.227.202): icmp_seq=10 ttl=52 time=12.4 ms

Traceroute looks fine too..

 traceroute [www.comcast.net](www.comcast.net)
traceroute to [www.comcast.net](www.comcast.net) (128.241.220.73), 30 hops max, 40 byte packets
 1  SoCity (192.168.15.2)  0.887 ms  1.169 ms  1.448 ms
 2  73.73.16.1 (73.73.16.1)  7.822 ms  11.972 ms  16.319 ms
 3  ge-4-2-ur02.dalycity.ca.sfba.comcast.net (68.85.216.133)  17.119 ms * *
 4  te-9-3-ur01.dalycity.ca.sfba.comcast.net (68.87.192.1)  16.766 ms * *
 5  pos-0-7-0-0-ar01.sfsutro.ca.sfba.comcast.net (68.86.90.154)  17.824 ms  17.825 ms  20.813 ms
 6  * * COMCAST-IP.edge1.SanJose1.Level3.net (4.79.43.138)  10.612 ms
 7  xe-11-0-0.edge1.SanJose1.Level3.net (4.79.43.137)  12.924 ms  16.594 ms  8.816 ms
 8  ae-2-79.edge1.SanJose3.Level3.net (4.68.18.80)  14.919 ms ae-3-89.edge1.SanJose3.Level3.net (4.68.18.144)  19.764 ms ae-1-69.edge1.SanJose3.Level3.net (4.68.18.16)  20.083 ms
 9  verio-level3-10ge.SanJose1.Level3.net (4.68.111.250)  20.054 ms  20.345 ms  20.341 ms
10  po-4.r03.snjsca04.us.bb.gin.ntt.net (129.250.4.78)  20.774 ms  20.772 ms  20.763 ms
11  128.241.220.73 (128.241.220.73)  21.815 ms  21.810 ms  24.670 ms

Let me know if lspci or lshw -C is needed....
thxs
darco

---

### Post by darco on 2008-05-01
any suggestions?

darco

---

### Post by dream_coder on 2009-04-07
Sounds like we are having the same problem, I am using Jaunty, on Intrepid speed was fine and also windows now with Jaunty my speed has gone from 2500 to 600 or so max of 1000 :( lol if you search for "speed usenet ipv6" you will find my post

---

### Post by superprash2003 on 2009-04-07
post your **ifconfig** output from the terminal

---

### Post by dream_coder on 2009-04-07
use sudo ifconfig check your MTU if its too low

Try changing your MTU! using:

sudo ifconfig <device-eg.eth0> mtu 1500

---

