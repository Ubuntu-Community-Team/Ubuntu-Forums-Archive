---
title: "Slow internet connection"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by kag on 2007-02-14
My connection feels really slow. I disabled IPv6 from /etc/modprobe.d/aliases, didn't change anything. My connection is supposed to be 5.1Mbps.

I tried to ping [www.google.com](www.google.com), it was really painful to see these numbers:
> kag@strider:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (72.14.205.104) 56(84) bytes of data.
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=1 ttl=240 time=1711 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=2 ttl=240 time=2245 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=3 ttl=240 time=1815 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=4 ttl=240 time=1916 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=5 ttl=240 time=2185 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=6 ttl=240 time=1815 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=7 ttl=240 time=1968 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=8 ttl=240 time=2298 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=9 ttl=240 time=2640 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=10 ttl=240 time=2019 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=11 ttl=240 time=1527 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=12 ttl=240 time=2025 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=13 ttl=240 time=1606 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=14 ttl=240 time=2089 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=15 ttl=240 time=1692 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=16 ttl=240 time=1411 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=17 ttl=240 time=1730 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=18 ttl=240 time=2088 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
18 packets transmitted, 18 received, 0% packet loss, time 43456ms
rtt min/avg/max/mdev = 1411.659/1932.752/2640.529/296.316 ms, pipe 3


I tried the "dig" command, looking at the query time makes my stomach hurt!
> kag@strider:~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17032
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 13

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       3755    IN      NS      C.ROOT-SERVERS.NET.
.                       3755    IN      NS      G.ROOT-SERVERS.NET.
.                       3755    IN      NS      F.ROOT-SERVERS.NET.
.                       3755    IN      NS      B.ROOT-SERVERS.NET.
.                       3755    IN      NS      J.ROOT-SERVERS.NET.
.                       3755    IN      NS      K.ROOT-SERVERS.NET.
.                       3755    IN      NS      L.ROOT-SERVERS.NET.
.                       3755    IN      NS      M.ROOT-SERVERS.NET.
.                       3755    IN      NS      I.ROOT-SERVERS.NET.
.                       3755    IN      NS      E.ROOT-SERVERS.NET.
.                       3755    IN      NS      D.ROOT-SERVERS.NET.
.                       3755    IN      NS      A.ROOT-SERVERS.NET.
.                       3755    IN      NS      H.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
G.ROOT-SERVERS.NET.     5719    IN      A       192.112.36.4
F.ROOT-SERVERS.NET.     9228    IN      A       192.5.5.241
B.ROOT-SERVERS.NET.     5719    IN      A       192.228.79.201
J.ROOT-SERVERS.NET.     9228    IN      A       192.58.128.30
K.ROOT-SERVERS.NET.     9228    IN      A       193.0.14.129
L.ROOT-SERVERS.NET.     7521    IN      A       198.32.64.12
M.ROOT-SERVERS.NET.     9228    IN      A       202.12.27.33
I.ROOT-SERVERS.NET.     5719    IN      A       192.36.148.17
E.ROOT-SERVERS.NET.     5719    IN      A       192.203.230.10
D.ROOT-SERVERS.NET.     7890    IN      A       128.8.10.90
A.ROOT-SERVERS.NET.     9228    IN      A       198.41.0.4
H.ROOT-SERVERS.NET.     5719    IN      A       128.63.2.53
C.ROOT-SERVERS.NET.     5719    IN      A       192.33.4.12

;; Query time: 1855 msec
;; SERVER: 24.200.241.37#53(24.200.241.37)
;; WHEN: Wed Feb 14 22:51:37 2007
;; MSG SIZE  rcvd: 436


Although I'm not saying it's not the problem, until now I've never really had issues with my ISP's DNS.

Where can I begin to check?

---

### Post by Floppyjoe on 2007-02-14
Here is a Url that may be of help to you:

[http://www.opendns.com/start/](http://www.opendns.com/start/)

---

### Post by kag on 2007-02-14
Thanks, but I get pretty much the same results with those DNS.
> kag@strider:~$ cat /etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220


---

### Post by kag on 2007-02-15
It must have been my ISP that was having problems with the winter storm yesterday. I came back from work today and everything is back to full speed. Thanks for those who helped!

---

