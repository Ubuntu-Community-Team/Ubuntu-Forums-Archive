---
title: "Some websites blocked since last update"
date: 2021-12-30
forum: Networking &amp; Wireless
---

### Post by jiggets on 2021-12-30
This is my first time using unbutu!!  I have no idea what is wrong or how to fix and none of the "solutions" I found when searching have worked.:(

I have a laptop that was being used as a streaming device, I believe it have 20.04.3 LTS currently.  Since the last time it updated it is blocking video from the site I was using for movies and giving me "server cannot be found" when trying to login to my hotmail and firefox accounts.  It gives the same error when trying to access any microsoft page and even these forums.  I did run the stuff reccomended in the "before posting in networking" sticky post and did not help.  The issue is the same whether wired or wireless.  Everything was fine before last update.

---

### Post by chili555 on 2021-12-31
Please run and post:

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
ip addr show
ls -al /etc/resolv.conf
```

---

### Post by jiggets on 2021-12-31
> k@McSnatch:~$ ping -c3 8.8.8.8
ping: connect: Network is unreachable
k@McSnatch:~$ ping -c3 8.8.8.8
ping: connect: Network is unreachable
k@McSnatch:~$ ping -c3 [www.unbutu.com](www.unbutu.com)
ping: connect: Network is unreachable
k@McSnatch:~$ ipaddr show

k@McSnatch:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether c8:0a:a9:ce:14:1a brd ff:ff:ff:ff:ff:ff
3: wlp9s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 5c:ac:4c:32:2e:ea brd ff:ff:ff:ff:ff:ff
    inet6 2601:242:682:3980:bb34:a41b:600f:785/64 scope global temporary dynamic 
       valid_lft 345581sec preferred_lft 40593sec
    inet6 2601:242:682:3980:cd70:a167:69f3:eb59/64 scope global temporary deprecated dynamic 
       valid_lft 345581sec preferred_lft 0sec
    inet6 2601:242:682:3980:a40e:1da2:3133:4b01/64 scope global temporary deprecated dynamic 
       valid_lft 345581sec preferred_lft 0sec
    inet6 2601:242:682:3980:a43:f81f:1fe6:3ae/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 345581sec preferred_lft 345581sec
    inet6 fe80::d9df:a4a9:da1d:da22/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
k@McSnatch:~$ ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Aug 17 13:24 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf


Is this what you need?

---

### Post by chili555 on 2022-01-01
Fascinating! You have a seemingly valid IPv6 address but no IPv4 address! Please check Settings > WiFi Settings and be certain that IPv4 is set to Automatic (DHCP): 

[IMG]https://i.postimg.cc/rFhLdKdD/Screenshot-from-2022-01-01-10-00-18.png[/IMG]

Reboot and tell us if there is any improvement.

---

### Post by jiggets on 2022-01-01
My IPv4 looks just the same as the picture without any changes.

Edit:  I rebooted without making any changes and it seems to be working.  I'm not sure what happened but I have tried many things and restarted several times now, then it starts working after making no changes....

---

### Post by chili555 on 2022-01-01
Glad it's working. Post back if it happens again.

---

