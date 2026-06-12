---
title: "Wireless network between two pcs"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Calixte on 2009-04-17
Hi,

My brother and I each have an Eee PC and freshly installed Eeebuntu on them.

It doesnt seem very different from the standard ubuntu i use on my desktop computer.

My internet connection is cabled, and I'd like to create a wireless network between our netbooks so both computers can connect to internet simultaneously.

How?

Thanks


Calixte

---

### Post by cariboo on 2009-04-17
The easiest way to do what you need is to buy a wireless router. If for some reason you don't want to get a router, you will need to install a wireless card in your desk top, then setup network connection sharing. Have a look at this [howto.]("http:///help.ubuntu.com/community/Internet/ConnectionSharing")

Jim

---

### Post by iponeverything on 2009-04-17
one way to do it -- On the wired pc where wlan0 is your wireless interface -- Note that when an interface is added /etc/interfaces it will not be managed by Network Manager.

in /etc/network/interface add:

```
iface wlan0 inet static
     address 192.168.5.1
     netmask 255.255.255.0
     wireless-essid Share
     wireless-mode Ad-Hoc

auto wlan0


```
on machine one in the /etc/rc.local append the lines
```

iptables -t nat -A POSTROUTING -s  192.168.5.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```


On machine two where wlan0 is your wireless interface

in /etc/network/interface add:
```

iface wlan0 inet static
     address 192.168.5.2
     netmask 255.255.255.0
     gateway 192.168.5.1
     wireless-essid Share
     wireless-mode Ad-Hoc

auto wlan0

```

---

### Post by Calixte on 2009-04-17
sorry i tried but i dont really understand the instructions...
:(

can you give more precisions?..

thanks again,

---

