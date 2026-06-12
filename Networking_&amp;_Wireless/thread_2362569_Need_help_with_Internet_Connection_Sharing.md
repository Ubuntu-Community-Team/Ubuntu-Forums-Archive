---
title: "Need help with Internet Connection Sharing"
date: 2017-05-30
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2017-05-30
Hi 

I am following [this guide]("https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet") to set up Internet connection Sharing.

```
$ ifconfig enp0s7: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.16.197.126  netmask 255.255.255.0  broadcast 172.16.197.255
        inet6 fe80::60bd:39c1:b660:bf99  prefixlen 64  scopeid 0x20<link>
        ether 40:61:86:bd:3c:a2  txqueuelen 1000  (Ethernet)
        RX packets 497567  bytes 577345561 (577.3 MB)
        RX errors 0  dropped 11661  overruns 0  frame 0
        TX packets 259084  bytes 22231779 (22.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enx00e04c534458: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.42.0.1  netmask 255.255.255.0  broadcast 10.42.0.255
        inet6 fe80::41f4:1f9b:aa63:d591  prefixlen 64  scopeid 0x20<link>
        ether 00:e0:4c:53:44:58  txqueuelen 1000  (Ethernet)
        RX packets 6021  bytes 1905906 (1.9 MB)
        RX errors 8  dropped 5  overruns 2  frame 9
        TX packets 8464  bytes 1011130 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5227  bytes 403169 (403.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5227  bytes 403169 (403.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

enp0s7 is my port for WAN connection and enx00e04c534458 is for sharing the connection. 

Under enx00e04c534458 I have selected  "Shared to other computers" and this port is directly connected to my WiFi router's WAN port.

Problem is no matter what I try I cant get the Internet connection from the router's LAN side.

The router is set to DHCP on the LAN side.

Any ideas ?

---

### Post by Keith_Helms on 2017-05-30
The guide was for directly connecting computer B to computer A through ethernet.  It sounds like you instead have connected a router to computer A.  Is that correct?  Did you enter the IP address of computer A into the router as the DNS server address?

---

### Post by linuxyogi on 2017-05-30
> **Keith_Helms said:**
> The guide was for directly connecting computer B to computer A through ethernet.  It sounds like you instead have connected a router to computer A.  Is that correct?  Did you enter the IP address of computer A into the router as the DNS server address?

Yes I have tried to enter the entire address manually (on the router)  like this 

```
IP : 10.42.0.2
netmask :  255.255.255.0
Gateway : 10.42.0.1
Primary DNS : 10.42.0.1
Secondary DNS : 8.8.8.8
```

This way I can ping the router address 10.42.0.2 but still no Internet connection on the router side.

Its working now. Looks like my WiFi devices forgot the network. I had to reconnect them.

---

