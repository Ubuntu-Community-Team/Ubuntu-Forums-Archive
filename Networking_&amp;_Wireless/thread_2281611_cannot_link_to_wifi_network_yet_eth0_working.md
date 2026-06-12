---
title: "cannot link to wifi network yet eth0 working"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by houmingc on 2015-06-08
I load a new software and i cannot link to wifi
The connection icon on the top right is not showing.

sudo ifdown eth0 && sudo ifup eth0


root@ubuntu:/home/ubuntu# service networking status
networking start/running
root@ubuntu:/home/ubuntu# service network-manager status
network-manager stop/waiting
root@ubuntu:/home/ubuntu# service network-manager restart

root@ubuntu:/home/ubuntu# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 28:d2:44:7f:23:d0 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.103/24 brd 255.255.255.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::2ad2:44ff:fe7f:23d0/64 scope link 
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether e8:2a:ea:81:3d:82 brd ff:ff:ff:ff:ff:ff

---

### Post by howefield on 2015-06-08
Thread moved to the "*Networking & Wireless*" forum where you'll have a better chance of getting help.

---

