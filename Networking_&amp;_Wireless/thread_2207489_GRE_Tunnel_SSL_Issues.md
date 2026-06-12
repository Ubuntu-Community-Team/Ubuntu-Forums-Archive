---
title: "GRE Tunnel SSL Issues"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by sandyd on 2014-02-23
I have setup a GRE Tunnel according to the BuyVM Guide [here]("http://wiki.buyvm.net/doku.php/gre_tunnel")

Everything seems to be working so far - except for SSL-Based applications. I can get HTTP, FTP, and a ZNC with SSL disabled working perfectly, but cannot get their SSL counterparts (HTTPS, FTP-TLS, ZNC w/ SSL) working.

Basically, the server does receive the request and perform the TCP Handshake (verified by Telneting into the port), but anything beyond that seems to fail.

* In the below, Public IP of GRE Host is 162.1.1.1, Public IP of GRE Client is 162.1.1.2, Private GRE Network is 192.168.168.0/30
* The below tcpdumps are from one side of the GRE tunnel to another.

HTTPS TCPDump 
```

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
20:38:35.797194 IP 162.1.1.1 > 162.1.1.2: GREv0, length 68: IP 162.1.1.1.57241 > 192.168.168.2.https: Flags [F.], seq 2309922020, ack 967290603, win 113, options [nop,nop,TS val 2741572007 ecr 7095948,nop,nop,sack 1 {1425:2711}], length 0
20:38:35.797431 IP 162.1.1.2 > 162.1.1.1: GREv0, length 56: IP 192.168.168.2.https > 162.1.1.1.57241: Flags [F.], seq 2711, ack 1, win 231, options [nop,nop,TS val 7107188 ecr 2741572007], length 0
20:38:35.826407 IP 162.1.1.1 > 162.1.1.2: GREv0, length 44: IP 162.1.1.1.57241 > 192.168.168.2.https: Flags [R], seq 2309922021, win 0, length 0
20:38:42.226492 IP 162.1.1.1 > 162.1.1.2: GREv0, length 64: IP 162.1.1.1.57693 > 192.168.168.2.https: Flags [S], seq 3457710687, win 14360, options [mss 1436,sackOK,TS val 2741578437 ecr 0,nop,wscale 7], length 0
20:38:42.226561 IP 162.1.1.2 > 162.1.1.1: GREv0, length 64: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [S.], seq 2548843531, ack 3457710688, win 28480, options [mss 1436,sackOK,TS val 7108796 ecr 2741578437,nop,wscale 7], length 0
20:38:42.255712 IP 162.1.1.1 > 162.1.1.2: GREv0, length 56: IP 162.1.1.1.57693 > 192.168.168.2.https: Flags [.], ack 1, win 113, options [nop,nop,TS val 2741578466 ecr 7108796], length 0
20:38:42.255875 IP 162.1.1.1 > 162.1.1.2: GREv0, length 281: IP 162.1.1.1.57693 > 192.168.168.2.https: Flags [P.], seq 1:226, ack 1, win 113, options [nop,nop,TS val 2741578466 ecr 7108796], length 225
20:38:42.255920 IP 162.1.1.2 > 162.1.1.1: GREv0, length 56: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], ack 226, win 231, options [nop,nop,TS val 7108803 ecr 2741578466], length 0
20:38:42.259125 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7108804 ecr 2741578466], length 1424
20:38:42.259140 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1342: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [P.], seq 1425:2711, ack 226, win 231, options [nop,nop,TS val 7108804 ecr 2741578466], length 1286
20:38:42.288782 IP 162.1.1.1 > 162.1.1.2: GREv0, length 68: IP 162.1.1.1.57693 > 192.168.168.2.https: Flags [.], ack 1, win 113, options [nop,nop,TS val 2741578499 ecr 7108803,nop,nop,sack 1 {1425:2711}], length 0
20:38:42.289556 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7108812 ecr 2741578499], length 1424
20:38:42.517575 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7108869 ecr 2741578499], length 1424
20:38:42.973566 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7108983 ecr 2741578499], length 1424
20:38:43.885560 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7109211 ecr 2741578499], length 1424
20:38:45.713578 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7109668 ecr 2741578499], length 1424
20:38:49.369553 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7110582 ecr 2741578499], length 1424
20:38:56.673589 IP 162.1.1.2 > 162.1.1.1: GREv0, length 1480: IP 192.168.168.2.https > 162.1.1.1.57693: Flags [.], seq 1:1425, ack 226, win 231, options [nop,nop,TS val 7112408 ecr 2741578499], length 1424
```

HTTP TCPDump```

20:43:57.661462 IP 162.1.1.1 > 162.1.1.2: GREv0, length 64: IP 162.1.1.1.54803 > 192.168.168.2.http: Flags [S], seq 2566087003, win 14360, options [mss 1436,sackOK,TS val 2741893872 ecr 0,nop,wscale 7], length 0
20:43:57.661558 IP 162.1.1.2 > 162.1.1.1: GREv0, length 64: IP 192.168.168.2.http > 162.1.1.1.54803: Flags [S.], seq 504236509, ack 2566087004, win 28480, options [mss 1436,sackOK,TS val 7187654 ecr 2741893872,nop,wscale 7], length 0
20:43:57.690718 IP 162.1.1.1 > 162.1.1.2: GREv0, length 56: IP 162.1.1.1.54803 > 192.168.168.2.http: Flags [.], ack 1, win 113, options [nop,nop,TS val 2741893901 ecr 7187654], length 0
20:43:57.690754 IP 162.1.1.1 > 162.1.1.2: GREv0, length 177: IP 162.1.1.1.54803 > 192.168.168.2.http: Flags [P.], seq 1:122, ack 1, win 113, options [nop,nop,TS val 2741893901 ecr 7187654], length 121
20:43:57.690824 IP 162.1.1.2 > 162.1.1.1: GREv0, length 56: IP 192.168.168.2.http > 162.1.1.1.54803: Flags [.], ack 122, win 223, options [nop,nop,TS val 7187662 ecr 2741893901], length 0
20:43:57.690988 IP 162.1.1.2 > 162.1.1.1: GREv0, length 490: IP 192.168.168.2.http > 162.1.1.1.54803: Flags [P.], seq 1:435, ack 122, win 223, options [nop,nop,TS val 7187662 ecr 2741893901], length 434
20:43:57.720155 IP 162.1.1.1 > 162.1.1.2: GREv0, length 56: IP 162.1.1.1.54803 > 192.168.168.2.http: Flags [.], ack 435, win 121, options [nop,nop,TS val 2741893930 ecr 7187662], length 0
```

GRE Config (Host Side)```

iptunnel add gre1 mode gre local 162.1.1.2 remote 162.1.1.1 ttl 255
ip addr add 192.168.168.2/30 dev gre1
ip link set gre1 up
ip rule add from 192.168.168.0/30 table DDOSGRE
ip route add default via 192.168.168.1 table DDOSGRE

```

GRE Config (Client Side)```

iptunnel add gre1 mode gre local 162.1.1.1 remote 162.1.1.2 ttl 255
ip addr add 192.168.168.1/30 dev gre1
ip link set gre1 up
```

GRE Interface (Host Side)```

gre1      Link encap:UNSPEC  HWaddr 40-20-07-E9-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.168.1  P-t-P:192.168.168.1  Mask:255.255.255.252
          UP POINTOPOINT RUNNING NOARP  MTU:1476  Metric:1
          RX packets:905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90649 (90.6 KB)  TX bytes:183371 (183.3 KB)
```
GRE Interface (Client Side)```

gre1      Link encap:UNSPEC  HWaddr 4A-5B-7A-6A-00-00-B0-A6-00-00-00-00-00-00-00-00  
          inet addr:192.168.168.2  P-t-P:192.168.168.2  Mask:255.255.255.252
          inet6 addr: fe80::200:5efe:4a5b:7a6a/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP  MTU:1476  Metric:1
          RX packets:907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:191718 (191.7 KB)  TX bytes:138043 (138.0 KB)
```
NAT Rules (Host Side)```

iptables -A FORWARD -j ACCEPT -p all -s 0/0 -i gre1
iptables -A FORWARD -j ACCEPT -p all -s 0/0 -o gre1

iptables -t nat -A POSTROUTING -s 192.168.168.0/30 -j SNAT --to-source 64.32.7.233

iptables -t nat -A PREROUTING -p tcp -d 162.1.1.1 --dport 1025 -j DNAT --to-destination 192.168.168.2:1025
iptables -A FORWARD -p tcp -d 192.168.168.2 --dport 1025 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -t nat -A PREROUTING -p tcp -d 162.1.1.1 --dport 113 -j DNAT --to-destination 192.168.168.2:113
iptables -A FORWARD -p tcp -d 192.168.168.2 --dport 113 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -t nat -A PREROUTING -p tcp -d 162.1.1.1 --dport 444 -j DNAT --to-destination 192.168.168.2:444
iptables -A FORWARD -p tcp -d 192.168.168.2 --dport 444 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```

OpenSSL Connect (which stalls right there)
```

root@MollyQuinn:~# openssl s_client -connect 192.168.168.2:443
CONNECTED(00000003)
```

---

