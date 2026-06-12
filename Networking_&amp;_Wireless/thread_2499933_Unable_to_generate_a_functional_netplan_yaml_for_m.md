---
title: "Unable to generate a functional netplan yaml for my laptop"
date: 2024-08-15
forum: Networking &amp; Wireless
---

### Post by fanatic26 on 2024-08-15
Its a MS Surface laptop with a built in Marvell WiFI (w1p1s0) that works fine. The second device (enx00e04c681826) is a USB ethernet adapter with the RTL8153 firmware.

Drivers are install, devices show up, wifi works just fine on its own.

:/etc/network# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enx00e04c681826: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:e0:4c:68:18:26 brd ff:ff:ff:ff:ff:ff
3: wwan0: <BROADCAST,MULTICAST,NOARP> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 4e:ba:8c:d4:d0:1d brd ff:ff:ff:ff:ff:ff
4: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1492 qdisc mq state UP group default qlen 1000
    link/ether 70:bc:10:5d:f6:52 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.161/24 metric 600 brd 192.168.1.255 scope global dynamic wlp1s0
       valid_lft 68466sec preferred_lft 68466sec

Its a basic class C network with a single subnet. The wifi is fine being DHCP but I am trying to setup the ethernet with a static IP for external routing purposes. 

Ive been digging through examples on the netplan github but I just cant seem to make it work. I have spent about 3 hours now attempting various things and none of it works. I have used online yaml checkers that verify syntax and spacing but every time I 'netplan try' my changes
I lose the IP on my wifi and have to physically console back in. Does anyone have any suggestions or maybe theres an online netplan yaml builder somewhere? Last time I setup anything like this in linux it still used /etc/network/interfaces and boy do I miss it. I would have it up in 5 
minutes if this system wasnt depreciated. Netplan is a nightmare in comparison.

---

### Post by currentshaft on 2024-08-15
1

---

### Post by fanatic26 on 2024-08-15
I have deleted all of my failed attempts, the only config I currently have is the wifi config.

```

network:
    ethernets: {}
    version: 2
    wifis:
        wlp1s0:
            access-points:
                XXXXXX:
                    password: XXXXXXXX
            dhcp4: true
```

---

