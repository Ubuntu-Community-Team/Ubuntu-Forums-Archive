---
title: "DNAT not working on Ubuntu 16"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by sloppytypist on 2017-02-21
Hi,

I've a strange problem.  I've done this many times before, but not  today.  I'm trying to DNAT 1:1 to a device.  In this case the device is  at 172.21.0.25.  I can ping the device no problem from the Ubuntu  16.04(4.8 kernel)but when I setup the following DNAT it responds to my  test ping with ICMP host unreachable.  

I confirmed 

So it should the server on 172.30.5.206 then > 172.21.0.25.

This is my iptables nat rules:

```
root@ip-172-30-5-161:/home/ubuntu# iptables -t nat -S -v
-P PREROUTING ACCEPT -c 0 0
-P INPUT ACCEPT -c 0 0
-P OUTPUT ACCEPT -c 1 60
-P POSTROUTING ACCEPT -c 1 60
-A PREROUTING -d 172.30.5.206/32 -c 1 60 -j DNAT --to-destination 172.21.0.25
root@ip-172-30-5-161:/home/ubuntu#
```

All other policies are set to ACCEPT:
```

root@ip-172-30-5-161:/home/ubuntu# iptables -S -v
-P INPUT ACCEPT -c 8649 550346
-P FORWARD ACCEPT -c 20 1200
-P OUTPUT ACCEPT -c 8367 580846
root@ip-172-30-5-161:/home/ubuntu#
```

Here is my routing table:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.30.5.1      0.0.0.0         UG    0      0        0 eth0
172.21.0.0      *               255.255.254.0   U     0      0        0 vti1
172.30.5.0      *               255.255.255.0   U     0      0        0 eth0
```

Here are my IPs
```

root@ip-172-30-5-161:/home/ubuntu# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 06:f2:02:c4:12:88 brd ff:ff:ff:ff:ff:ff
    inet 172.30.5.161/24 brd 172.30.5.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet 172.30.5.206/24 brd 172.30.5.255 scope global secondary eth0:10
       valid_lft forever preferred_lft forever
    inet6 fe80::4f2:2ff:fec4:1288/64 scope link
       valid_lft forever preferred_lft forever
3: ovs-system: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 56:af:d1:d4:4e:4c brd ff:ff:ff:ff:ff:ff
4: OVSBR: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 76:a0:55:27:b8:47 brd ff:ff:ff:ff:ff:ff
5: ip_vti0@NONE: <NOARP> mtu 1332 qdisc noop state DOWN group default qlen 1
    link/ipip 0.0.0.0 brd 0.0.0.0
6: vti1@NONE: <NOARP,UP,LOWER_UP> mtu 1332 qdisc noqueue state UNKNOWN group default qlen 1
    link/ipip 172.30.5.161 brd 0.0.0.0
    inet 172.21.0.1/23 scope global vti1
       valid_lft forever preferred_lft forever
```

Here is proof I'm ready to route:

```
root@ip-172-30-5-161:/home/ubuntu# sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1
```

Here is proof that the host is reachable:
```

root@ip-172-30-5-161:/home/ubuntu# ping 172.21.0.25
PING 172.21.0.25 (172.21.0.25) 56(84) bytes of data.
64 bytes from 172.21.0.25: icmp_seq=1 ttl=64 time=35.8 ms

```

Related note, when I change the DNAT to be the IP(172.21.0.1) on vti1  that is directly connected to the 172.21.0.0/23 subnet, it works, but  tcpdump does not show traffic on vti1 even when ping returned. What am I missing?  Thanks.

CB

---

### Post by DuckHook on 2017-02-21
Welcome to the forums, sloppytypist.

For ease of readability, please use standard fonts and post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

