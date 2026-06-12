---
title: "Ubuntu - OpenVPN setup   remote LAN needs to access Server side LAN machines"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by wowiesy2 on 2017-12-11
I managed to get a OpenVPN Road Warrior setup work late last week (OVPN server at the server side, a lone mac openvpn client connecting to the server) and was able to access other LAN machines at the server side.. 


I figure that this will be a stepping stone for the site to site config I am planning  on..


SERVER SIDE:


LAN Gateway1: 192.168.100.2
LAN Gateway2: 192.168.100.5
LAN Gateway3: 192.168.100.112


OpenVPN Box LAN IP: 192.168.100.253
            VPN IP: 10.8.0.1


Servers that need to be accessed at SERVER SIDE: 
192.168.100.246  - db server
192.168.100.141 & 192.168.100.144  - remote desktop 




SERVER OPENVPN CONFIG: 


```
port 1194
proto udp
dev tun
topology subnet
ca /etc/openvpn/ca.crt
cert /etc/openvpn/BULVPNSERVER.crt
key /etc/openvpn/BULVPNSERVER.key  # This file should be kept secret
dh /etc/openvpn/dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.100.0 255.255.255.0"
client-config-dir ccd
route 192.168.254.0 255.255.255.0  # site B LAN
route 192.168.111.0 255.255.255.0  # site A LAN
client-config-dir ccd
route 10.8.0.245 255.255.255.0   # fixed vpn ip of site B
route 10.8.0.249 255.255.255.0   # fixed vpn ip of site A
keepalive 10 120
tls-auth ta.key 0 # This file is secret
cipher AES-128-CBC   # AES
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
log-append  openvpn.log
verb 3

```



client ccd dir: 


```
kss1x@UBUNTUVPN:/etc/openvpn/ccd$ ls
BUL.JFINCR  BUL.U1010

```



contents of BUL.JFINCR: 


```
iroute 192.168.111.0 255.255.255.0
ifconfig-push 10.8.0.249 255.255.255.0



```

ifconfig at vpn server


```
kss1x@UBUNTUVPN:~$ ifconfig
eno1      Link encap:Ethernet  HWaddr 94:c6:91:13:63:d8  
          inet addr:192.168.100.253  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::96c6:91ff:fe13:63d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325791 errors:0 dropped:181331 overruns:0 frame:0
          TX packets:21609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43337430 (43.3 MB)  TX bytes:2643077 (2.6 MB)
          Interrupt:16 Memory:dc100000-dc120000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:14250 (14.2 KB)  TX bytes:14250 (14.2 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:101997 (101.9 KB)  TX bytes:116980 (116.9 KB)



```ip route show


```
default via 192.168.100.5 dev eno1 onlink 
10.8.0.0/24 dev tun0  proto kernel  scope link  src 10.8.0.1 
169.254.0.0/16 dev eno1  scope link  metric 1000 
192.168.100.0/24 dev eno1  proto kernel  scope link  src 192.168.100.253 
192.168.111.0/24 via 10.8.0.2 dev tun0 
192.168.254.0/24 via 10.8.0.2 dev tun0 



```

over at the vpn client side (site A): 


client config


```


client
dev tun
proto udp
remote xxx.xx.xx.xxx  1194
remote-random
resolv-retry infinite
nobind
user nobody
group nogroup
persist-key
persist-tun
ca ca.crt
cert BUL.JFINCR.crt
key BUL.JFINCR.key
remote-cert-tls server
tls-auth ta.key 1
cipher AES-128-CBC
comp-lzo
verb 3

```





ifconfig


```
kss1x@JFINCRROUTER:~$ ifconfig
enp1s0    Link encap:Ethernet  HWaddr 7c:8b:ca:01:45:d7  
          inet addr:192.168.15.254  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::7e8b:caff:fe01:45d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170879 errors:0 dropped:6 overruns:0 frame:0
          TX packets:165404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110413307 (110.4 MB)  TX bytes:37594212 (37.5 MB)


enp2s0    Link encap:Ethernet  HWaddr 1c:1b:0d:d6:b5:84  
          inet addr:192.168.111.1  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::1e1b:dff:fed6:b584/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:664899 errors:0 dropped:9231 overruns:0 frame:0
          TX packets:656674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117215448 (117.2 MB)  TX bytes:566612266 (566.6 MB)


enp3s0    Link encap:Ethernet  HWaddr 7c:8b:ca:01:8e:8e  
          inet addr:192.168.2.254  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::7e8b:caff:fe01:8e8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:470731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:467080400 (467.0 MB)  TX bytes:67721317 (67.7 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:55263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:5154158 (5.1 MB)  TX bytes:5154158 (5.1 MB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.249  P-t-P:10.8.0.249  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:55147 (55.1 KB)  TX bytes:59531 (59.5 KB)





```ip route show
```


default 
	nexthop via 192.168.15.1  dev enp1s0 weight 1
	nexthop via 192.168.2.1  dev enp3s0 weight 4
10.8.0.0/24 dev tun0  proto kernel  scope link  src 10.8.0.249 
169.254.0.0/16 dev enp3s0  scope link  metric 1000 
192.168.2.0/24 dev enp3s0  proto kernel  scope link  src 192.168.2.254 
192.168.15.0/24 dev enp1s0  proto kernel  scope link  src 192.168.15.254 
192.168.100.0/24 via 10.8.0.1 dev tun0 
192.168.111.0/24 dev enp2s0  proto kernel  scope link  src 192.168.111.1 





```at the site B router (with direct link to vpn tunnel), ping:


```
kss1x@JFINCRROUTER:~$ ping -c 5 192.168.100.253
PING 192.168.100.253 (192.168.100.253) 56(84) bytes of data.
64 bytes from 192.168.100.253: icmp_seq=1 ttl=64 time=58.5 ms
64 bytes from 192.168.100.253: icmp_seq=2 ttl=64 time=59.2 ms
64 bytes from 192.168.100.253: icmp_seq=3 ttl=64 time=59.2 ms
64 bytes from 192.168.100.253: icmp_seq=4 ttl=64 time=58.6 ms
64 bytes from 192.168.100.253: icmp_seq=5 ttl=64 time=58.4 ms


--- 192.168.100.253 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 58.496/58.837/59.256/0.400 ms
kss1x@JFINCRROUTER:~$ ping -c 5 192.168.100.2
PING 192.168.100.2 (192.168.100.2) 56(84) bytes of data.
64 bytes from 192.168.100.2: icmp_seq=1 ttl=63 time=63.5 ms
64 bytes from 192.168.100.2: icmp_seq=2 ttl=63 time=60.0 ms
64 bytes from 192.168.100.2: icmp_seq=3 ttl=63 time=59.4 ms
64 bytes from 192.168.100.2: icmp_seq=4 ttl=63 time=60.2 ms
64 bytes from 192.168.100.2: icmp_seq=5 ttl=63 time=59.9 ms


--- 192.168.100.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 59.413/60.614/63.500/1.499 ms
kss1x@JFINCRROUTER:~$ ping -c 5 192.168.100.246
PING 192.168.100.246 (192.168.100.246) 56(84) bytes of data.


--- 192.168.100.246 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms



```



Note:
1. 192.168.100.253 is the OPNVPN server box…  successful ping from the remote client vpn box means that the tunnels are working properly


2. 192.168.100.2 is one of the gateways at the server side LAN… successful ping somehow means to me that the routes are setup properly.. if no static routes were setup…  ping should also be unsuccessful


3. 192.168.100.246  is one of the servers at the server side that needs to be accessed by the remote clients…     unsuccessful ping.. I don’t understand why…  even at the successful road warrior setup…  i couldn’t ping the server sid emachines.. and yet i am able to access the services they provdie…   






at the remote client LAN client  (although this client also has vpn credentials to connect to the openvpn server as a road warrior, in here.. i use it as an ordinary lan client)


ifconfig


```
KSS1XMAC:~ kss1x$ ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	options=3<RXCSUM,TXCSUM>
	inet6 ::1 prefixlen 128 
	inet 127.0.0.1 netmask 0xff000000 
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
	nd6 options=1<PERFORMNUD>
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	options=27<RXCSUM,TXCSUM,VLAN_MTU,TSO4>
	ether 34:15:9e:23:1e:80 
	nd6 options=1<PERFORMNUD>
	media: autoselect
	status: inactive
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:26:bb:0a:71:92 
	inet6 fe80::226:bbff:fe0a:7192%en1 prefixlen 64 scopeid 0x5 
	inet 192.168.111.204 netmask 0xffffff00 broadcast 192.168.111.255
	nd6 options=1<PERFORMNUD>
	media: autoselect
	status: active
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 4078
	lladdr 34:15:9e:ff:fe:23:1e:80 
	nd6 options=1<PERFORMNUD>
	media: autoselect <full-duplex>
	status: inactive
p2p0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 2304
	ether 02:26:bb:0a:71:92 
	media: autoselect
	status: inactive



```netstat -nr


```
KSS1XMAC:~ kss1x$ netstat -nr
Routing tables


Internet:
Destination        Gateway            Flags        Refs      Use   Netif Expire
default            192.168.111.1      UGSc            9      227     en1
127                127.0.0.1          UCS             0        0     lo0
127.0.0.1          127.0.0.1          UH              2   101271     lo0
169.254            link#5             UCS             0        0     en1
192.168.111        link#5             UCS             5        0     en1
192.168.111.1/32   link#5             UCS             1        0     en1
192.168.111.1      1c:1b:d:d6:b5:84   UHLWIir        10     4473     en1   1165
192.168.111.201    f4:ec:38:cc:5f:e5  UHLWI           0        0     en1    328
192.168.111.204/32 link#5             UCS             1        0     en1
192.168.111.206    d4:6e:e:8d:8:73    UHLWI           0       54     en1    244
192.168.111.211    0:21:85:99:80:a4   UHLWI           0      559     en1   1004
192.168.111.253    9c:ae:d3:f7:3c:13  UHLWI           0      794     en1    893
192.168.111.255    ff:ff:ff:ff:ff:ff  UHLWbI          0       30     en1
224.0.0            link#5             UmCS            2        0     en1
224.0.0.1          1:0:5e:0:0:1       UHmLWI          0     2960     en1
224.0.0.251        1:0:5e:0:0:fb      UHmLWI          0        0     en1
255.255.255.255/32 link#5             UCS             0        0     en1


Internet6:
Destination                             Gateway                         Flags         Netif Expire
::1                                     ::1                             UHL             lo0
fe80::%lo0/64                           fe80::1%lo0                     UcI             lo0
fe80::1%lo0                             link#1                          UHLI            lo0
fe80::%en1/64                           link#5                          UCI             en1
fe80::226:bbff:fe0a:7192%en1            0:26:bb:a:71:92                 UHLI            lo0
ff01::%lo0/32                           ::1                             UmCI            lo0
ff01::%en0/32                           link#4                          UmCI            en0
ff01::%en1/32                           link#5                          UmCI            en1
ff02::%lo0/32                           ::1                             UmCI            lo0
ff02::%en0/32                           link#4                          UmCI            en0
ff02::%en1/32                           link#5                          UmCI            en1



```

```
KSS1XMAC:~ kss1x$ ping -c 5 192.168.100.253
PING 192.168.100.253 (192.168.100.253): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
Request timeout for icmp_seq 3
64 bytes from 192.168.100.253: icmp_seq=4 ttl=63 time=64.080 ms


--- 192.168.100.253 ping statistics ---
5 packets transmitted, 1 packets received, 80.0% packet loss
round-trip min/avg/max/stddev = 64.080/64.080/64.080/0.000 ms
KSS1XMAC:~ kss1x$ ping -c 5 192.168.100.2
PING 192.168.100.2 (192.168.100.2): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
Request timeout for icmp_seq 3


--- 192.168.100.2 ping statistics ---
5 packets transmitted, 0 packets received, 100.0% packet loss
KSS1XMAC:~ kss1x$ ping -c 5 192.168.100.246
PING 192.168.100.246 (192.168.100.246): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
Request timeout for icmp_seq 3


--- 192.168.100.246 ping statistics ---
5 packets transmitted, 0 packets received, 100.0% packet loss







```

```
KSS1XMAC:~ kss1x$ traceroute 192.168.100.253
traceroute to 192.168.100.253 (192.168.100.253), 64 hops max, 52 byte packets
 1  192.168.111.1 (192.168.111.1)  3.815 ms  0.742 ms  0.720 ms
 2  192.168.100.253 (192.168.100.253)  61.539 ms  59.129 ms  58.841 ms




KSS1XMAC:~ kss1x$ traceroute 192.168.100.253
traceroute to 192.168.100.253 (192.168.100.253), 64 hops max, 52 byte packets
 1  192.168.111.1 (192.168.111.1)  3.815 ms  0.742 ms  0.720 ms
 2  192.168.100.253 (192.168.100.253)  61.539 ms  59.129 ms  58.841 ms
KSS1XMAC:~ kss1x$ traceroute 192.168.100.2
traceroute to 192.168.100.2 (192.168.100.2), 64 hops max, 52 byte packets
 1  192.168.111.1 (192.168.111.1)  4.509 ms  0.948 ms  0.713 ms
 2  10.8.0.1 (10.8.0.1)  59.230 ms  59.519 ms  59.485 ms
 3  * * *
 4  *


 *^C
KSS1XMAC:~ kss1x$ traceroute 192.168.100.246
traceroute to 192.168.100.246 (192.168.100.246), 64 hops max, 52 byte packets
 1  192.168.111.1 (192.168.111.1)  5.441 ms  0.740 ms  0.736 ms
 2  10.8.0.1 (10.8.0.1)  59.623 ms  59.841 ms  59.305 ms
 3  * *^C





```

I am not sure which way to look further to fix this…

---

### Post by wowiesy2 on 2017-12-11
when I read thru my post here.. and then reread the HOWTO on OpenVPN.. it hit me... 
I didn't have static routings setup at the server side LAN gateways for the remote LAN subnets setup (192.168.111.0/24 for Site B and 192.168.254.0/24 for site A)... when I came into work this morning at the Server side.. I put them in and now I think its working... 

I will get to test it later on..

---

