---
title: "How-To: Create route between 2 interfaces"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2007-08-18
HELP!!!

My network setup figure available at:-

[http://www.geocities.com/fy_heng/Network.JPG](http://www.geocities.com/fy_heng/Network.JPG) [Please ZooM for clearer image]

Overall I am building an simple access point. 

**1. IP Forwarding part:**

> echo 1 > /proc/sys/net/ipv4/ip_forward

> cd /etc/sysctl.conf
net.ipv4.conf.forwarding=1

**2. Routing Table in Linux based Box:**

> root@heng:/home/heng# route -n 
Kernel IP routing table 
Destination     Gateway         Genmask              Flags Metric Ref    Use    Iface 
219.93.218.177  0.0.0.0         255.255.255.255   UH    0      0        0        ppp0 
192.168.20.0    0.0.0.0         255.255.255.0        U     0      0        0         ath0 
192.168.10.0    0.0.0.0         255.255.255.0        U     0      0        0         eth0 
0.0.0.0             0.0.0.0         0.0.0.0                  U     0      0        0         ppp0

**3. Windows based Desktop side:**

From the figures, the **Windows based Desktop** is connected to the access point (AP) through static configuration at **IP = 192.168.20.3 / 24, GW = 192.168.20.2**. It _not able_ to surf net. From **Windows prompt**, it able to ping all the interfaces at the **Linux based Box**, it able to **ping** 192.168.20.3 (itself), 192.168.20.2 and 192.168.10.2. It mean there are a connectivity at a whole. 

**4. Linux based Box side:**

From the figures, the laptop have 2 interfaces. One is **ath0** that configured as an access point and **eth0** is a Ethernet that connect to my home ADSL. It _able_ to surf net. From the laptop itself, I able to **ping** 192.168.10.2 and 192.168.20.2. I able to ping 192.168.20.3 (the client Windows based desktop). 

> root@heng:/home/heng# **ping 192.168.10.2** 
PING 192.168.10.2 (192.168.10.2) 56(84) bytes of data. 
64 bytes from 192.168.10.2: icmp_seq=1 ttl=64 time=0.083 ms 
64 bytes from 192.168.10.2: icmp_seq=2 ttl=64 time=0.107 ms 
64 bytes from 192.168.10.2: icmp_seq=3 ttl=64 time=0.069 ms

r> oot@heng:/home/heng# **ping 192.168.20.2** 
PING 192.168.20.2 (192.168.20.2) 56(84) bytes of data. 
64 bytes from 192.168.20.2: icmp_seq=1 ttl=64 time=0.080 ms 
64 bytes from 192.168.20.2: icmp_seq=2 ttl=64 time=0.072 ms 
64 bytes from 192.168.20.2: icmp_seq=3 ttl=64 time=0.073 ms

> root@heng:/home/heng# **ping 192.168.20.3** 
PING 192.168.20.3 (192.168.20.3) 56(84) bytes of data. 
64 bytes from 192.168.20.2: icmp_seq=1 ttl=64 time=0.080 ms 
64 bytes from 192.168.20.2: icmp_seq=2 ttl=64 time=0.072 ms 
64 bytes from 192.168.20.2: icmp_seq=3 ttl=64 time=0.073 ms

I able to ping from both side successfully!  But in the Windows Routing table, it don't have the entry of 192.168.10.0.

But the Windows Box (192.168.20.3) still not able to use the Internet connection which provide by the ADSL. How ya? To enable NAT/IP Masqurade?

Someone please assist.

---

