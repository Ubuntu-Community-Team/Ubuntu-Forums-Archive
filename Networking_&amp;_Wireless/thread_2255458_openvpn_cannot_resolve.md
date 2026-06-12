---
title: "openvpn cannot resolve"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by Apagon on 2014-12-05
Here is my (x)ubuntu version:

```
root@ubuntu:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

Before I mount the vpn, here is what we have: 

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


wlan0     Link encap:Ethernet  HWaddr 00:24:01:ee:91:3d  
          inet addr:192.168.2.79  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1ff:feee:913d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:628026 (628.0 KB)  TX bytes:56869 (56.8 KB)
```

Ping is filtered by the ISP:

```

root@ubuntu:~# ping www.google.com
PING www.google.com (64.233.167.103) 56(84) bytes of data.
From 192.168.2.1 icmp_seq=1 Destination Net Prohibited
From 192.168.2.1 icmp_seq=2 Destination Net Prohibited
From 192.168.2.1 icmp_seq=3 Destination Net Prohibited
```

I can ping the stack:

```
root@ubuntu:~# ping 192.168.02.79
PING 192.168.02.79 (192.168.2.79) 56(84) bytes of data.
64 bytes from 192.168.2.79: icmp_seq=1 ttl=64 time=0.023 ms
64 bytes from 192.168.2.79: icmp_seq=2 ttl=64 time=0.049 ms
```

I installed client configuration from a free VPN provider 
here is the client configuration: 

```
client
dev tun1
proto tcp
remote 93.115.83.250 443
resolv-retry infinite
nobind
persist-key
persist-tun
auth-user-pass
comp-lzo
verb 3
cipher AES-128-CBC
fast-io
pull
route-delay 2
redirect-gateway
###---I just added the following: ----
verb 6


```

I connect to the vpn server: 

```
Thu Dec  4 15:16:36 2014 us=990883 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Thu Dec  4 15:16:36 2014 us=990952 NOTE: --fast-io is disabled since we are not using UDP
Thu Dec  4 15:16:36 2014 us=992665 LZO compression initialized
Thu Dec  4 15:16:36 2014 us=992867 Control Channel MTU parms [ L:1560 D:140 EF:40 EB:0 ET:0 EL:0 ]
Thu Dec  4 15:16:36 2014 us=992969 Socket Buffers: R=[87380->131072] S=[16384->131072]
Thu Dec  4 15:16:36 2014 us=993035 Data Channel MTU parms [ L:1560 D:1450 EF:60 EB:135 ET:0 EL:0 AF:3/1 ]
Thu Dec  4 15:16:36 2014 us=993091 Local Options String: 'V4,dev-type tun,link-mtu 1560,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,cipher AES-128-CBC,auth SHA1,keysize 128,key-method 2,tls-client'
Thu Dec  4 15:16:36 2014 us=993113 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1560,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,cipher AES-128-CBC,auth SHA1,keysize 128,key-method 2,tls-server'
Thu Dec  4 15:16:36 2014 us=993170 Local Options hash (VER=V4): 'bc07730e'
Thu Dec  4 15:16:36 2014 us=993211 Expected Remote Options hash (VER=V4): 'b695cb4a'
Thu Dec  4 15:16:36 2014 us=993259 Attempting to establish TCP connection with [AF_INET]93.115.83.250:443 [nonblock]
Thu Dec  4 15:16:37 2014 us=993523 TCP connection established with [AF_INET]93.115.83.250:443
Thu Dec  4 15:16:37 2014 us=993596 TCPv4_CLIENT link local: [undef]
Thu Dec  4 15:16:37 2014 us=993625 TCPv4_CLIENT link remote: [AF_INET]93.115.83.250:443
Thu Dec  4 15:16:37 2014 us=993748 TCPv4_CLIENT WRITE [14] to [AF_INET]93.115.83.250:443: P_CONTROL_HARD_RESET_CLIENT_V2 kid=0 [ ] pid=0 DATA len=0
Thu Dec  4 15:16:38 2014 us=90125 TCPv4_CLIENT READ [26] from [AF_INET]93.115.83.250:443: P_CONTROL_HARD_RESET_SERVER_V2 kid=0 [ 0 ] pid=0 DATA len=0
Thu Dec  4 15:16:38 2014 us=90205 TLS: Initial packet from [AF_INET]93.115.83.250:443, sid=c7148944 7465b88f
Thu Dec  4 15:16:38 2014 us=90260 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 0 ]
Thu Dec  4 15:16:38 2014 us=90329 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Thu Dec  4 15:16:38 2014 us=90360 TCPv4_CLIENT WRITE [114] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=1 DATA len=100
Thu Dec  4 15:16:38 2014 us=90385 TCPv4_CLIENT WRITE [114] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=2 DATA len=100
Thu Dec  4 15:16:38 2014 us=90409 TCPv4_CLIENT WRITE [39] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=3 DATA len=25
Thu Dec  4 15:16:38 2014 us=320860 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 1 ]
Thu Dec  4 15:16:38 2014 us=454622 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 2 ]
Thu Dec  4 15:16:38 2014 us=454685 TCPv4_CLIENT READ [126] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ 3 ] pid=1 DATA len=100
Thu Dec  4 15:16:38 2014 us=454770 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=2 DATA len=100
Thu Dec  4 15:16:38 2014 us=454791 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=3 DATA len=100
Thu Dec  4 15:16:38 2014 us=454812 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=4 DATA len=100
Thu Dec  4 15:16:38 2014 us=454833 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 1 ]
Thu Dec  4 15:16:38 2014 us=454882 TCPv4_CLIENT WRITE [30] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 2 3 4 ]
Thu Dec  4 15:16:38 2014 us=550166 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=5 DATA len=100
Thu Dec  4 15:16:38 2014 us=550236 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 5 ]
Thu Dec  4 15:16:38 2014 us=647096 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=6 DATA len=100
Thu Dec  4 15:16:38 2014 us=647160 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 6 ]
Thu Dec  4 15:16:38 2014 us=742280 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=7 DATA len=100
Thu Dec  4 15:16:38 2014 us=742347 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=8 DATA len=100
Thu Dec  4 15:16:38 2014 us=742399 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 7 ]
Thu Dec  4 15:16:38 2014 us=742419 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 8 ]
Thu Dec  4 15:16:38 2014 us=836052 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=9 DATA len=100
Thu Dec  4 15:16:38 2014 us=836258 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 9 ]
Thu Dec  4 15:16:38 2014 us=929756 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=10 DATA len=100
Thu Dec  4 15:16:38 2014 us=929826 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 10 ]
Thu Dec  4 15:16:39 2014 us=23949 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=11 DATA len=100
Thu Dec  4 15:16:39 2014 us=24066 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=12 DATA len=100
Thu Dec  4 15:16:39 2014 us=24098 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 11 ]
Thu Dec  4 15:16:39 2014 us=24124 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 12 ]
Thu Dec  4 15:16:39 2014 us=117875 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=13 DATA len=100
Thu Dec  4 15:16:39 2014 us=117994 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 13 ]
Thu Dec  4 15:16:39 2014 us=212512 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=14 DATA len=100
Thu Dec  4 15:16:39 2014 us=212671 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 14 ]
Thu Dec  4 15:16:39 2014 us=307308 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=15 DATA len=100
Thu Dec  4 15:16:39 2014 us=307424 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=16 DATA len=100
Thu Dec  4 15:16:39 2014 us=307456 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 15 ]
Thu Dec  4 15:16:39 2014 us=307483 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 16 ]
Thu Dec  4 15:16:39 2014 us=401580 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=17 DATA len=100
Thu Dec  4 15:16:39 2014 us=401755 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 17 ]
Thu Dec  4 15:16:39 2014 us=496062 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=18 DATA len=100
Thu Dec  4 15:16:39 2014 us=496182 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 18 ]
Thu Dec  4 15:16:39 2014 us=591394 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=19 DATA len=100
Thu Dec  4 15:16:39 2014 us=591551 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=20 DATA len=100
Thu Dec  4 15:16:39 2014 us=591628 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 19 ]
Thu Dec  4 15:16:39 2014 us=591691 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 20 ]
Thu Dec  4 15:16:39 2014 us=687983 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=21 DATA len=100
Thu Dec  4 15:16:39 2014 us=688097 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 21 ]
Thu Dec  4 15:16:39 2014 us=782779 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=22 DATA len=100
Thu Dec  4 15:16:39 2014 us=782866 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 22 ]
Thu Dec  4 15:16:39 2014 us=877451 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=23 DATA len=100
Thu Dec  4 15:16:39 2014 us=877607 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=24 DATA len=100
Thu Dec  4 15:16:39 2014 us=877683 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 23 ]
Thu Dec  4 15:16:39 2014 us=877812 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 24 ]
Thu Dec  4 15:16:39 2014 us=971340 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=25 DATA len=100
Thu Dec  4 15:16:39 2014 us=971458 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 25 ]
Thu Dec  4 15:16:40 2014 us=65227 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=26 DATA len=100
Thu Dec  4 15:16:40 2014 us=65346 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 26 ]
Thu Dec  4 15:16:40 2014 us=160165 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=27 DATA len=100
Thu Dec  4 15:16:40 2014 us=161894 VERIFY OK: depth=1, C=MT, ST=MLT, L=Valletta, O=FreeVPN.me, OU=FreeVPN.me, CN=FreeVPN.me CA, name=FreeVPN.me, emailAddress=contact@freevpn.me
Thu Dec  4 15:16:40 2014 us=163344 VERIFY OK: depth=0, C=MT, ST=MLT, L=Valletta, O=FreeVPN.me, OU=FreeVPN.me, CN=FreeVPN.me, name=FreeVPN.me, emailAddress=contact@freevpn.me
Thu Dec  4 15:16:40 2014 us=163472 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=28 DATA len=100
Thu Dec  4 15:16:40 2014 us=163551 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 27 ]
Thu Dec  4 15:16:40 2014 us=163616 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 28 ]
Thu Dec  4 15:16:40 2014 us=253396 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=29 DATA len=100
Thu Dec  4 15:16:40 2014 us=253509 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 29 ]
Thu Dec  4 15:16:40 2014 us=347870 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=30 DATA len=100
Thu Dec  4 15:16:40 2014 us=347990 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 30 ]
Thu Dec  4 15:16:40 2014 us=441661 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=31 DATA len=100
Thu Dec  4 15:16:40 2014 us=441820 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=32 DATA len=100
Thu Dec  4 15:16:40 2014 us=441897 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 31 ]
Thu Dec  4 15:16:40 2014 us=441961 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 32 ]
Thu Dec  4 15:16:40 2014 us=537084 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=33 DATA len=100
Thu Dec  4 15:16:40 2014 us=537156 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 33 ]
Thu Dec  4 15:16:40 2014 us=631310 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=34 DATA len=100
Thu Dec  4 15:16:40 2014 us=631481 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 34 ]
Thu Dec  4 15:16:40 2014 us=724912 TCPv4_CLIENT READ [103] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=35 DATA len=89
Thu Dec  4 15:16:40 2014 us=779076 TCPv4_CLIENT WRITE [126] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ 35 ] pid=4 DATA len=100
Thu Dec  4 15:16:40 2014 us=779109 TCPv4_CLIENT WRITE [114] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=5 DATA len=100
Thu Dec  4 15:16:40 2014 us=779129 TCPv4_CLIENT WRITE [114] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=6 DATA len=100
Thu Dec  4 15:16:40 2014 us=779149 TCPv4_CLIENT WRITE [40] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=7 DATA len=26
Thu Dec  4 15:16:40 2014 us=956873 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 4 ]
Thu Dec  4 15:16:41 2014 us=89394 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 5 ]
Thu Dec  4 15:16:41 2014 us=89581 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 6 ]
Thu Dec  4 15:16:41 2014 us=89642 TCPv4_CLIENT READ [126] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ 7 ] pid=36 DATA len=100
Thu Dec  4 15:16:41 2014 us=89717 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=37 DATA len=100
Thu Dec  4 15:16:41 2014 us=89954 TCPv4_CLIENT READ [48] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=38 DATA len=34
Thu Dec  4 15:16:41 2014 us=90276 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 36 ]
Thu Dec  4 15:16:41 2014 us=90385 TCPv4_CLIENT WRITE [130] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ 37 38 ] pid=8 DATA len=100
Thu Dec  4 15:16:41 2014 us=90433 TCPv4_CLIENT WRITE [114] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=9 DATA len=100
Thu Dec  4 15:16:41 2014 us=90505 TCPv4_CLIENT WRITE [114] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=10 DATA len=100
Thu Dec  4 15:16:41 2014 us=90548 TCPv4_CLIENT WRITE [92] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=11 DATA len=78
Thu Dec  4 15:16:41 2014 us=322864 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 8 ]
Thu Dec  4 15:16:41 2014 us=454411 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 9 ]
Thu Dec  4 15:16:41 2014 us=454575 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 10 ]
Thu Dec  4 15:16:41 2014 us=454623 TCPv4_CLIENT READ [126] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ 11 ] pid=39 DATA len=100
Thu Dec  4 15:16:41 2014 us=454730 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=40 DATA len=100
Thu Dec  4 15:16:41 2014 us=454778 TCPv4_CLIENT READ [96] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=41 DATA len=82
Thu Dec  4 15:16:41 2014 us=455128 Data Channel Encrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Thu Dec  4 15:16:41 2014 us=455157 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Dec  4 15:16:41 2014 us=455180 Data Channel Decrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Thu Dec  4 15:16:41 2014 us=455254 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Dec  4 15:16:41 2014 us=455302 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 39 ]
Thu Dec  4 15:16:41 2014 us=455404 TCPv4_CLIENT WRITE [26] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 40 41 ]
Thu Dec  4 15:16:41 2014 us=455459 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Thu Dec  4 15:16:41 2014 us=455541 [FreeVPN.me] Peer Connection Initiated with [AF_INET]93.115.83.250:443
Thu Dec  4 15:16:43 2014 us=814138 SENT CONTROL [FreeVPN.me]: 'PUSH_REQUEST' (status=1)
Thu Dec  4 15:16:43 2014 us=814256 TCPv4_CLIENT WRITE [104] to [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=12 DATA len=90
Thu Dec  4 15:16:43 2014 us=911787 TCPv4_CLIENT READ [22] from [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 12 ]
Thu Dec  4 15:16:44 2014 us=51636 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=42 DATA len=100
Thu Dec  4 15:16:44 2014 us=51861 TCPv4_CLIENT READ [114] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=43 DATA len=100
Thu Dec  4 15:16:44 2014 us=51915 TCPv4_CLIENT READ [48] from [AF_INET]93.115.83.250:443: P_CONTROL_V1 kid=0 [ ] pid=44 DATA len=34
Thu Dec  4 15:16:44 2014 us=52032 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS 8.8.8.8,dhcp-option DNS 8.8.4.4,route 10.13.0.1,topology net30,ping 15,ping-restart 120,ifconfig 10.13.0.94 10.13.0.93'
Thu Dec  4 15:16:44 2014 us=52202 OPTIONS IMPORT: timers and/or timeouts modified
Thu Dec  4 15:16:44 2014 us=52224 OPTIONS IMPORT: --ifconfig/up options modified
Thu Dec  4 15:16:44 2014 us=52242 OPTIONS IMPORT: route options modified
Thu Dec  4 15:16:44 2014 us=52258 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Thu Dec  4 15:16:44 2014 us=52563 ROUTE_GATEWAY 192.168.2.1/255.255.255.0 IFACE=wlan0 HWADDR=00:24:01:ee:91:3d
Thu Dec  4 15:16:44 2014 us=53073 TUN/TAP device tun1 opened
Thu Dec  4 15:16:44 2014 us=53110 TUN/TAP TX queue length set to 100
Thu Dec  4 15:16:44 2014 us=53142 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Thu Dec  4 15:16:44 2014 us=53207 /sbin/ip link set dev tun1 up mtu 1500
Thu Dec  4 15:16:44 2014 us=55739 /sbin/ip addr add dev tun1 local 10.13.0.94 peer 10.13.0.93
Thu Dec  4 15:16:44 2014 us=56888 TCPv4_CLIENT WRITE [22] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 42 ]
Thu Dec  4 15:16:44 2014 us=57018 TCPv4_CLIENT WRITE [26] to [AF_INET]93.115.83.250:443: P_ACK_V1 kid=0 [ 43 44 ]
Thu Dec  4 15:16:46 2014 us=237316 /sbin/ip route add 93.115.83.250/32 via 192.168.2.1
Thu Dec  4 15:16:46 2014 us=238627 /sbin/ip route add 0.0.0.0/1 via 10.13.0.93
Thu Dec  4 15:16:46 2014 us=240611 /sbin/ip route add 128.0.0.0/1 via 10.13.0.93
Thu Dec  4 15:16:46 2014 us=243113 /sbin/ip route add 10.13.0.1/32 via 10.13.0.93
Thu Dec  4 15:16:46 2014 us=245592 Initialization Sequence Completed
```

The vpn is now mounted: 

```
tun1      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.13.0.94  P-t-P:10.13.0.93  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Here is the routing table when vpn is in place: 

```
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.13.0.93      128.0.0.0       UG    0      0        0 tun1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
10.13.0.1       10.13.0.93      255.255.255.255 UGH   0      0        0 tun1
10.13.0.93      0.0.0.0         255.255.255.255 UH    0      0        0 tun1
93.115.83.250   192.168.2.1     255.255.255.255 UGH   0      0        0 wlan0
128.0.0.0       10.13.0.93      128.0.0.0       UG    0      0        0 tun1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


ubuntu@ubuntu:~$ ip route show
0.0.0.0/1 via 10.13.0.93 dev tun1 
default via 192.168.2.1 dev wlan0 
10.13.0.1 via 10.13.0.93 dev tun1 
10.13.0.93 dev tun1  proto kernel  scope link  src 10.13.0.94 
93.115.83.250 via 192.168.2.1 dev wlan0 
128.0.0.0/1 via 10.13.0.93 dev tun1 
192.168.2.0/24 dev wlan0  proto kernel  scope link  src 192.168.2.79 

```

I can ping the stack: 
```

ubuntu@ubuntu:~$ ping 10.13.0.94
PING 10.13.0.94 (10.13.0.94) 56(84) bytes of data.
64 bytes from 10.13.0.94: icmp_seq=1 ttl=64 time=0.052 ms
64 bytes from 10.13.0.94: icmp_seq=2 ttl=64 time=0.054 ms
```

I can ping the vpn server: 
```

ubuntu@ubuntu:~$ ping 10.13.0.1
PING 10.13.0.1 (10.13.0.1) 56(84) bytes of data.
64 bytes from 10.13.0.1: icmp_seq=1 ttl=64 time=96.1 ms
64 bytes from 10.13.0.1: icmp_seq=2 ttl=64 time=99.6 ms
```

I cannot ping the tunnel end host (which is normal):
```

ubuntu@ubuntu:~$ ping 10.13.0.93
PING 10.13.0.93 (10.13.0.93) 56(84) bytes of data.
From 10.13.0.1 icmp_seq=1 Destination Host Prohibited
From 10.13.0.1 icmp_seq=2 Destination Host Prohibited
```

I can ping any ip on internet through the tunnel: 
```

ubuntu@ubuntu:~$ ping 212.27.40.240 
PING 212.27.40.240 (212.27.40.240) 56(84) bytes of data.
64 bytes from 212.27.40.240: icmp_seq=1 ttl=49 time=138 ms
64 bytes from 212.27.40.240: icmp_seq=2 ttl=49 time=137 ms
64 bytes from 212.27.40.240: icmp_seq=3 ttl=49 time=137 ms
```

```
ubuntu@ubuntu:~$ ping 173.194.44.18
PING 173.194.44.18 (173.194.44.18) 56(84) bytes of data.
64 bytes from 173.194.44.18: icmp_seq=1 ttl=51 time=140 ms
64 bytes from 173.194.44.18: icmp_seq=2 ttl=51 time=1722 ms
64 bytes from 173.194.44.18: icmp_seq=3 ttl=51 time=809 ms
```

I can ping both dns provided by the vpn 

```
ubuntu@ubuntu:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=52 time=130 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=52 time=130 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=52 time=133 ms

ubuntu@ubuntu:~$ ping 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_seq=1 ttl=52 time=128 ms
64 bytes from 8.8.4.4: icmp_seq=2 ttl=52 time=127 ms
64 bytes from 8.8.4.4: icmp_seq=3 ttl=52 time=128 ms
```

I made a little dump to be sure the tunnel is used when pinging an ip over internet:

```
root@ubuntu:~# tcpdump -ni any icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol dec    ode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes
11:18:12.091704 IP 10.13.0.14 > 212.27.40.240: ICMP echo request, id 6625, seq 1, length 64
11:18:12.227045 IP 212.27.40.240 > 10.13.0.14: ICMP echo reply, id 6625, seq 1, length 64
11:18:13.093187 IP 10.13.0.14 > 212.27.40.240: ICMP echo request, id 6625, seq 2, length 64
11:18:13.228153 IP 212.27.40.240 > 10.13.0.14: ICMP echo reply, id 6625, seq 2, length 64
11:18:14.094211 IP 10.13.0.14 > 212.27.40.240: ICMP echo request, id 6625, seq 3, length 64
```

dump above shows there is no routing issue as well. 
but I cannot resolve anything: 

```
ubuntu@ubuntu:~$ nslookup www.google.com 8.8.8.8
;; connection timed out; no servers could be reached

ubuntu@ubuntu:~$ nslookup www.google.com 8.8.4.4
;; connection timed out; no servers could be reached
```

tcpdump shows that the dns requests are sent, but we never see any response back to our requests:

```
root@ubuntu:~# tcpdump -ni any port 53
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes
15:31:42.213105 IP 10.13.0.94.36335 > 8.8.8.8.53: 55836+ A? www.google.com. (32)
15:31:47.213243 IP 10.13.0.94.36335 > 8.8.8.8.53: 55836+ A? www.google.com. (32)
15:31:52.213427 IP 10.13.0.94.36335 > 8.8.8.8.53: 55836+ A? www.google.com. (32)
```

No filter is in place: 

```
root@ubuntu:~# ufw status
Status: inactive
```

iptables not installed 

I dont think it's a routing problem, because ping to an internet ip or to the dns ips (of the vpn) gets back normally. 
I have tried another free vpn provider and have the exact same problem. 
I have digged over and over again through google but could not find any accetable answer or lead. It starts becoming insame at this point, because I start doing the same tests over and over and dont know what to do.

I have already read this post and other posts regarding openvpn but could not find any answer to this issue. 

[http://ubuntuforums.org/search.php?searchid=6402849](http://ubuntuforums.org/search.php?searchid=6402849)

thanks for your help folks!

---

### Post by kevdog on 2014-12-08
Try do this in your openvpn conf file:

Right now you have:
redirect-gateway

Try
redirect-gateway def1

And if that doesnt work
redirect-gateway def1 bypass-dhcp

I'm not sure why however but there is a problem with how your dhcp requests are being routed.

---

### Post by Apagon on 2014-12-15
Thank you very much kevdog; I was so deseperate, I did not check the forum for 1 week.
I tried your suggestions, and even did the following.
I tried 'redirect-gateway def1' with and without this:

script-security 2
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf

the problem remains. Then I tried 'redirect-gateway def1 bypass-dhcp' with and without what's above, and the problem still remains.

I am just wondering how dhcp could be the cause of this issue. It looks like dhcp does its jobs correctly as it gives me a tunnel ip so that I can mount the tunnel. Furthermore, I can ping everybody from there.
Anyway, thank you very much. If you have other ideas, they are more than welcome (btw, it was perfectly working with previous ubuntu distro, I just needed to add script sec 2 to avoid dns leaks).

---

