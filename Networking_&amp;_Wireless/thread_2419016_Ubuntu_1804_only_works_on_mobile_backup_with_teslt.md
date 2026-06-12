---
title: "Ubuntu 1804 only works on mobile backup with tesltra smart modem"
date: 2019-05-15
forum: Networking &amp; Wireless
---

### Post by uncleBez on 2019-05-15
I have an ubuntu 1804 laptop connected to internet via telstra cable.

So the setup is that there is a 'telstra cable adaptor' plugged into the cable socket in the wall.
A telstra smart modem plugged into the telstra cable adaptor.

Current situation is that everything works, laptop browses the internet fine when I unplug the cable adapter and let the smart modem switch to 'mobile data' mode.
But when connected to the internet via the 'cable adaptor' the laptop will have connectivity for a very short time.. and then not.

The first webpage I open loads (usually), but anything after that just either says "connecting...." or "resolving host...."

Then over time, sometimes part of a page loads, but usually not.

NOW.. the Interesting thing is that my mobile works over WIFI in both scenarios, using mobile backup mode or the cable adaptor.. go figure!

Also, the interesting part, is that if I browse to the router 192.168.0.1 I get 'connection refused'.
But I can ping it and also browse to it via my mobile phone.

I have spent hours chatting to telstra support and they've escalated the issue.. but since the mobile works I'm suspecting some configuration issue on my laptop.

more information is that this was working until the other day, I contaced them and they said I was barred.. my mobile wouldn't connect either.. they unbarred the service and 24hours later i'm in this current situation.. the mobile phone connects to internet over wifi but the laptop does not.

they have done all the usual things, reboot the router, reset the router, etc etc..

I'm hoping someone here might have experience the same issue, or has enough smarts to give me an idea..

I thought perpaps docker's networking was interfering so I disable the docker service and deleted all the br-* interfaces, docker0 and lxcbr

Here's some system info:

```
$ ifconfig
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
inet 192.168.0.6  netmask 255.255.255.0  broadcast 192.168.0.255
inet6 fe80::e866:7410:db2e:2e0d  prefixlen 64  scopeid 0x20<link>
ether e8:6a:64:4f:be:b3  txqueuelen 1000  (Ethernet)
RX packets 1018  bytes 169893 (169.8 KB)
RX errors 0  dropped 0  overruns 0  frame 0
TX packets 1447  bytes 198586 (198.5 KB)
TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
device interrupt 16  memory 0xe8200000-e8220000

$ lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
inet 127.0.0.1  netmask 255.0.0.0
inet6 ::1  prefixlen 128  scopeid 0x10<host>
loop  txqueuelen 1000  (Local Loopback)
RX packets 7346  bytes 1494150 (1.4 MB)
RX errors 0  dropped 0  overruns 0  frame 0
TX packets 7346  bytes 1494150 (1.4 MB)
TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

$ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp0s31f6
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s31f6
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s31f6
$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.095 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.111 ms
^C
--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.095/0.103/0.111/0.008 ms
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

$ ^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3005ms
$
```

I've disable DHCP on the router, and then reenabled it which has provided the laptop a new IP.
I've connected via both ethernet and via wifi.

I also have relevant logs when attempting to enable the ethernet interface in pastebin here: [https://pastebin.com/uDdWQjbL](https://pastebin.com/uDdWQjbL)

I don't know if this really is a linux issue, or a telstra issue or what.. But if someone can offer me anything I'll gladly take the input.. 
this may need posting elsewhere, but since it works on mobile back up but not on cable.. well it's a broadband issues i suppose

```
Also, here is the output of traceroute to 8.8.8.8, and shows it never gets a single hop.

$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
1  * * *
2  * * *
3  * * *
4  * * *
5  * * *
6  * * *
7  * * *
8  * * *
9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
$
```

---

