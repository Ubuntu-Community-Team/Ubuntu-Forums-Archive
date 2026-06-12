---
title: "Big problem Gutsy 8.0.4 resolv DNS"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by yanayun on 2008-07-11
Big problem in ubuntu 8.0.4 Amd64bit can't skip to second nameserver in file /etc/resolv.com

nameserver aaa.bbb.ccc.ddd
nameserver bbb.ccc.ddd.eee
nameserver ccc.ddd.eee.fff

Ubuntu only read first DNS aaa.bbb.ccc.ddd since this address not active or have problem service dns.
Ubuntu never skip to next nameserver

Try to add inactive nameserver in first line, your network will problem resolv to internet.

---

### Post by chili555 on 2008-07-11
*resolv.conf* times out and moves down fine on my machine:```
chili@LAPTOP60:~$ cat /etc/resolv.conf
nameserver 11.111.111.11
nameserver 192.168.1.254
``````
chili@LAPTOP60:~$ ping -c3 www.yahoo.com
PING www.yahoo-ht3.akadns.net (209.191.93.52) 56(84) bytes of data.
64 bytes from f1.www.vip.mud.yahoo.com (209.191.93.52): icmp_seq=1 ttl=49 time=66.1 ms
64 bytes from f1.www.vip.mud.yahoo.com (209.191.93.52): icmp_seq=2 ttl=49 time=66.2 ms
64 bytes from f1.www.vip.mud.yahoo.com (209.191.93.52): icmp_seq=3 ttl=49 time=59.0 ms

--- www.yahoo-ht3.akadns.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10198ms
rtt min/avg/max/mdev = 59.063/63.821/66.221/3.371 ms
```Can you ping all three nameservers?

---

### Post by yanayun on 2008-07-12
> **chili555 said:**
> *resolv.conf* times out and moves down fine on my machine:```
chili@LAPTOP60:~$ cat /etc/resolv.conf
nameserver 11.111.111.11
nameserver 192.168.1.254
``````
chili@LAPTOP60:~$ ping -c3 www.yahoo.com
PING www.yahoo-ht3.akadns.net (209.191.93.52) 56(84) bytes of data.
64 bytes from f1.www.vip.mud.yahoo.com (209.191.93.52): icmp_seq=1 ttl=49 time=66.1 ms
64 bytes from f1.www.vip.mud.yahoo.com (209.191.93.52): icmp_seq=2 ttl=49 time=66.2 ms
64 bytes from f1.www.vip.mud.yahoo.com (209.191.93.52): icmp_seq=3 ttl=49 time=59.0 ms

--- www.yahoo-ht3.akadns.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10198ms
rtt min/avg/max/mdev = 59.063/63.821/66.221/3.371 ms
```Can you ping all three nameservers?

i can ping all nameserver. i must move second nameserver to first line everytime connect to internet.

---

