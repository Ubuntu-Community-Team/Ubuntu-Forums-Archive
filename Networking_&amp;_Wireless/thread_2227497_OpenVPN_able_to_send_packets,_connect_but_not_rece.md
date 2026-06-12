---
title: "OpenVPN able to send packets, connect but not receive data"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by James_Grafton on 2014-06-02
After following [this]("https://docs.google.com/document/d/1Ol0kC9bgbBh2zlohtBP7uZnzioZ4sShIcENgTwq5Ot0/edit") guide I've setup OpenVPN server on Ubuntu and am using TunnelBlick on OSX to connect.

Strangely all appears to work with the connection, I'm able to ping sites:

```

jrgrafton-macbookpro:~ jrgrafton$ ping jamesgrafton.com
PING jamesgrafton.com (66.33.214.180): 56 data bytes
64 bytes from 66.33.214.180: icmp_seq=0 ttl=52 time=103.068 ms

```

I'm also able to **wget** certain files:

```

jrgrafton-macbookpro:~ jrgrafton$ wget http://cachefly.cachefly.net/100mb.test
--2014-06-02 15:22:06--  http://cachefly.cachefly.net/100mb.test
Resolving cachefly.cachefly.net... 205.234.175.175
Connecting to cachefly.cachefly.net|205.234.175.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 104857600 (100M) [application/octet-stream]
Saving to: '100mb.test.2'

 7% [======>                                                                                             ] 7,688,152   2.33MB/s  eta 40s   

```


I'm even able to **telnet** to a website:

```

telnet jamesgrafton.com 80
Connected to jamesgrafton.com.
Escape character is '^]'

```

All websites hosted within our local domain work perfectly however websites outside it take up to 60 seconds to load in a browser or on the command line (tried Safari, Chrome and FF).

```

jrgrafton-macbookpro:tmp jrgrafton$ wget jamesgrafton.com
--2014-06-02 15:56:16--  http://jamesgrafton.com/
Resolving jamesgrafton.com... 66.33.214.180
Connecting to jamesgrafton.com|66.33.214.180|:80... connected.
HTTP request sent, awaiting response... 

```

My guess is that it's some kind of NAT issues, yet as I'm quite new to networking in general I can't figure out exactly what's going on here. Below are all relevant configurations:

**** CLIENT ****
```

**client.conf**

client
dev tun
proto udp
remote 23.251.131.51 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client1.crt
key client1.key
ns-cert-type server
comp-lzo
verb 3

```

```

**/etc/resolv.conf**
search openvpn
nameserver 10.8.0.1

```

```

**netstat -nr**

jrgrafton-macbookpro:~ jrgrafton$ netstat -nr
Routing tables

Internet:
Destination Gateway Flags Refs Use Netif Expire
0/1 10.8.0.13 UGSc 16 3 tun0
default 172.16.205.254 UGSc 1 53 en0
10.8.0.1/32 10.8.0.13 UGSc 1 0 tun0
10.8.0.13 10.8.0.14 UHr 28 38 tun0
23.251.131.51/32 172.16.205.254 UGSc 1 0 en0
127 127.0.0.1 UCS 0 0 lo0
127.0.0.1 127.0.0.1 UH 11 3266 lo0
128.0/1 10.8.0.13 UGSc 7 0 tun0
169.254 link#4 UCS 40 0 en0
169.254.3.229 4c:8d:79:f3:cb:2c UHLSW 0 0 en0
169.254.6.176 78:31:c1:bf:f8:5e UHLSW 0 0 en0
169.254.18.54 d0:e1:40:8f:bb:5a UHLSW 0 0 en0
169.254.19.99 64:76:ba:92:69:46 UHLSW 0 0 en0
169.254.22.232 4:c:ce:cf:3e:3e UHLSW 0 0 en0
169.254.31.190 4:c:ce:d1:9f:24 UHLSW 0 0 en0 430
169.254.37.125 d0:e1:40:9d:ba:24 UHLSW 0 0 en0
169.254.47.25 68:a8:6d:11:e8:2e UHLSW 0 0 en0
169.254.59.178 14:10:9f:e2:50:3d UHLSW 0 0 en0
169.254.77.83 b8:f6:b1:18:6:17 UHLSW 0 0 en0
169.254.87.7 98:fe:94:47:6c:8a UHLSW 0 0 en0
169.254.92.224 4c:8d:79:f3:bb:66 UHLSW 0 0 en0
169.254.93.30 5c:f9:38:8c:ab:4 UHLSW 0 0 en0
169.254.100.159 88:1f:a1:5:59:38 UHLSW 0 0 en0
169.254.101.18 4:c:ce:d0:8d:de UHLSW 0 0 en0
169.254.107.6 98:fe:94:48:5c:aa UHLSW 0 0 en0
169.254.107.95 10:93:e9:c:e8:d0 UHLSW 0 0 en0
169.254.108.72 10:40:f3:9c:5a:12 UHLSW 0 0 en0
169.254.113.141 84:38:35:56:2f:9a UHLSW 0 0 en0
169.254.121.19 14:10:9f:f0:fc:4c UHLSW 0 0 en0
169.254.132.175 98:fe:94:43:d7:d0 UHLSW 0 0 en0 1023
169.254.135.115 98:fe:94:43:b6:1e UHLSW 0 0 en0
169.254.143.52 78:31:c1:d4:23:3e UHLSW 0 0 en0
169.254.148.234 44:2a:60:f3:34:a UHLSW 0 0 en0
169.254.164.205 78:31:c1:b7:37:40 UHLSW 0 0 en0
169.254.170.254 84:38:35:54:2f:58 UHLSW 0 0 en0
169.254.183.57 d0:e1:40:8c:17:8e UHLSW 0 0 en0
169.254.184.75 8c:29:37:f3:30:ba UHLSW 0 0 en0
169.254.185.189 14:10:9f:e2:51:61 UHLSW 0 0 en0
169.254.186.216 4c:8d:79:f1:70:88 UHLSW 0 0 en0 865
169.254.195.98 14:10:9f:f0:d2:58 UHLSW 0 0 en0 117
169.254.201.10 7c:d1:c3:f7:9d:11 UHLSW 0 0 en0
169.254.209.169 ac:7b:a1:86:78:56 UHLSW 0 0 en0
169.254.216.155 4:c:ce:d1:ac:56 UHLSW 0 0 en0
169.254.227.199 10:93:e9:f:e5:8a UHLSW 0 0 en0
169.254.236.214 88:1f:a1:6:2e:72 UHLSW 0 0 en0
169.254.245.16 d0:e1:40:9f:78:aa UHLSW 0 0 en0
169.254.246.89 60:3:8:94:74:4c UHLSW 0 0 en0
169.254.251.105 f8:1e:df:f2:85:91 UHLSW 0 0 en0
169.254.252.100 14:10:9f:f1:a5:42 UHLSW 0 0 en0
172.16.204/23 link#4 UCS 98 0 en0
172.16.204.6 c8:e0:eb:17:27:85 UHLWI 0 0 en0 680
172.16.204.7 14:10:9f:dd:84:81 UHLWI 0 0 en0 921
172.16.204.13 44:d8:84:6d:dd:39 UHLWI 0 0 en0 645
172.16.204.20 14:10:9f:f1:97:c0 UHLWI 0 0 en0 981
172.16.204.21 8c:29:37:f3:3c:1e UHLWI 0 0 en0 565
172.16.204.22 4c:8d:79:f3:cb:2c UHLWI 0 0 en0 1025
172.16.204.30 4c:8d:79:f3:a1:ee UHLWI 0 0 en0 815
172.16.204.34 84:3a:4b:d1:b3:d4 UHLWI 0 0 en0 1165
172.16.204.40 84:3a:4b:f:98:b4 UHLWI 0 0 en0 144
172.16.204.43 f8:1e:df:e5:f9:5a UHLWI 0 0 en0 1094
172.16.204.45 78:31:c1:b7:75:3c UHLWI 0 0 en0 891
172.16.204.49 14:10:9f:da:97:9f UHLWI 0 0 en0 975
172.16.204.50 b8:e8:56:14:d5:c0 UHLWI 0 0 en0 836
172.16.204.53 64:76:ba:92:5f:e0 UHLWI 0 0 en0
172.16.204.55 0:24:d7:bb:25:ac UHLWI 0 0 en0 1136
172.16.204.57 a0:88:b4:7d:a4:48 UHLWI 0 0 en0 1124
172.16.204.68 28:cf:e9:50:d5:9d UHLWI 0 0 en0 867
172.16.204.74 24:77:3:57:d3:10 UHLWI 0 0 en0 1177
172.16.204.75 10:93:e9:f:d6:72 UHLWI 0 0 en0 182
172.16.204.78 14:10:9f:f0:d8:8 UHLWI 0 0 en0 855
172.16.204.89 14:10:9f:f1:9a:ae UHLWI 0 0 en0 784
172.16.204.95 4:c:ce:d1:9f:24 UHLWI 0 0 en0 475
172.16.204.100 8c:29:37:ef:1d:6a UHLWI 0 0 en0
172.16.204.107 84:38:35:5d:cd:6 UHLWI 0 0 en0 874
172.16.204.117 20:c9:d0:79:e0:3 UHLWI 0 0 en0 842
172.16.204.131 84:38:35:63:ab:32 UHLWI 0 0 en0 567
172.16.204.134 b8:8d:12:2c:e1:b4 UHLWI 0 0 en0 1010
172.16.204.139 10:40:f3:80:27:26 UHLWI 0 0 en0 244
172.16.204.141 88:1f:a1:6:3:f2 UHLWI 0 0 en0 962
172.16.204.142 8c:29:37:f3:22:a6 UHLWI 0 0 en0 553
172.16.204.146 88:1f:a1:5:a6:4c UHLWI 0 0 en0 888
172.16.204.157 14:10:9f:e2:51:61 UHLWI 0 0 en0
172.16.204.161 78:31:c1:b7:7d:48 UHLWI 0 0 en0 983
172.16.204.162 44:2a:60:f2:35:54 UHLWI 0 0 en0 673
172.16.204.163 0:24:d7:a6:9b:2c UHLWI 0 0 en0 911
172.16.204.165 78:31:c1:b7:4c:98 UHLWI 0 0 en0 950
172.16.204.168 10:40:f3:86:58:70 UHLWI 0 0 en0 984
172.16.204.172 127.0.0.1 UHS 1 0 lo0
172.16.204.187 5c:f9:38:9c:8a:7a UHLWI 0 0 en0 1115
172.16.204.191 24:77:3:d2:2f:88 UHLWI 0 0 en0
172.16.204.198 8c:29:37:f2:c2:d4 UHLWI 0 0 en0 923
172.16.204.206 60:3:8:a8:9b:18 UHLWI 0 0 en0 984
172.16.204.208 4c:8d:79:f1:70:70 UHLWI 0 0 en0 192
172.16.204.220 24:77:3:27:4a:3c UHLWI 0 0 en0 680
172.16.204.229 10:40:f3:86:82:36 UHLWI 0 0 en0 200
172.16.204.234 28:cf:e9:20:6b:4f UHLWI 0 0 en0 1108
172.16.204.248 7c:d1:c3:f1:b8:99 UHLWI 0 0 en0 1121
172.16.204.249 b8:8d:12:13:bc:a6 UHLWI 0 0 en0 969
172.16.205.1 88:1f:a1:5:a6:1e UHLWI 0 0 en0 821
172.16.205.6 64:76:ba:98:a:b4 UHLWI 0 0 en0 342
172.16.205.12 5c:f9:38:90:54:98 UHLWI 0 0 en0
172.16.205.14 10:93:e9:f:e5:8a UHLWI 0 0 en0 642
172.16.205.15 88:1f:a1:2:11:42 UHLWI 0 0 en0 280
172.16.205.49 8:11:96:5:32:64 UHLWI 0 0 en0
172.16.205.54 4:c:ce:d6:ee:70 UHLWI 0 0 en0 811
172.16.205.56 64:76:ba:98:e:4 UHLWI 0 0 en0 356
172.16.205.58 f8:1e:df:f2:85:91 UHLWI 0 0 en0 447
172.16.205.59 d0:e1:40:91:f1:8c UHLWI 0 0 en0 1173
172.16.205.70 4:c:ce:ce:f2:ec UHLWI 0 0 en0 980
172.16.205.73 8c:29:37:e9:77:5e UHLWI 0 0 en0 588
172.16.205.76 10:40:f3:7c:b2:c UHLWI 0 0 en0 1151
172.16.205.101 54:26:96:db:c1:6f UHLWI 0 0 en0 1129
172.16.205.116 b8:8d:12:13:82:8 UHLWI 0 0 en0 1138
172.16.205.120 4:c:ce:ce:ab:6e UHLWI 0 0 en0 1058
172.16.205.125 f8:1e:df:da:ec:76 UHLWI 0 0 en0
172.16.205.131 60:3:8:94:74:4c UHLWI 0 0 en0 23
172.16.205.140 b8:e8:56:7:d9:c4 UHLWI 0 0 en0 182
172.16.205.141 84:3a:4b:96:8e:dc UHLWI 0 0 en0 1147
172.16.205.146 84:38:35:56:2f:9a UHLWI 0 0 en0
172.16.205.151 14:10:9f:d0:da:47 UHLWI 0 0 en0 273
172.16.205.153 84:38:35:67:a6:e UHLWI 0 0 en0 1070
172.16.205.159 5c:f9:38:8f:2c:72 UHLWI 0 0 en0 526
172.16.205.160 a0:88:b4:6a:71:c UHLWI 0 0 en0 752
172.16.205.163 10:93:e9:c:3d:96 UHLWI 0 0 en0 914
172.16.205.164 10:93:e9:0:6b:9c UHLWI 0 0 en0 475
172.16.205.172 b8:e8:56:8:27:36 UHLWI 0 0 en0 891
172.16.205.178 84:38:35:54:1d:d0 UHLWI 0 0 en0 741
172.16.205.179 98:fe:94:43:b6:1e UHLWI 0 0 en0 893
172.16.205.183 84:38:35:67:48:48 UHLWI 0 0 en0 645
172.16.205.189 10:93:e9:0:a6:6 UHLWI 0 0 en0 1155
172.16.205.192 88:1f:a1:5:f5:16 UHLWI 0 0 en0 777
172.16.205.194 4c:8d:79:f1:35:18 UHLWI 0 0 en0 149
172.16.205.195 4:c:ce:d1:9d:34 UHLWI 0 0 en0 652
172.16.205.203 98:fe:94:48:5c:aa UHLWI 0 0 en0 211
172.16.205.213 14:10:9f:d0:1c:8b UHLWI 0 0 en0
172.16.205.214 60:3:8:94:74:4a UHLWI 0 0 en0 40
172.16.205.217 88:1f:a1:5:a6:58 UHLWI 0 0 en0 1129
172.16.205.219 b8:e8:56:14:b4:b0 UHLWI 0 0 en0 483
172.16.205.220 7c:d1:c3:e8:38:e5 UHLWI 0 0 en0 560
172.16.205.222 d0:e1:40:90:84:8e UHLWI 0 0 en0 905
172.16.205.230 7c:d1:c3:f7:ec:5d UHLWI 0 0 en0 551
172.16.205.231 84:3a:4b:ce:1f:f4 UHLWI 0 0 en0 1177
172.16.205.232 84:3a:4b:d6:5d:20 UHLWI 0 0 en0 1180
172.16.205.236 24:77:3:57:72:84 UHLWI 0 0 en0 870
172.16.205.240 84:3a:4b:17:2e:6a UHLWI 0 0 en0 828
172.16.205.246 14:10:9f:f0:f2:64 UHLWI 0 0 en0 1119
172.16.205.249 a0:88:b4:7e:6a:58 UHLWI 0 0 en0 830
172.16.205.254 0:0:c:9f:f0:46 UHLWIir 3 408 en0 1169
172.16.205.255 ff:ff:ff:ff:ff:ff UHLWbI 0 7 en0

```

```

[B]ifconfig tun0
[/B]
tun0: flags=8851<UP,POINTOPOINT,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    inet 10.8.0.14 --> 10.8.0.13 netmask 0xffffffff 
    open (pid 29759)

```

```

**ifconfig en0**

en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether 78:31:c1:b7:7d:52 
    inet6 fe80::7a31:c1ff:feb7:7d52%en0 prefixlen 64 scopeid 0x4 
    inet6 2620::1073:22:7a31:c1ff:feb7:7d52 prefixlen 64 autoconf 
    inet6 2620::1073:22:4c0f:6e8c:20f:d6e1 prefixlen 64 autoconf temporary 
    inet 172.16.204.172 netmask 0xfffffe00 broadcast 172.16.205.255
    nd6 options=1<PERFORMNUD>
    media: autoselect
    status: active

```


**** SERVER ****
```

**server.conf**

port 1194
proto udp
dev tun
ca ca.crt
cert myservername.crt
key myservername.key
dh /etc/openvpn/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1"
push "dhcp-option DNS 10.8.0.1"
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3

```

```

**IPTables rules**

# OpenVPN
iptables -A INPUT -i eth0 -m state --state NEW -p udp --dport 1194 -j ACCEPT

# Allow TUN interface connections to OpenVPN server
iptables -A INPUT -i tun0 -j ACCEPT

# Allow TUN interface connections to be forwarded through other interfaces
iptables -A FORWARD -i tun0 -j ACCEPT
iptables -A FORWARD -i tun0 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o tun+ -m state --state RELATED,ESTABLISHED -j ACCEPT

# NAT the VPN client traffic to the internet
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

```

```

**netstat -nr**

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.240.0.1      0.0.0.0         UG        0 0          0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
10.240.0.1      0.0.0.0         255.255.255.255 UH        0 0          0 eth0

```

```

**ifconfig eth0**

eth0      Link encap:Ethernet  HWaddr 42:01:0a:f0:94:ae  
          inet addr:10.240.148.174  Bcast:10.240.148.174  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1460  Metric:1
          RX packets:6343172 errors:0 dropped:0 overruns:0 frame:35991
          TX packets:6507208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1452428402 (1.3 GiB)  TX bytes:1177643035 (1.0 GiB)

```

```

[B]ifconfig tun0
[/B]
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:102458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266369 errors:0 dropped:391 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:61222915 (58.3 MiB)  TX bytes:243674352 (232.3 MiB)

```

---

### Post by James_Grafton on 2014-06-05
All fixed now!

Turns out the TCP rather than UDP fixed the issue (DD-WRT) made it that much more fiddly...

---

