---
title: "[SOLVED] Internet share between Ubuntu and Arch Linux"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by carandraug on 2008-08-10
Hi,

As the title says, I'm trying to share an internet connection between my Ubuntu and Arch Linux boxes. Ubuntu gets internet through wireless and I want it to share with Arch through Ethernet. I've done it previously with success (with other computers) but for some reason I can't get it done this time.

Ubuntu gets wireless internet through wlan0 (it's an USB adapter) and connects through eth0 with an Ethernet cable to another eth0 in Arch

Here's a diagram of what I mean

router ))) wireless (((wlan0-Ubuntu-eth0<---Ethernet--->eth0-Arch

What I've done:
[LIST=1]
[*]I enabled (I think) packet forward in Ubuntu by uncommenting at /etc/sysctl.conf the line```
net.ipv4.conf.default.forwarding=1
```

[*]I tried to reload the settings with sudo sysctl -p but I've rebooted it since then so that's probably not an issue.

[*]Both computers have the same DNS. In the arch box I went to /etc/resolv.conf and entered the same values I have in Ubuntu.

[*]I made a connection between both computers by entering, in Ubuntu ,```
sudo ifconfig eth0 192.168.0.1 netmask 255.255.255.0 up
```

[*]In Arch I setted Ubuntu IP (192.168.0.1) as gateway and gave him 192.168.0.2 as his IP.

[*]In Ubuntu I entered ```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```which, if I understand correctly what says in the man pages, will forward the packets from Arch to wlan0.
[/LIST]

The result:
[LIST]
[*]Both computers can ping each other.
[*]Can't ping anything else in Arch Linux.
[*]I don't think the problem is in the Arch since it's connected to Ubuntu, probably something that I missed in Ubuntu.
[/LIST]

Can someone see where I'm going wrong? Thanks in advance

---

### Post by carandraug on 2008-08-10
I mananged to solve my problem with the help from nDuff at #ubuntu

after a look at "iptables -L -v -t nat" and "iptables -L -v", he noticed the counts as zero which pointed to a problem with the gateway in the Arch Box. And so it was. In the Arch Linux I did use the correct IP as gateway but I forgot to remove the "! from the line```
ROUTES=(!gateway)
```The "!" HAS to go if you want it to work. Can't believe I missed it.

---

