---
title: "Netplan problem"
date: 2024-05-15
forum: Networking &amp; Wireless
---

### Post by georgy-trubetkoy-ru74 on 2024-05-15
I configured static ip on my NIC via netplan.
But it still accept dhcp.

Config itself:

network:
    version: 2
    renderer: networkd
    ethernets:
        eth0:
            link-local: [ ipv4 ]
            dhcp4: no
            dhcp6: no
            addresses: [192.168.1.6/24]
            nameservers:
                addresses: [192.168.1.1]
            routes:
                - to: default
                  via: 192.168.1.1

Result of "ip a":

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:15:5d:01:a7:21 brd ff:ff:ff:ff:ff:ff
    inet 169.254.212.20/16 metric 2048 brd 169.254.255.255 scope link eth0
       valid_lft forever preferred_lft forever
    inet 192.168.1.6/24 brd 192.168.1.255 scope global eth0
       valid_lft forever preferred_lft forever

---

### Post by georgy-trubetkoy-ru74 on 2024-05-16
It seems like I solved it via remove ipv4 in link-local: [].
But I left:
dhcp4: off
dhcp6: off
Strange. I should always carefully read the documentation.

---

