---
title: "Ping reply DUP! error"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by apit on 2007-02-07
hi there..
i'm using ubuntu 6.06 dapper drake
when i ping to my webserver, this is the result :

> 
me@buzz:~$ ping 172.10.30.26
PING 172.10.30.26 (172.10.30.26) 56(84) bytes of data.
64 bytes from 172.10.30.26: icmp_seq=1 ttl=254 time=0.194 ms
64 bytes from 172.10.30.26: icmp_seq=1 ttl=254 time=0.213 ms (DUP!)
64 bytes from 172.10.30.26: icmp_seq=2 ttl=254 time=0.180 ms
64 bytes from 172.10.30.26: icmp_seq=2 ttl=254 time=0.200 ms (DUP!)
64 bytes from 172.10.30.26: icmp_seq=3 ttl=254 time=0.205 ms
64 bytes from 172.10.30.26: icmp_seq=3 ttl=254 time=0.225 ms (DUP!)
64 bytes from 172.10.30.26: icmp_seq=4 ttl=254 time=0.186 ms
64 bytes from 172.10.30.26: icmp_seq=4 ttl=254 time=0.208 ms (DUP!)


i try ping using different device (switch) & the result:
> 
me@buzz:~$ ping 172.10.60.254
PING 172.10.60.254 (172.10.60.254) 56(84) bytes of data.
64 bytes from 172.10.60.254: icmp_seq=1 ttl=63 time=2.40 ms
64 bytes from 172.10.60.254: icmp_seq=1 ttl=63 time=2.44 ms (DUP!)
64 bytes from 172.10.60.254: icmp_seq=2 ttl=63 time=2.88 ms
64 bytes from 172.10.60.254: icmp_seq=2 ttl=63 time=2.90 ms (DUP!)
64 bytes from 172.10.60.254: icmp_seq=3 ttl=63 time=2.05 ms
64 bytes from 172.10.60.254: icmp_seq=3 ttl=63 time=2.08 ms (DUP!)


then i try ping from different vlan with the same device
the result:

> 
me@buzz:~$ ping 172.10.30.26
PING 172.10.30.26 (172.10.30.26) 56(84) bytes of data.
64 bytes from 172.10.30.26: icmp_seq=1 ttl=254 time=0.194 ms
64 bytes from 172.10.30.26: icmp_seq=1 ttl=254 time=0.213 ms 
64 bytes from 172.10.30.26: icmp_seq=2 ttl=254 time=0.180 ms
64 bytes from 172.10.30.26: icmp_seq=2 ttl=254 time=0.200 ms 
64 bytes from 172.10.30.26: icmp_seq=3 ttl=254 time=0.205 ms
64 bytes from 172.10.30.26: icmp_seq=3 ttl=254 time=0.225 ms 
64 bytes from 172.10.30.26: icmp_seq=4 ttl=254 time=0.186 ms
64 bytes from 172.10.30.26: icmp_seq=4 ttl=254 time=0.208 ms 


[B]Question
--------------[/B]

1- Using **man ping**, it said that there was duplicate  and  damaged  packets. How to trace this duplicate  and  damaged  packets?

2-Is it possible that the problem come from faulty device such as router/switch?

3-If i'm using WinXP, the ping result is normal. Why ping result different using Linux & WinXP?

---

### Post by apit on 2007-02-08
answer from others community:

[http://www.freebsdforums.com/forums/showthread.php?t=47441](http://www.freebsdforums.com/forums/showthread.php?t=47441)
[http://www.firewall.cx/ftopict-4104.html](http://www.firewall.cx/ftopict-4104.html)

Any volunters from ubuntu community?

---

