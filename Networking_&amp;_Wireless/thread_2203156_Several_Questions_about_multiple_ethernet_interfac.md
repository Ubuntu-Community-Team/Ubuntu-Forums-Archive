---
title: "Several Questions about multiple ethernet interfaces and static ip addresses"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Dudsmacka2 on 2014-02-01
I'm a recent migrant to the linux world.  I apologize if something like this was already posted - I was unable to find anything like this search :(

Running 13.10 x64 server.

When I set ip addresses to static dns resolution stopped working even though gateway was set (and pingable).  Had to set dns-nameserver in /etc/network/interfaces.  Why is this?

Here's my current /etc/network/interfaces

```

auto lo
iface lo inet loopback
[INDENT]
auto eth0
iface eth0 inet static
address 172.30.30.70
netmask 255.255.254.0
broadcast 172.30.31.255
gateway 172.30.30.7
dns-nameservers 208.67.222.222 8.8.4.4
[/INDENT]
[INDENT]
auto eth1
iface eth1 inet static
address 172.30.30.75
netmask 255.255.254.0
broadcast 172.30.31.255
gateway 172.30.30.7
dns-nameservers 208.67.222.222 8.8.4.4[/INDENT]

```

---

### Post by TheFu on 2014-02-02
Having 2 interfaces on the same subnet is an advanced technique. Manual configuration of the specific routes per device will be needed.

If you intend to get double the throughput, then the networking equipment needs to support "[bonded" interfaces]("https://help.ubuntu.com/community/UbuntuBonding") and be configured specifically for this to work on the switch AND computer. I don't know of any sub-$150 switches that do it, though dd-wrt, tomato and openwrt on appropriate hardware do, I believe.

```
ifconfig
route

```will provide the output needed to advise more. Only you will know if the network devices do what you want. Check the product specs.

If none of this describes what you are trying to do, then it is likely that putting each network card on a different subnet is the easiest answer. Doing so will change the routes automatically.

---

