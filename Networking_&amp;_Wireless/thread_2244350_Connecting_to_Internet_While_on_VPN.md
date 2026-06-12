---
title: "Connecting to Internet While on VPN"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by beenny on 2014-09-15
Hello,

I have seen this problem with others but the solutions haven't worked for me yet. I'm hard wired into my (new) university network (ethernet). When I activate the VPN (to go into a different (old) university network where I server exists I need to use), I connect with no trouble. However I can no longer access the internet. I think this problem is specific to the new university network b/c I never before had trouble with the VPN before.

I have tried this solution:

```

1. Open Network connection and click on VPN tab.
2. Click on VPN to be configured.
3. Now click on Edit
4. Go to IPV4 Settings
5. Click on Routes button
6. Now check the box in front of the text "Use the connections only for the resources on its network" (This will solve the problem of breakage of your internet connection)
```

But it has not worked. 

Any thoughts would be appreciated.

Also, results from:

ifconfig
route -n
cat /etc/resolv.conf
ping -c3 91.189.94.186
ping -c3 ubuntuforums.com

which I saw another thread ask for with and without VPN are:

with:
```

[WorkLap: Mon Sep 15 ~]$ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:79:f7:2c  
          inet addr:10.152.3.187  Bcast:10.152.3.255  Mask:255.255.252.0
          inet6 addr: fe80::f2de:f1ff:fe79:f72c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:251277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:187174576 (187.1 MB)  TX bytes:18705431 (18.7 MB)
          Interrupt:20 Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1205340 (1.2 MB)  TX bytes:1205340 (1.2 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:171.66.16.43  P-t-P:171.66.16.43  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:361912 (361.9 KB)  TX bytes:37451 (37.4 KB)

wlan0     Link encap:Ethernet  HWaddr 64:80:99:3d:0d:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:121859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95635384 (95.6 MB)  TX bytes:29747756 (29.7 MB)

wmx0      Link encap:Ethernet  HWaddr 00:1d:e1:4a:3b:2b  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[WorkLap: Mon Sep 15 ~]$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.152.0.1      0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 tun0
10.152.0.0      0.0.0.0         255.255.252.0   U     1      0        0 eth0
128.12.0.0      0.0.0.0         255.255.0.0     U     0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
171.64.0.0      0.0.0.0         255.252.0.0     U     0      0        0 tun0
171.66.1.253    10.152.0.1      255.255.255.255 UGH   0      0        0 eth0
171.66.16.0     0.0.0.0         255.255.252.0   U     0      0        0 tun0
172.16.0.0      0.0.0.0         255.240.0.0     U     0      0        0 tun0
172.18.0.0      0.0.0.0         255.254.0.0     U     0      0        0 tun0
172.20.0.0      0.0.0.0         255.252.0.0     U     0      0        0 tun0
172.24.0.0      0.0.0.0         255.252.0.0     U     0      0        0 tun0
192.168.8.0     0.0.0.0         255.255.252.0   U     0      0        0 tun0
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 tun0
192.168.208.0   0.0.0.0         255.255.240.0   U     0      0        0 tun0
192.168.211.0   0.0.0.0         255.255.255.0   U     0      0        0 tun0
192.168.220.0   0.0.0.0         255.255.255.224 U     0      0        0 tun0
204.63.224.0    0.0.0.0         255.255.248.0   U     0      0        0 tun0
[WorkLap: Mon Sep 15 ~]$cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search stanford.edu dhe.duke.edu duhs.duke.edu mc.duke.edu
[WorkLap: Mon Sep 15 ~]$ping -c3 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
64 bytes from 91.189.94.186: icmp_req=1 ttl=48 time=83.1 ms
64 bytes from 91.189.94.186: icmp_req=2 ttl=48 time=82.5 ms
64 bytes from 91.189.94.186: icmp_req=3 ttl=48 time=82.6 ms

--- 91.189.94.186 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 82.566/82.797/83.178/0.358 ms
[WorkLap: Mon Sep 15 ~]$ping -c3 ubuntuforums.com
ping: unknown host ubuntuforums.com

```

without vpn:

```

[WorkLap: Mon Sep 15 ~]$ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:79:f7:2c  
          inet addr:10.152.3.187  Bcast:10.152.3.255  Mask:255.255.252.0
          inet6 addr: fe80::f2de:f1ff:fe79:f72c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:186700185 (186.7 MB)  TX bytes:18597726 (18.5 MB)
          Interrupt:20 Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1193255 (1.1 MB)  TX bytes:1193255 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 64:80:99:3d:0d:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:121859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95635384 (95.6 MB)  TX bytes:29747756 (29.7 MB)

wmx0      Link encap:Ethernet  HWaddr 00:1d:e1:4a:3b:2b  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[WorkLap: Mon Sep 15 ~]$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.152.0.1      0.0.0.0         UG    0      0        0 eth0
10.152.0.0      0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
[WorkLap: Mon Sep 15 ~]$cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search dhe.duke.edu duhs.duke.edu mc.duke.edu
[WorkLap: Mon Sep 15 ~]$ping -c3 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
64 bytes from 91.189.94.186: icmp_req=1 ttl=48 time=83.0 ms
64 bytes from 91.189.94.186: icmp_req=2 ttl=48 time=82.7 ms
64 bytes from 91.189.94.186: icmp_req=3 ttl=48 time=82.7 ms

--- 91.189.94.186 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 82.737/82.848/83.069/0.367 ms
[WorkLap: Mon Sep 15 ~]$ping -c3 ubuntuforums.com
PING ubuntuforums.com (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=48 time=83.2 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=48 time=82.4 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=48 time=83.0 ms

--- ubuntuforums.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 82.443/82.892/83.217/0.467 ms

```

cheers,

bg

---

### Post by beenny on 2014-09-18
Just curious if there were any thoughts on this...

bg

---

### Post by sp40140 on 2014-09-18
I have this same issue on Windows. After quick look on internet, I think it's intentional behavior of VPN.

---

### Post by SeijiSensei on 2014-09-18
1) It's ubuntuforums.**org**, not .com, which explains the "unknown host" error.

2) The routing table specifies 10.152.0.1 as the default gateway in both instances, so you should be able to route traffic to the Internet.

3) Try installing **traceroute** on your machine, then run the command "traceroute -n 8.8.8.8" to see where along the path the connection stops. (The "-n" switch disables attempts to resolve IP addresses to host/network names. 8.8.8.8 is the address of Google's main DNS server.)

4) One thing you might try is removing the route to 10.0.0.0.  In principle, this shouldn't matter because you have a route specified for 10.152.0.0 as well, but see if removing it helps. Try using the command

```
sudo ip route del 10.0.0.0/8 dev tun0
```

to delete it.

---

### Post by beenny on 2014-09-19
Seiji,

Thank you for the reply. There does seem to be a difference in traceroute:

> **SeijiSensei said:**
> 
3) Try installing **traceroute** on your machine, then run the command "traceroute -n 8.8.8.8" to see where along the path the connection stops. (The "-n" switch disables attempts to resolve IP addresses to host/network names. 8.8.8.8 is the address of Google's main DNS server.)


This is traceroute without VPN

```

[WorkLap: Fri Sep 19 ~]$traceroute -n 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  10.152.0.2  0.478 ms  0.510 ms  0.514 ms
 2  10.41.0.18  0.481 ms  0.497 ms  0.507 ms
 3  10.0.0.153  0.473 ms  0.488 ms  0.726 ms
 4  192.168.50.86  3.765 ms  4.000 ms  3.341 ms
 5  152.3.219.229  5.108 ms  5.132 ms  4.755 ms
 6  128.109.70.13  5.116 ms  4.205 ms  4.206 ms
 7  128.109.9.70  6.945 ms  6.891 ms  6.929 ms
 8  72.14.202.138  10.915 ms  10.598 ms  10.929 ms
 9  209.85.242.142  11.222 ms 209.85.242.140  9.495 ms  32.450 ms
10  72.14.236.152  9.635 ms 72.14.236.148  9.874 ms 72.14.236.98  10.498 ms
11  66.249.95.197  17.660 ms  17.471 ms 66.249.95.231  32.804 ms
12  72.14.234.55  17.249 ms 72.14.234.67  16.710 ms 72.14.234.55  17.318 ms
13  * * *
...
30  * * *

```

and with VPN

```

1  10.152.0.2  0.638 ms  0.665 ms  0.668 ms
 2  * * *
 3  * * *
 4  192.168.50.86  2.929 ms  2.921 ms  2.619 ms
 5  152.3.219.229  2.902 ms  2.904 ms  4.463 ms
 6  128.109.70.13  4.463 ms  3.121 ms  3.742 ms
 7  128.109.9.70  5.009 ms  6.558 ms  6.248 ms
 8  72.14.202.138  9.397 ms  9.323 ms  9.373 ms
 9  209.85.242.140  9.837 ms 209.85.242.142  9.232 ms 209.85.242.140  9.526 ms
10  72.14.236.98  10.649 ms 72.14.236.152  9.464 ms  9.496 ms
11  66.249.95.197  17.452 ms  17.495 ms 64.233.174.11  17.439 ms
12  72.14.234.55  17.462 ms  17.786 ms 72.14.234.65  16.480 ms
13  * * *
...
30  * * *

```

> **SeijiSensei said:**
> 
4) One thing you might try is removing the route to 10.0.0.0.  In principle, this shouldn't matter because you have a route specified for 10.152.0.0 as well, but see if removing it helps. Try using the command

```
sudo ip route del 10.0.0.0/8 dev tun0
```

to delete it.
tun0 doesn't seem to exist
```
~]$sudo ip route del 10.0.0.0/8 dev tun0
Cannot find device "tun0"
```

If this is something I can internally resolve that would be great b/c I'm certain my IT people will not know what to do...

---

### Post by SeijiSensei on 2014-09-19
When the VPN is active, there should be a tun0 device.  It appears in the results from ifconfig and route you posted earlier with the VPN up.

From my machine, a traceroute times out briefly at another Google machine, 72.14.234.67, then eventually gets to 8.8.8.8.  

The traceroute indicates you can get out to the public Internet with or without the VPN in use, so I don't really know what the problem might be.  I'd give the IT people a call.

---

### Post by beenny on 2014-09-19
Ah - I was able to delete the route with the VPN running.

So that actually solved the problem. Is this something that I will need to do every time I start the VPN? Is there a way to make that a permanent fix?

Thanks,

bg

---

### Post by SeijiSensei on 2014-09-19
Glad that fixed the problem!  Making it permanent  depends on where the route is set up.  

If it's part of your client configuration, you can remove it there.  

If the route is pushed to you by the VPN server, then you might be able to add a line to your client configuration that deletes the route after the tunnel is established.  With OpenVPN, for instance, you can include a directive ("[--up]("http://openvpn.net/index.php/open-source/documentation/manuals/65-openvpn-20x-manpage.html")") that runs a script once the connection is made.  I use that feature to add routes that use the VPN to reach other locations.  If your VPN client software has a similar facility, you could use it to run the command that deletes the route to 10/8 when the tunnel starts up.  It's likely this script runs as root, so don't include "sudo" at the beginning of the "ip route" command.

Otherwise, you could "wrap" the command that starts the VPN in a simple shell script like this:
```

#!/bin/sh

DEL_ROUTE="10.0.0.0/8"
TUN_IF="tun0"

/path/to/whatever_starts_your_vpn_client

/sbin/ip route del $DEL_ROUTE dev $TUN_IF

exit 0

```
Any commands that change routing will have to run with root privileges of course.  OpenVPN starts as root so it can create and configure the tun interface and add or delete routes, but it then switches ownership of the process that manages the tunnel to an anonymous user, usually "nobody."

---

### Post by beenny on 2014-09-19
thanks - for the time being i just made a little alias - FIXVPN that runs the command...

much appreciated

bg

---

