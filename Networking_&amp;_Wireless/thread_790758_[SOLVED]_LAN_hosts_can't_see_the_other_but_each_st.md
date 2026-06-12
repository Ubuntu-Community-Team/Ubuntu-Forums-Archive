---
title: "[SOLVED] LAN hosts can't see the other but each still have Internet."
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2008-05-11
Just a few months back I could play with nmap in order to see the other hosts on my LAN.  But now when I run nmap or a simple ping to a neighbouring host there's no connectivity.  Yet each host where one of them is a Windows machine can reach the Internet without problems.
I went through the router settings but everything seems to be OK and I've disabled all port rules for every host on the LAN still nothing. :confused:

Also I pinged the router and I don't get any response.  Still I can talk to you guys on the Internet. :confused: Also I did this but no difference.
> bill@gates:~$ sudo route add default gw 192.168.0.1
Password:
SIOCADDRT: File exists



Got any tips for me?

---

### Post by superprash2003 on 2008-05-11
have firestarter or anything similar installed?

---

### Post by jingo811 on 2008-05-12
Thanks that pinpointed the problem for me X-File closed.  The MoBlock guys must've increased security with their latest upgrade.  Still it's weird that it's possible to deny ping to Default Gateway while you still can ping Internet like [www.google.com](www.google.com).

```
bill@gates:~$ **sudo moblock-control stop**
[sudo] password for bill:
Stopping MoBlock   ...done.

bill@gates:~$ **ping -c 3 192.168.0.1**
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.967 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.969 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.03 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.967/0.990/1.035/0.040 ms


```

---

