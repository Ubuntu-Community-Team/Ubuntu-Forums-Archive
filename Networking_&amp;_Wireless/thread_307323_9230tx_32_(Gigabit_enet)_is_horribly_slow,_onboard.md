---
title: "9230tx 32 (Gigabit enet) is horribly slow, onboard is much faster (but 100mbit/s)"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by KingCrimson on 2006-11-26
Hi there,

I'm getting mad :-k 

I've got a 9230tx 32 ethernet-card, it's autoconfigured by ubuntu, using a r8169 driver.

[   38.898650] eth1: Identified chip type is 'RTL8169s/8110s'.
[   38.898654] eth1: RTL8169 at 0xffffc2000003cc00, 00:0e:2e:87:90:b6, IRQ 201

~$ ip a
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:18:f3:02:e7:83 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0e:2e:87:90:b6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.101/24 brd 192.168.1.255 scope global eth1
    inet6 fe80::20e:2eff:fe87:90b6/64 scope link 
       valid_lft forever preferred_lft forever
4: sit0: <NOARP> mtu 1480 qdisc noop 
    link/sit 0.0.0.0 brd 0.0.0.0

It works, but VERY VERY VERY slow, filesharing with Samba using a PowerMac G5 stucks at about 180kB/s, same with nfs ... 

With the exact same configuration - exept using the onboard ethernet eth0 - I reach about 10mbyte/s. :confused: My PowerMac reads at about 15mbyte/s from my Powerbook, so it shouldn't be a "mac-problem". 

I tried the r1000 module, no change, slow speed but working connection. mii-diag tells my, that SIOCGMIIPHY on eth1 failed: Operation not supported, no error msg in dmesg ...

I've been fighting this prob for about a week, ](*,) it seems I'm just too n00by to solve it on my own, is there anybody out there knowing how to fix this!?

Anybody helping can be shure to be my personal hero ;-)

THANX in advance,

     Andreas

---

