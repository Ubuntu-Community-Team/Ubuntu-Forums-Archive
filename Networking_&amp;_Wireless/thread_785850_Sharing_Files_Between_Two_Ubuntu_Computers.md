---
title: "Sharing Files Between Two Ubuntu Computers"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by rizlmilk on 2008-05-07
I have a laptop and a desktop. I want to store the majority of my files on the desktop, and carry essential files on my laptop. I want to essentially use my desktop as a server, not having a monitor, keyboard, or mouse hooked up. I would just like to plug my laptop into the desktop via an Ethernet cable and swap files as I wish.

I have NFS and SMB sharing on both computers, and have tried setting up connections with both. What it does is my Desktop can view its files over the network, and the laptop can see its files, but they cannot see each other's.

I've read every possible post on the subject, and anything online that I could find. Everything either doesn't make much sense to me, or is outdated and tells me to download things that aren't in existence or are included in things I already have.

I'm kind of taken back by the fact that when you connect two Ubuntu machines it doesn't just automatically work. I just don't understand why it doesn't.

Any help would be greatly appreciated.

---

### Post by superprash2003 on 2008-05-07
firstly, are the two pcs able to ping each other?

---

### Post by Kralizec on 2008-05-07
I'm having the same issue. And yes, I can ping between the computers.

---

### Post by rizlmilk on 2008-05-07
I'm not sure how I can tell if they ping each other. Is there a command in the terminal I can try to find out?

---

### Post by Kralizec on 2008-05-07
You need to know the IPs of the computers, which you can find out by running ifconfig in a terminal. Result:
```
Link encap:Ethernet  HWaddr 00:14:a5:e5:00:3c  
          inet addr:**192.168.0.102**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fee5:3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44553620 (42.4 MB)  TX bytes:3088048 (2.9 MB)
          Interrupt:18 Memory:c0300000-c0304000 
```
In bold is the IP address.

At first computer: ping <ip of second computer>
At second computer: ping <ip of first computer>

A positive result will look something like this:
```
PING www.l.google.com (64.233.169.147) 56(84) bytes of data.
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=1 ttl=244 time=16.3 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=2 ttl=244 time=17.0 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=3 ttl=244 time=15.5 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=4 ttl=244 time=21.7 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
```

Negative result:
```
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.
From 192.168.0.102 icmp_seq=1 Destination Host Unreachable
From 192.168.0.102 icmp_seq=2 Destination Host Unreachable
From 192.168.0.102 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.3 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3007ms
, pipe 3
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.
From 192.168.0.102 icmp_seq=1 Destination Host Unreachable
From 192.168.0.102 icmp_seq=2 Destination Host Unreachable
From 192.168.0.102 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.3 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3007ms
, pipe 3
```

---

### Post by LastHylian on 2008-05-07
Same here. I would like to know, but previous attempts at setting up SAMBA and NFS were disastrous. I'm somewhat of a n00b when it comes to those, so if someone could discuss that here for general knowledge and a foundation, I would greatly appreciate it. ^_^

BTW:


My Laptop : Ubuntu Hardy Heron 8.04
My Desktop: Ubuntu Feisty Fawn 7.04

Both able to ping each other.

---

### Post by superprash2003 on 2008-05-08
kralizec is right on how to ping .. just type ping (ip) ... you need to try this on both the pcs.. 

@lasthylian
try the samba guide over here [http://ubuntuguide.org](http://ubuntuguide.org) ...

---

