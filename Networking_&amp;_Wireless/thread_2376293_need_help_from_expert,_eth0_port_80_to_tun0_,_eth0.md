---
title: "need help from expert, eth0 port 80 to tun0 , eth0 port 8080 to tun1"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by khong20 on 2017-11-01
i installed ubuntu with 2 openvpn client tun0 and tun1.

```
eno1      Link encap:Ethernet  HWaddr f4:6d:04:40:d4:99  
          inet addr:192.168.0.228  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:e68:542c:269e:6565:9164:5677:3390/64 Scope:Global
          inet6 addr: fe80::766b:fcc:c875:e097/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:506877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:477270846 (477.2 MB)  TX bytes:85044619 (85.0 MB)
          Interrupt:20 Memory:f7f00000-f7f20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1641134 (1.6 MB)  TX bytes:1641134 (1.6 MB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.3  P-t-P:10.8.0.3  Mask:255.255.255.0
          inet6 addr: fe80::10ab:9467:cb70:ad05/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:281613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:329333778 (329.3 MB)  TX bytes:18036070 (18.0 MB)


tun1      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.7.0.3  P-t-P:10.7.0.3  Mask:255.255.255.0
          inet6 addr: fe80::170c:11d4:c7ec:8911/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
[COLOR=#000000][FONT=Menlo]RX bytes:56575 (56.5 KB)[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]TX bytes:40887 (40.8 KB)
[/FONT][/COLOR]
```

everything setup properly at server side and working well with only one VPN client but with 2 client connected tun0 working and tun1 only work with ping 10.7.0.1.
my ip route 

```

default via 192.168.0.1 dev eno1  proto static  metric 100 
10.7.0.0/24 dev tun1  proto kernel  scope link  src 10.7.0.3 
10.8.0.0/24 dev tun0  proto kernel  scope link  src 10.8.0.3 
45.77.4.83 via 192.168.0.1 dev eno1 
45.77.118.170 via 192.168.0.1 dev eno1 
128.0.0.0/1 via 10.8.0.1 dev tun0 
169.254.0.0/16 dev eno1  scope link  metric 1000 
192.168.0.0/24 dev eno1  proto kernel  scope link  src 192.168.0.228  metric 100 

```

anyone who know IPtables by setting
 eno1 port 80 to tun0 , eno1 port 8080 to tun1 
 tun0 port 80 to eno1 port 80 , tun1 port 8080 to eno port 8080
thanks alot. your help really  appreciate.
p/s : fixing this error 2 days and headache

---

### Post by khong20 on 2017-11-01
bump ..

---

