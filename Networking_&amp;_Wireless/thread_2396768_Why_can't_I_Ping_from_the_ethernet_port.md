---
title: "Why can't I Ping from the ethernet port?"
date: 2018-07-20
forum: Networking &amp; Wireless
---

### Post by kazakore on 2018-07-20
Pinging usually works fine, it does from the WiFi anyway. But I don't seem to be able to get it to do so through the ethernet connection, whether I specify it or if I disable everything else to force it.

```
$ ping -I enp0s25 10.42.0.81
PING 10.42.0.81 (10.42.0.81) from 10.42.0.1 enp0s25: 56(84) bytes of data.
^C
--- 10.42.0.81 ping statistics ---
204 packets transmitted, 0 received, 100% packet loss, time 207848ms

```

But I managed to get a point2point nmap to work as PoC.
```
$ nmap -T5  -v -e enp0s25 -sn 10.42.0.0/24

Starting Nmap 7.60 ( https://nmap.org ) at 2018-07-20 15:13 BST
Initiating Ping Scan at 15:13
Scanning 256 hosts [2 ports/host]
Completed Ping Scan at 15:13, 1.75s elapsed (256 total hosts)
Initiating Parallel DNS resolution of 256 hosts. at 15:13
Completed Parallel DNS resolution of 256 hosts. at 15:13, 0.00s elapsed
Nmap scan report for 10.42.0.0 [host down]
Nmap scan report for ThisOne (10.42.0.1)
Host is up (0.00026s latency).
Nmap scan report for 10.42.0.2 [host down]

--snip--

Nmap scan report for 10.42.0.81
Host is up (0.0018s latency).
Nmap scan report for 10.42.0.82 [host down]

--snip--

Read data files from: /usr/bin/../share/nmap
Nmap done: 256 IP addresses (2 hosts up) scanned in 1.76 seconds
```

---

