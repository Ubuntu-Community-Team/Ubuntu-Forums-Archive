---
title: "Intel X553 Network chip doesn't autoconfigure"
date: 2018-04-18
forum: Networking &amp; Wireless
---

### Post by CrisisCore on 2018-04-18
I have PC I am trying to install Ubuntu Server 17.10 on. It uses this mainboard:
supermicro.com/products/motherboard/atom/A2SDi-4C-HLN4F.cfm
Which has an Inter Atom C3000 SoC with an Intel X553 Networking chip. Now with 17.10, this chip is recognized automatically, so there is no need to install the driver manually as with 16.04:
[https://www.servethehome.com/day-0-with-intel-atom-c3000-getting-nics-working/](https://www.servethehome.com/day-0-with-intel-atom-c3000-getting-nics-working/)
(Later I did test what happened if I manually installed the latest driver, but it didn't change my problem).

This mainboard provides 4/5 Ethernet ports. I'm using the first one, though I tried all of them. I'm positive my cable is plugged into the first one, because it says so in the mainboards docs and in the BIOS, the first port is said to be connected. My ethernet network has a router providing DHCP which I would like to use, and I am positive that the cable I'm using is working, since it works fine with another Ubuntu laptop.

When in the installer I have to configure my networking to proceed, however when pick eno1 (which is the one with the cable in it, though I tried the others, experiencing the same symptoms) it fails when trying to configure DHCP, timing out.

I also tried installing the OS with a wifi dongle, which works, but I still couldn't figure out a way to switch to ethernet. I documented my attempts to configure networking after the install here: [https://unix.stackexchange.com/questions/438360/how-to-configure-networking-and-internet-access-with-the-intel-x553-networking-c](https://unix.stackexchange.com/questions/438360/how-to-configure-networking-and-internet-access-with-the-intel-x553-networking-c)

```
[COLOR=#242729][FONT=Arial]I'm having trouble getting networking configured on my NAS using this mainboard:[/FONT][/COLOR][https://www.supermicro.com/products/motherboard/atom/A2SDi-4C-HLN4F.cfm](https://www.supermicro.com/products/motherboard/atom/A2SDi-4C-HLN4F.cfm)[COLOR=#242729][FONT=Arial] which is running an Intel Atom C3000 CPU and an intel x553 networking chipset, with Ubuntu Server 17.10. The chip is already recognized and has been even by the installer, however, since it wasn't working I also followed these instructions to install the latest intel driver: [/FONT][/COLOR][https://www.servethehome.com/day-0-with-intel-atom-c3000-getting-nics-working/](https://www.servethehome.com/day-0-with-intel-atom-c3000-getting-nics-working/)[COLOR=#242729][FONT=Arial] but I'm still not getting a connection. During the install I used a wifi dongle to get an internet connection, but I'd like to use ethernet. I want a simple connection using my existing and working switch using dhcp.[/FONT][/COLOR][COLOR=#242729][FONT=Arial]I configured /etc/network/interfaces as follows:[/FONT][/COLOR]
auto lo

auto eno1
iface eno1 inet dhcp
[COLOR=#242729][FONT=Arial]Where eno1 is the interface I want to use (the mainboard provides multiple ethernet sockets).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Using ip a I get the following output:[/FONT][/COLOR]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether some:address::0000 brd ff:ff:ff:ff:ff:ff
    inet6 some:address::0000/64 scope link 
       valid_lft forever preferred_lft forever
3: eno2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether some:address::0000 brd ff:ff:ff:ff:ff:ff
4: eno3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether some:address::0000 brd ff:ff:ff:ff:ff:ff
5: eno4: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether some:address::0000 brd ff:ff:ff:ff:ff:ff
6: wlx647002097ecc: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether some:address::0000 brd ff:ff:ff:ff:ff:ff
    inet 192.168.178.87/24 brd 192.168.178.255 scope global dynamic wlx647002097ecc
       valid_lft 863362sec preferred_lft 863362sec
    inet6 some:address::0000/64 scope global mngtmpaddr noprefixroute dynamic 
       valid_lft 7014sec preferred_lft 3414sec
    inet6 some:address::0000/64 scope link 
       valid_lft forever preferred_lft forever [COLOR=#242729][FONT=Arial]So the wifi dongle is working, but without it I have no internet access. eno1 (which I want to use and which is connected to ethernet) seems to be up, but isn't providing internet access. At boot time the networking service seems to just time out: "A start job is running for Raise network interfaces". At shutdown there's a timeout at "A stop job is running for ifup for eno1".[/FONT][/COLOR]
```

I kindly ask for assistance. I'd say I'm a Linux and Ubuntu veteran, but so far I never had to manually configure networking. Ideally I'd like to get it to work at install time, but anythings fine.

---

### Post by chili555 on 2018-04-18
Since you have the wireless working, may I assume that the installation is done and all is well except for the ethernet?

May we please see:```
cat /etc/netplan/*.yaml
```

---

### Post by CrisisCore on 2018-04-22
I have no idea what changed, but I installed it again it just worked out of the box. Thanks though!

---

