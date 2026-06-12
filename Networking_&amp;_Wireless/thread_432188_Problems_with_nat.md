---
title: "Problems with nat"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by angelot on 2007-05-03
I've got a fresh install of feisty.

I've got two network cards (eth0 and eth1) on my server

Eth0 is my internet connection - it's getting its IP from a broadband-router in the 10.0.0.0 subnet.
Eth1 I've set up as a local network with a static ip 192.168.1.2

I've got a wireless router (AP) connected to eth1 and it's giving out ipadresses in the range 192.168.1.100 - 192.168.1.200.

I've set it up properly, and with my laptop I get ip 192.168.1.100 from the wireless router with dhcp enabled.

btw the wireless router is on 192.168.1.1

I can ssh from server to client, and from client to server. I've even set up cups so that I can use the servers local printer as a network printer. When connected I can print from my laptop.

The only thing I can't do is to get online on the internett.

I've treid to do this:

# ifconfig eth1 192.168.1.2

# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# echo 1 > /proc/sys/net/ipv4/ip_forward

Installed dnsmasq and ipmasq:

# /etc/init.d/dnsmasq restart

Reconfigured ipmasq to start after networking has been started.

# dpkg-reconfigure ipmasq

Added the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf and rebooted.

I still can't get online.

Can anyone help me?

---

