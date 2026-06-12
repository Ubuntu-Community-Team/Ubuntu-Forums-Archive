---
title: "After Network bonding, Unusual pinging"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by jspking on 2008-05-29
I configured network bonding with [http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)


root@eidicom-server:/dev/usb# ifconfig
bond0 Link encap:Ethernet HWaddr 00:02:b3:52:73:a3 
inet addr:192.168.1.19 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::202:b3ff:fe52:73a3/64 Scope:Link
UP BROADCAST RUNNING MASTER MULTICAST MTU:1500 Metric:1
RX packets:1861256 errors:0 dropped:0 overruns:3 frame:3
TX packets:1452949 errors:26 dropped:0 overruns:0 carrier:26
collisions:252332 txqueuelen:0 
RX bytes:313868061 (299.3 MB) TX bytes:956594703 (912.2 MB)

bond0:0 Link encap:Ethernet HWaddr 00:02:b3:52:73:a3 
inet addr:2xx.xxx.xx.xx Bcast:2xx.xxx.xxx.xx Mask:255.255.255.240
UP BROADCAST RUNNING MASTER MULTICAST MTU:1500 Metric:1

eth0 Link encap:Ethernet HWaddr 00:02:b3:52:73:a3 
UP BROADCAST RUNNING SLAVE MULTICAST MTU:1500 Metric:1
RX packets:931024 errors:0 dropped:0 overruns:3 frame:3
TX packets:726756 errors:15 dropped:0 overruns:0 carrier:15
collisions:137888 txqueuelen:1000 
RX bytes:155097627 (147.9 MB) TX bytes:475923416 (453.8 MB)

eth1 Link encap:Ethernet HWaddr 00:02:b3:52:73:a3 
UP BROADCAST RUNNING SLAVE MULTICAST MTU:1500 Metric:1
RX packets:930232 errors:0 dropped:0 overruns:0 frame:0
TX packets:726193 errors:11 dropped:0 overruns:0 carrier:11
collisions:114444 txqueuelen:100 
RX bytes:158770434 (151.4 MB) TX bytes:480671287 (458.4 MB)
Base address:0x2460 Memory:fe020000-fe040000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1270 errors:0 dropped:0 overruns:0 frame:0
TX packets:1270 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:68316 (66.7 KB) TX bytes:68316 (66.7 KB)




root@eidicom-server:/dev/usb# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.858 ms
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.867 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=1.18 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=1.19 ms (DUP!)






Samba, ssh, ftp are running on this server. It works. 

I really wonder where this is OK.


thanks.

---

