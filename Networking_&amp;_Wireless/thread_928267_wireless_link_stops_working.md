---
title: "wireless link stops working"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Frantic225 on 2008-09-23
Hi,

I have a really strange thing happening: I'm running Hardy on a laptop with a Intel pro 3945ABG wireless card, however after a few KB traffic, my wireless stops working. I have a dual-boot with WinXP, and everything works great there.

More detailed: whenever I boot the PC, I can do a few KB of traffic after which everything stops working: telnet, ssh, web, etc, however ping, DNS and opening connections are still fine. I've tried reconnecting to the AP, restarting the wireless card, reloading it's driver (iwl3945 by the way) but the only way to get it to work again is to reboot the computer, and afterwards it's just going to be a few KB before it stops again.

I know it's only a few KB because I started Opera and it will always load 5-25 KB of a page after a fresh reboot, but nothing else afterwards. If for example I do a SSH and run Opera after, it won't load anything.

I've also made sure the firewall is not blocking anything.

Does anyone have any idea what's causing this?

Just to be clear, XP works fine with the same card and access point.

Thanks in advance.

---

### Post by willca on 2008-09-24
try adding this to the end of your /etc/sysctl.conf

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1


Then reload it by issuing

sudo sysctl -p

---

### Post by Frantic225 on 2008-09-24
I've added that and did sysctl -p, nothing changed :(. I'm writing from Win now, on the same PC, same AP, same wireless card. Anyway thanks for trying willca.

I've also attached a file with outputs from ifconfig and iwconfig. Does anyone have any other idea?

---

### Post by Frantic225 on 2008-09-24
bummer

---

### Post by Frantic225 on 2008-09-25
I've just reinstalled a fresh Hardy 8.04.1, exactly the same thing.

apparently this is not a known issue

GG, game over, gates wins :-z

---

