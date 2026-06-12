---
title: "Create static route with netplan"
date: 2022-12-06
forum: Networking &amp; Wireless
---

### Post by anoch on 2022-12-06
[COLOR=#1A1A1A][FONT=&amp]Hi all.Ubuntu 20.04 here.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]Have a task, to add route with netplan. Send packets to 8.8.8.8 through 4.4.4.4.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]I can explain it more clearly by example:[/FONT][/COLOR]
```
ping 8.8.8.8 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 
IP icmp_seq=1 Destination Host Unreachable

```[COLOR=#1A1A1A][FONT=&amp]but others should not be affected[/FONT][/COLOR]
```
ping google.com PING google.com (216.58.206.206): 
56 data bytes 64 bytes from 216.58.206.206: icmp_seq=0 ttl=112 time=62.656 ms 64 bytes 
from 216.58.206.206: icmp_seq=1 ttl=112 time=60.827 ms

```[COLOR=#1A1A1A][FONT=&amp]I tried to go through the [examples]("https://netplan.io/examples") in official documentation, but it's not helped me. My 50-cloud-init.yaml[/FONT][/COLOR]
```
network:
  version: 2
  ethernets:
    eth0:
      addresses: [172.31.42.247/20, 8.8.8.0/8]
      gateway4: 172.31.32.1
      dhcp4: no
      nameservers:
        addresses: [8.8.4.4, 8.8.8.8]
        search: []
      routes:
      - to: 8.8.8.8/32
        via: 4.4.4.4
        metric: 100

```[COLOR=#1A1A1A][FONT=&amp]it gave me almost need result with ping [8.8.8.8]("https://8.8.8.8/"), but ping [google.com]("https://google.com/") gave me[/FONT][/COLOR]
```
ping: google.com: Temporary failure in name resolution

```[COLOR=#1A1A1A][FONT=&amp]Please help me, what im doing wrong? I assume that my cat is completely incorrect and works out by accident :)[/FONT][/COLOR]

---

### Post by TheFu on 2022-12-08
If 4.4.4.4 isn't a router, this won't work.

---

