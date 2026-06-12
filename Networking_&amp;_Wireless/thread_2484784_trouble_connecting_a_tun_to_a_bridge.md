---
title: "trouble connecting a tun to a bridge"
date: 2023-03-09
forum: Networking &amp; Wireless
---

### Post by jusp on 2023-03-09
I am trying to connect a tun to a network bridge, pretty much following [https://krackout.wordpress.com/2020/03/08/network-bridges-and-tun-tap-interfaces-in-linux/](https://krackout.wordpress.com/2020/03/08/network-bridges-and-tun-tap-interfaces-in-linux/) (Bridge using routed subnet, VM <-> host-LAN-Internet).

The connection attempt fails as follows:

$ sudo ip link set tun0 master br0
**RTNETLINK answers: Invalid argument**

The bridge I am using is one that has proven to work in giving a qemu client full internet access (in that case it connects to a tap), see below, but I get the same error message when I create and bring up br0 from scratch by 
    ip link add br0 type bridge
and then giving it an ip address and bringing it up.

4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 1e:0d:a5:d0:0e:52 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.16/24 brd 192.168.1.255 scope global dynamic noprefixroute br0
       valid_lft 81486sec preferred_lft 81486sec
    inet6 fe80::1c0d:a5ff:fed0:e52/64 scope link 
       valid_lft forever preferred_lft forever

Same for tun0, it makes no difference if I create it from scratch on the command line, or create a temporary one in a C program by ioctl'ing /dev/net/tun.

According to various web pages that I can find on it, including the one above, this should all pretty much work. 
What am I doing wrong?

---

### Post by jusp on 2023-03-10
Ah, cool, connecting a tap to a bridge works. So tuns appear to be incompatible with bridges, with the tools giving an unintelligible error message.

---

