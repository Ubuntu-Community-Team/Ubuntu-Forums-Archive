---
title: "interface name changing at every boot (atheros + thinkpad t30)"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by paet on 2008-01-16
I have a d-link dwl-g650 pcmcia wifi adapter, and everytime I turn on my laptop, its interface name (ath*) increases by one.
Is there any way to stop that from happening, because I don't like yanking out the card every time I turn off my laptop, and plugging it back in efter every boot?

---

### Post by pebo on 2008-01-16
You can give a persistent name to your interface by creating a udev rule:
Taken from the Archlinux wiki udev article:
> Another method for network card ordering is to use the udev-sanctified method of statically-naming each interface. Create a file called /etc/udev/rules.d/10-network.rules and bind the MAC address of each of your cards to a certain interface name:

SUBSYSTEM=="net", ATTRS{address}=="aa:bb:cc:dd:ee:ff", NAME="lan0"
SUBSYSTEM=="net", ATTRS{address}=="ff:ee:dd:cc:bb:aa", NAME="wlan0"

A couple things to note:

* To get the MAC address of each card, use this command: udevinfo -a -p /sys/class/net/<yourdevice>
* Make sure to use the lower-case hex values in your udev rules. It doesn't like upper-case.
* Some people have problems naming their interfaces after the old style: eth0, eth1, etc. Try something like "lan" or "wlan" if you experience this problem.
HTH
____

---

