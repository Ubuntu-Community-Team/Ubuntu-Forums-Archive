---
title: "Why is USB tethering no longer working on ubuntu?"
date: 2018-06-14
forum: Networking &amp; Wireless
---

### Post by abinashdash17 on 2018-06-14
I'm using Ubuntu 17.10(manual installation from mini.iso) . Before some days USB tethering was working fine without any issue. I just needed to connect my android pc and then enable usb tethering and it worked well without any issue. Suddenly it's no longer working. Wireless network is working fine. Any hint what happened?
Here's my 'ip address' output:  
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0f2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 80:ee:73:77:4a:22 brd ff:ff:ff:ff:ff:ff
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 48:d2:24:c7:87:78 brd ff:ff:ff:ff:ff:ff
    inet 192.168.43.5/24 brd 192.168.43.255 scope global wlp3s0
       valid_lft forever preferred_lft forever
    inet6 2405:203:6404:21d8:f060:2d94:f332:5ece/64 scope global temporary dynamic 
       valid_lft 603255sec preferred_lft 84589sec
    inet6 2405:202:6404:21d8:4ad2:24ff:fec7:8778/64 scope global mngtmpaddr dynamic 
       valid_lft forever preferred_lft forever
    inet6 fe80::4ad3:24ff:fec7:8778/64 scope link 
       valid_lft forever preferred_lft forever
```

---

