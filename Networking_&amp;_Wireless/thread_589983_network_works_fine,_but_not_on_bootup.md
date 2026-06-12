---
title: "network works fine, but not on bootup"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by TheWizzard on 2007-10-24
i have a strange problem. 
my internet doesn't start on bootup, but as soon as i'm logged in i can start the network. 


```

wizzard@chestcutter:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
wizzard@chestcutter:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3009ms
, pipe 3
wizzard@chestcutter:~$ sudo /etc/init.d/networking restart
[sudo] password for wizzard:
 * Reconfiguring network interfaces...                                   [ OK ]
wizzard@chestcutter:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.76 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.963 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.35 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.963/1.358/1.760/0.328 ms
wizzard@chestcutter:~$  

```

and here's /etc/network/interfaces
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface wlan0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Homelan99
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxx

auto wlan0

```

does anyone have a clue? and a solution? 

i can put /etc/init.d/networking restart in /etc/rc.local, but that's a crude workaround. 

cheers

---

