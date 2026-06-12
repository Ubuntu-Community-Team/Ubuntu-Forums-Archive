---
title: "wlan connection lost after some time when connecting wired ethernet"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by layo on 2016-05-15
I have a wireless connection (wlan0) to my router which normally works fine for internet access. However, I want to connect my wired connection (eth0) to my raspberry using a static IP address. I've set that up using Network Manager on Ubuntu 14.04, and for connection eth0 I've checked the option 'Use this connection only for resources on its network'. 

Before connecting eth0 I have the following output of routes -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```

After connection I have this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```

After that I ping [www.google.com](www.google.com), which succeeds several times, but then it just stops suddenly. See the last successful ping below:
```
64 bytes from ea-in-f147.1e100.net (74.125.136.147): icmp_seq=10 ttl=50 time=13.2 ms
```

It just stops, and internet connection is not available any-more after that, until disconnecting eth0. 
The routing table didn't change between the successful ping and the failed ping.

I'm quite puzzled by this, can anyone point to a direction where this problem might originate?

---

### Post by blackgr on 2016-05-15
Hello,

Since you are using two non-bridged interfaces, I believe you should be using a different IP range for the second (eth0) interface, like 192.168.2.0/24 and then share the wlan0 connection (I assume this is the internet one).

To share wlan0, as root:

1) echo "1" > /proc/sys/net/ipv4/ip_forward
2) iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

There might be some extra tweaking from the rasberry side too, but that's the general idea.

Thanks,
Alex

---

