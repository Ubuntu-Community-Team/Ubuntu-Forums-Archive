---
title: "adsl bridge setup on enp1s0 with concurrent wlan on wlo1"
date: 2020-11-25
forum: Networking &amp; Wireless
---

### Post by djshaw1987 on 2020-11-25
Hi Everybody!

I am struggling with my network setup. I am working at home more often as of late, and my internet connection is unstable. I arranged for a backup internet connection, and I'm trying to setup something that will let me use both connections either concurrently or in a fail-over like scenario. For the time being, I have my second internet connection connected directly into my machine via enp1s0, and I'm using wlo1 to research what I am doing.

For the time being, I'd like only my machine to use the backup internet connection. My hope is that this is easier. I setup the ADSL modem in bridge mode and with ip address 192.168.2.1. I added route specific to the modem with:
```

$ sudo ip route add 192.168.2.1/32 dev enp1s0
$ ip route list
default via 192.168.1.1 dev wlo1 proto dhcp metric 600 
169.254.0.0/16 dev wlo1 scope link metric 1000 
192.168.1.0/24 dev wlo1 proto kernel scope link src 192.168.1.130 metric 600 
192.168.2.1 dev enp1s0 scope link

```

Checking the output of ifconfig (old habits die hard), I see that enp1s0 doesn't have an ip address, so I set one with:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.3.100/24]
      gateway4: 192.168.2.1
      nameservers:
          addresses: [8.8.8.8]

```

(I put in arbitrary values for gateway4 and the nameserver)

And a sudo netplan apply for these changes to take effect. ifconfig shows that the ipaddress is set.

```

$ ifconfig
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.3.100  netmask 255.255.255.0  broadcast 192.168.3.255
        inet6 fe80::7ae3:b5ff:fe61:d36c  prefixlen 64  scopeid 0x20<link>
        ether 78:e3:b5:61:d3:6c  txqueuelen 1000  (Ethernet)
        RX packets 5  bytes 300 (300.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1138  bytes 118377 (118.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 410  bytes 36571 (36.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 410  bytes 36571 (36.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.130  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::173a:8380:3be2:af5  prefixlen 64  scopeid 0x20<link>
        ether 60:d8:19:20:d1:7e  txqueuelen 1000  (Ethernet)
        RX packets 47620  bytes 39226945 (39.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 46227
        TX packets 38280  bytes 5891935 (5.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

```

At this point, I was expecting to be able to ping the ADSL modem. I assumed that the routing rule that I created would route anything to 192.168.2.1 over enp1s0 and everything else would stay on wan. Unfortunately, the ping was unsuccessful:
```

$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
^C
--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2041ms

```

And invoking ping with -I did not change the outcome:
```

$ ping -I enp1s0 192.168.2.1
PING 192.168.2.1 (192.168.2.1) from 192.168.3.100 enp1s0: 56(84) bytes of data.
^C
--- 192.168.2.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1013ms

```

Can anyone offer any advice to how I can proceed to use both my existing wlan alongside the adsl modem? Any help would be greatly appreciated.

I am using Ubuntu 18.04

---

