---
title: "Port Security Help"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by phimurh on 2007-12-01
Can Someone Help Me Lock This

PORT      STATE SERVICE
1/tcp     open  tcpmux
11/tcp    open  systat
15/tcp    open  netstat
79/tcp    open  finger
111/tcp   open  rpcbind
119/tcp   open  nntp
143/tcp   open  imap
540/tcp   open  uucp
631/tcp   open  ipp
635/tcp   open  unknown
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
6667/tcp  open  irc
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k

Nmap finished: 1 IP address (1 host up) scanned in 0.158 seconds

---

### Post by phimurh on 2007-12-02
From an external scan i received

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-02 10:19 EST
sendto in send_ip_packet: sendto(5, packet, 44, 0, *, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51840 > *1:6667 S ttl=37 id=53084 iplen=44  seq=4058308063 win=2048 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51841 > *1:6667 S ttl=51 id=23268 iplen=44  seq=4058373598 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51842 > *:6667 S ttl=45 id=11489 iplen=44  seq=4058439133 win=2048 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *6) => Operation not permitted
Offending packet: TCP 192.168.0.100:51843 > *:6667 S ttl=39 id=44453 iplen=44  seq=4058504668 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *1, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51840 > *:79 S ttl=42 id=58170 iplen=44  seq=4058308063 win=3072 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, 24.165.181.71, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51841 > *:79 S ttl=39 id=19458 iplen=44  seq=4058373598 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *1, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51842 > *:79 S ttl=50 id=11647 iplen=44  seq=4058439133 win=3072 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51843 > *1:79 S ttl=44 id=48025 iplen=44  seq=4058504668 win=1024 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *.71, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51840 > *:1 S ttl=47 id=12308 iplen=44  seq=4058308063 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, *.71, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51841 > *:1 S ttl=57 id=28110 iplen=44  seq=4058373598 win=2048 <mss 1460>
Omitting future Sendto error messages now that 10 have been shown.  Use -d2 if you really want to see them.
Interesting ports on cpe-**-***-***.**.***.***.**.com (**.***.***.**):
Not shown: 1692 closed ports
PORT     STATE    SERVICE
1/tcp    filtered tcpmux
11/tcp   filtered systat
79/tcp   filtered finger
80/tcp   open     http
6667/tcp filtered irc

Nmap finished: 1 IP address (1 host up) scanned in 6.933 seconds

---

### Post by phimurh on 2007-12-02
How do I find these processes or close these ports

---

### Post by breaking on 2008-01-19
Use a firewall. If you're not confident configuring IPTABLES, use guarddog (a point-and-click frontend to IPTABLES).

---

