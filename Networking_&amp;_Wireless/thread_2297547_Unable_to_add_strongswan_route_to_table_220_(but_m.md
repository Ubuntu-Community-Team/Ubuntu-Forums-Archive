---
title: "Unable to add strongswan route to table 220 (but main table works)"
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by donbowman on 2015-10-04
Strongswan is failing to install my routes, giving this error:
```
installing new virtual IP 192.168.130.3
received netlink error: Invalid argument (22)
unable to install source route for 192.168.130.3

```
If i try and run the command manually, I find that

```
ip r add 10/8 via 172.16.0.1 dev eno1 proto static src 192.168.130.3 table 220
```
fails with

```
RTNETLINK answers: Invalid argument
```

but the same command without 'table 220' on the end works [and then I can ping the remote subnet 10/8].

[FONT=courier new]ip route show table 220[/FONT] returns nothing (that table is blank). I'm not sure where to look. Why would this command fail when attaching to table 220, but pass in the main table?

Worse, I have two systems, identically setup w/ software. 1 works (my laptop), 1 fails (my desktop).

I'm running 15.10, kernel 4.3.0-040300rc2-generic #201509201830. iproute2 is version 4.1.1-1ubuntu1.

```
# ip rule ls
0:      from all lookup local 
220:    from all lookup 220 
32766:  from all lookup main 
32767:  from all lookup default 

# ifconfig eno1
eno1      Link encap:Ethernet  HWaddr 30:85:a9:9a:02:03  
          inet addr:172.16.0.8  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::3285:a9ff:fe9a:203/64 Scope:Link
          inet6 addr: 2001:470:1d:6fd:800d:f631:5022:6736/64 Scope:Global
          inet6 addr: 2001:470:1d:6fd:3285:a9ff:fe9a:203/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:228776 errors:0 dropped:1475 overruns:0 frame:0
          TX packets:88649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138398637 (138.3 MB)  TX bytes:21136254 (21.1 MB)
          Interrupt:18 Memory:fbf00000-fbf20000 

# ip r
default via 172.16.0.1 dev eno1  proto static  metric 100 
169.254.0.0/16 dev docker0  scope link  metric 1000 
172.16.0.0/16 dev eno1  proto kernel  scope link  src 172.16.0.8  metric 100 
172.16.0.2 via 172.16.0.1 dev eno1  proto static  metric 100 
172.16.10.0/24 dev virbr0  proto kernel  scope link  src 172.16.10.1 
172.17.0.0/16 dev docker0  proto kernel  scope link  src 172.17.42.1 

# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 90:e2:ba:07:57:98 brd ff:ff:ff:ff:ff:ff
3: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 30:85:a9:9a:02:03 brd ff:ff:ff:ff:ff:ff
    inet 172.16.0.8/16 brd 172.16.255.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet 192.168.130.3/32 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 2001:470:1d:6fd:800d:f631:5022:6736/64 scope global temporary dynamic 
       valid_lft 602sec preferred_lft 602sec
    inet6 2001:470:1d:6fd:3285:a9ff:fe9a:203/64 scope global mngtmpaddr noprefixroute dynamic 
       valid_lft 602sec preferred_lft 602sec
    inet6 fe80::3285:a9ff:fe9a:203/64 scope link 
       valid_lft forever preferred_lft forever
4: enp4s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 90:e2:ba:07:57:99 brd ff:ff:ff:ff:ff:ff
5: enp5s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 90:e2:ba:07:57:9c brd ff:ff:ff:ff:ff:ff
6: enp5s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 90:e2:ba:07:57:9d brd ff:ff:ff:ff:ff:ff
7: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 56:84:7a:fe:97:99 brd ff:ff:ff:ff:ff:ff
    inet 172.17.42.1/16 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::5484:7aff:fefe:9799/64 scope link 
       valid_lft forever preferred_lft forever
8: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:a5:15:7f brd ff:ff:ff:ff:ff:ff
    inet 172.16.10.1/24 brd 172.16.10.255 scope global virbr0
       valid_lft forever preferred_lft forever
    inet6 2001:470:1d:6fd::1/64 scope global tentative 
       valid_lft forever preferred_lft forever
9: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc noqueue master virbr0 state DOWN group default qlen 500
    link/ether 52:54:00:a5:15:7f brd ff:ff:ff:ff:ff:ff
11: veth6513477@if10: <BROADCAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 9a:9f:02:90:7a:c3 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::989f:2ff:fe90:7ac3/64 scope link 
       valid_lft forever preferred_lft forever




```

---

