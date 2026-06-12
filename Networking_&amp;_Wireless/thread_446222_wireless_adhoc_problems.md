---
title: "wireless adhoc problems"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by brtzsnr on 2007-05-16
I have Intel Corporation PRO/Wireless 3945ABG network adapter. I'm trying to setup an adhoc wireless connection using these setings (from /etc/network/interfaces):

auto eth1
iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.252
        broadcast 192.168.0.3
        wireless-mode ad-hoc
        wireless-channel 10
        wireless-ap off
        wireless-essid alexandru-laptop

my problem is that after a minute or two it exists the adhoc mode and I think it starts searching for a network. I tried also different configuration combinations (with key, with ap any or auto or even missing, etc) but I've got the same result.

I'm running Ubuntu 7.04 on a Dell Inspiron E1505.

---

