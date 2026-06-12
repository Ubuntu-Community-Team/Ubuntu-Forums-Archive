---
title: "Just installed Ubuntu Gnome 15.10 and my network doesn't seem to connect"
date: 2016-04-15
forum: Networking &amp; Wireless
---

### Post by Pieter_Kuijper on 2016-04-15
I've just done a fresh install of Ubuntu Gnome 15.10 and my network doesn't connect at all.


I've updated my driver to the latest version to the best of my abilities (new to linxu, so I hope I've done it right. Followed the readme so I assume so)


All my outputs: [here]("https://gist.github.com/anonymous/7ee6219dfa0e06ef7cfb843e7031a107")

---

### Post by TheFu on 2016-04-15
Welcome to the forums.

Can you ping the router by IP?
Can you ping 8.8.8.8?
Can you lookup google.com?
Troubleshooting: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has specific commands.

---

### Post by Pieter_Kuijper on 2016-04-15
Pinging anything doesn't seem to work. Can't even connect to the router. It tries to connect and then fails and shuts down the wired connection.

---

### Post by TheFu on 2016-04-15
Please post the exact ping command used.  The e1000e driver is extremely stable, so it is likely a cable or port issue.  The fact that a GigE connection is only reporting a 100-base-t connection is also odd to me.  Is the router/switch only 100base-t?  Check the cable and try a different port.

To get the fastest help, best to always show the exact command AND the output, using "code tags" so things line up.
For example, 
```
$ ping 172.22.22.1
PING 172.22.22.1 (172.22.22.1) 56(84) bytes of data.
64 bytes from 172.22.22.1: icmp_seq=1 ttl=64 time=1.48 ms
64 bytes from 172.22.22.1: icmp_seq=2 ttl=64 time=0.745 ms
64 bytes from 172.22.22.1: icmp_seq=3 ttl=64 time=0.779 ms

$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=45 time=14.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=45 time=13.3 ms

```
Telling us the result isn't the same, since often we don't know what we don't know and misinterpret the results.  It also helps less experienced people to see the steps and results.

Is the system using static IPs or DHCP?
Output from **ifconfig** and **route**, please. No options needed.

---

### Post by Pieter_Kuijper on 2016-04-16
The message did surprisingly change overnight to it can connect. But still no actual internet connection.
Here are my results from ifconfig/route and ping
```

eno1      Link encap:Ethernet  HWaddr bc:ee:7b:73:6e:8a  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beee:7bff:fe73:6e8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14199 (14.1 KB)  TX bytes:157302 (157.3 KB)
          Interrupt:20 Memory:f7200000-f7220000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1527190 (1.5 MB)  TX bytes:1527190 (1.5 MB)



```
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
link-local      *               255.255.0.0     U     1000   0        0 eno1
192.168.1.0     *               255.255.255.0   U     100    0        0 eno1



```
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.17 icmp_seq=1 Destination Host Unreachable
From 192.168.1.17 icmp_seq=2 Destination Host Unreachable
From 192.168.1.17 icmp_seq=3 Destination Host Unreachable
From 192.168.1.17 icmp_seq=4 Destination Host Unreachable
From 192.168.1.17 icmp_seq=5 Destination Host Unreachable


--- 8.8.8.8 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4024ms
pipe 3



```

---

### Post by TheFu on 2016-04-16
**ping 192.168.1.1 **
fails?  If so, then check the cable and the port. All the other settings seem reasonable.  I asked a few other questions. Answers please?

---

### Post by Pieter_Kuijper on 2016-04-16
I'm running my internet through a 1gb switch, tried different ports. No changes there. Wired connection does work normally on windows without problems so I doubt it's that. Even swapped out the cable

---

### Post by Pieter_Kuijper on 2016-04-16
Just got some assistance from a friend.
using: ```
sudo route add default gw 192.168.1.1 eno1
``` worked and fixed the problem

---

