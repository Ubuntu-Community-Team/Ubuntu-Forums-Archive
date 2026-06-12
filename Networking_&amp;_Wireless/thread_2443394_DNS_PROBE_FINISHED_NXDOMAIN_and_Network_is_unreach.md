---
title: "DNS_PROBE_FINISHED_NXDOMAIN and Network is unreachable"
date: 2020-05-15
forum: Networking &amp; Wireless
---

### Post by florestankorp on 2020-05-15
Hi all,
I have a UBEE EVW321B router in my apartment that serves as a signal splitter / switch and receives a signal through an Ethernet port in my wall from the ISP's router downstairs. 

That access point provides internet for six people, who all have the same setup in their homes now. This setup has been working and providing stable internet for two years. All of a sudden we are experiencing connectivity issues and outages both on the cable and wireless networks. There is no scheduled maintenance and I don't think it has anything to do with an increased load on the network due to Coronavirus and people working from home, which was a theory my neighbors had for a while. 

[B]Error shown in browser: DNS_PROBE_FINISHED_NXDOMAIN
[/B]
[B]Steps taken: 
[/B]1. Restarting access point multiple times
2. Restarting my own network switch aka UBEE router multiple times
3. Reseting UBEE router to factory settings
3. Restarting Network manager on Ubuntu 20.04 through hardware but also through GUI @ [B]192.168.178.1
[/B](So I know my routers IP works sometimes)
4. Followed this [blog]([https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking))

[B]Output below:
[/B]
```

&#10140;  ~ ip addr                 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet [127.0.0.1/8]("http://127.0.0.1/8") scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether f0:79:59:62:27:6f brd ff:ff:ff:ff:ff:ff
    inet6 2001:1c00:e13:bf00:a868:7c0c:611e:1c7b/64 scope global temporary dynamic 
       valid_lft 41459sec preferred_lft 12659sec
    inet6 2001:1c00:e13:bf00:8179:e459:9d1e:6285/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 41459sec preferred_lft 12659sec
    inet6 fe80::fe60:fbd6:cbc9:4f46/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
       
&#10140;  ~ route -n                
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

&#10140;  ~ ping 192.168.178.1
ping: connect: Network is unreachable

&#10140;  ~ ping 8.8.8.8
ping: connect: Network is unreachable

&#10140;  ~ ping [google.com]("http://google.com")
PING [google.com]("http://google.com")([ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e)) 56 data bytes
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=1 ttl=53 time=12.2 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=2 ttl=53 time=12.4 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=3 ttl=53 time=17.7 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=4 ttl=53 time=9.35 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=5 ttl=53 time=26.0 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=6 ttl=53 time=17.4 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=7 ttl=53 time=11.1 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=8 ttl=53 time=10.2 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=9 ttl=53 time=9.78 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=10 ttl=53 time=11.0 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=11 ttl=53 time=9.82 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=12 ttl=53 time=10.6 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=13 ttl=53 time=9.09 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=14 ttl=53 time=9.89 ms
64 bytes from [ams15s40-in-x0e.1e100.net]("http://ams15s40-in-x0e.1e100.net") (2a00:1450:400e:80d::200e): icmp_seq=15 ttl=53 time=10.5 ms
^C
--- [google.com]("http://google.com") ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 14021ms
rtt min/avg/max/mdev = 9.089/12.460/25.988/4.425 ms

```
[B]Then after running 

[/B]```

&#10140;  ~ sudo service network-manager restart

&#10140;  ~ route -n                            
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```
[B]AND THEN!!!

[/B]```

&#10140;  ~ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    20100  0        0 enp3s0
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

```
[B]But after five minutes back to the same story:

[/B]```

&#10140;  ~ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

&#10140;  ~ netstat -nr                                
Kernel IP routing table 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

```

---

### Post by webaake on 2020-05-15
I don't see that your PC has an IPv4 address above. It should have. Do you do DHCP (Dynamic IP)? I guess so. Try static IP instead on your PC.

Is your BBE router also getting an IP from the ISP? Try static IP on that too. Yes, all static IP's on your side might mess upp your neighbors IP's but it is for error searching only.

My primary guess is that it is hardware failure due to heat, poor quality or somesuch, on your common router. They do wear out sometimes.

---

