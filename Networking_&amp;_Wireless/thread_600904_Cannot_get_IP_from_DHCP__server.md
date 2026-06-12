---
title: "Cannot get IP from DHCP  server"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by maximx86 on 2007-11-02
Hi

I cannot obtain IP from my router BT Home Hub, It perfectly works on Static IP. Under Windows I am able to get the IP from DHCP. It's not the router's fault. I tried reinstalling DHCP client. Didn't help. I am using Ubuntu 7.10. Tried also:

sudo /etc/init.d/networking restart - again nothing

What shall I check next. I am new to Linux environment.

Tahnks

---

### Post by k_grdn on 2007-11-02
Hi maximx86,

Firstly check - /etc/network/interfacesuld

For dhcp should look like this:

auto eth2
iface eth2 inet dhcp

Replace eth2 with your interface, if this still fails assign a static address in the same subnet and try pinging your router.

Static entry

iface eth0 inet static
address 192.168.0.55
netmask 255.255.255.0
gateway 192.168.0.10

Again replace ip entries with your own, when troubleshooting networks start with the first of the seven OSI layers.

physcial - cables, connectors, cards etc..

Regards,

k_grdn

---

