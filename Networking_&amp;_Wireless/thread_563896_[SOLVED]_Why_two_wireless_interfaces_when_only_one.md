---
title: "[SOLVED] Why two wireless interfaces when only one present?"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2007-09-30
I really only have one wireless interface, built into my Acer Travelmate 630. An wired ethernet device is also built-in. 

I have edited /etc/network/interfaces and down to lo and ath0.

Why then does the system change /etc/network/interfaces to the following (below).

My connectivity is good with this configuration, but I do not know why I have an ath0 and an eth1.

-------------- begin /etc/network/interfaces ...........................................

iface lo inet loopback

auto lo

iface ath0 inet dhcp
wireless-essid mtlaughmore
wireless-key 8871680A9E577859BB6CE285D8

auto ath0


iface eth1 inet dhcp
wireless-essid mtlaughmore
wireless-key 8871680A9E577859BB6CE285D8

auto eth1

iface eth0 inet dhcp

-------------- end /etc/network/interfaces ...........................................

---

### Post by noob12 on 2007-09-30
You probably don't have an atheros card.  You probably have something else whose driver prefers to have the interface called **eth*N***.

Output of the commands
```

lspci -nn

sudo lshw -C network

ifconfig -a

```
will tell you how things are.

The **/etc/network/interfaces** file does not determine the names of interfaces.  It configures interfaces that already have the specified names.  The interface naming is determined by the kernel, driver and udev.

---

