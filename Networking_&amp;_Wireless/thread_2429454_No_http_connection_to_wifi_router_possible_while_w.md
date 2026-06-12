---
title: "No http connection to wifi router possible while wifi operational"
date: 2019-10-18
forum: Networking &amp; Wireless
---

### Post by ndb2 on 2019-10-18
For some unknown reason I can't ping nor make a http connection to the wifi router I use.
Connection request seem to be blocked in Xubuntu 19.04, though NOT using an Android smartphone. Using Android it works fine.
Other than that, the internet connection works fine.
Remarkable: The router (gateway) has IP 192.168.2.254. Output using console (Xubuntu) shows a different gateway, 192.168.1.1:
[B]
Idea requested,[/B] where to look for what's causing this problem.

Output:
```

 ifconfig

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.2  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::a7b1:b116:53c2:7510  prefixlen 64  scopeid 0x20<link>
        ether 00:26:b9:db:3a:95  txqueuelen 1000  (Ethernet)
        RX packets 2174  bytes 309902 (309.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2483  bytes 277203 (277.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xe9600000-e9620000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1603  bytes 121951 (121.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1603  bytes 121951 (121.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.68  netmask 255.255.255.0  broadcast 192.168.1.255
        ether a8:57:4e:12:f2:16  txqueuelen 1000  (Ethernet)
        RX packets 66103  bytes 29541698 (29.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 58956  bytes 8582749 (8.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

netstat -r -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlp3s0

```

---

### Post by milesweb on 2019-10-18
Seems you are only being assigned an ipv6 ip address with your Ethernet. Did you change some settings?

---

### Post by TheFu on 2019-10-18
The wired connection is going to 192.168.2.2/24.
The wireless connection is going to 192.168.1.68/24.
The routing tables show the wired wifi connection is controlling the gateway.

Run
```
sudo iwlist scan| egrep 'SSID|wlan|Channel|Quality|Cell'
```
to see which wifi SSID the connection is actually getting. Appears NOT to be the one you want. Could be a neighbor or some hacker having fun.

---

### Post by ndb2 on 2019-10-18
Not that I know of. I saw that when I'm not connected using a cable but only wireless, the wireless interface does have an IPv6 address.

---

### Post by ndb2 on 2019-10-18
TheFu: Yes... I was connected to the wrong wifi network. Corrected that. Same outcome.
- Cabled interfasce has IPv4 address and no IPv6 address.
- Wifi interface has both versions of addresses - IP 192.168.2.4 
- Ping nor http connect to 192.168.2.254 provokes response.

However... looking further I flushed iptables. And then... connection is possible.

So. After all... this situation is both explainable and fixable.

Sorry to have bothered you! Topic closed.

---

