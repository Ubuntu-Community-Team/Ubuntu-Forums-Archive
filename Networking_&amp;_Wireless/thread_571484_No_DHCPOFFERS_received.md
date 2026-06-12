---
title: "No DHCPOFFERS received"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by hindiogine on 2007-10-09
Using a 3C network card with a Motorola cable modem with SuddenLink.

I have no problem when I connect from my MacBook using DHCP.

I am not able to connect using Kubuntu 7.04.

dhclient times out giving:

No DHCPOFFERS received


The network card works because I can connect it to my LAN and ping.

route -a is empty

I disabled IPV6 in the aliases configuration file.

I uninstalled AVAHI.

/etc/hosts has 127.0.0.1 localhost

/etc/resolv.conf has the 2 DNS servers of SuddenLink.

ifconfig did give an IP address when AVAHI was installed but does not anymore.

It used to work fine with Dapper.

Thanks for your help.

Enrico

---

### Post by kevdog on 2007-10-09
Can you post 

lshw -C network
lspci -nn

---

