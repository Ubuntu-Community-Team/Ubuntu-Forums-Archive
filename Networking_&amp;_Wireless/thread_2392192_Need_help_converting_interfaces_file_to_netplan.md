---
title: "Need help converting interfaces file to netplan"
date: 2018-05-17
forum: Networking &amp; Wireless
---

### Post by kevin.traub on 2018-05-17
Doing a tech refresh on a system and moving from a static /etc/net/interfaces file to netplan and I need some help converting my interfaces file to netplan.
My current interfaces file is as follows:

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        pre-up /sbin/ethtool -s eth0 speed 1000 duplex full autoneg off
        address 192.168.44.39
        netmask 255.255.255.224
        network 192.168.44.32
        broadcast 192.168.44.63
        gateway 192.168.44.62
        # dns - options are implemented by the reslovconf package, if installed
        dns-nameservers 192.243.224.248 192.243.224.249
        dns-search xax.net

auto eth1
iface eth1 inet static
        address 192.168.29.130
        netmask 255.255.255.252


****Any help is greatly appreciated.

[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

---

