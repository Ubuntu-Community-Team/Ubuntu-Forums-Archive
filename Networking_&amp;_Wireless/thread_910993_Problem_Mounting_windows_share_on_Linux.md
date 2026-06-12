---
title: "Problem Mounting windows share on Linux"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by ivikas on 2008-09-05
Hello all,

          Iam using Ubuntu 8.04 LTS Desktop and there are eight windows machines.One windows machine has a shared folder and that is inaccessible from my linux machine and so is similar with other machine.i have  a wirless
network.The output of ifconfig is as below

```

root@vikas-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:7a:20:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x20c0 Memory:50300000-50320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1280436 (1.2 MB)  TX bytes:1280436 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:2c:dc:f9  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fe2c:dcf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11336 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17933277 (17.1 MB)  TX bytes:1071220 (1.0 MB)
          Interrupt:23 Memory:50000000-50010000 

root@vikas-desktop:~# 

```

The windows machine offering share is at ip address:192.168.1.100 and infact i can ping to it.Here's the ping report

```

root@vikas-desktop:~# ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=128 time=20.5 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=128 time=1.15 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=128 time=1.18 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=128 time=1.99 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=128 time=1.19 ms

--- 192.168.1.100 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 1.152/5.218/20.575/7.685 ms
root@vikas-desktop:~# 
```

The window share is in above Machine,ubuntu is not automatically taking it up,In places->network-windows network is blank.

I tried via ALT+F2 and typed like this smb://192.168.1.100/webmasters,but it says  "Could not open location 'smb://192.168.1.100/webmasters/'

Therefore how can i get windows share over linux.Is there any services that i have to check for and enable.

Please give a fix

Thanks in advance.

---

