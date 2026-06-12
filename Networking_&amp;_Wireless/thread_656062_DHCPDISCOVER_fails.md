---
title: "DHCPDISCOVER fails"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by gnjurac on 2008-01-02
Hi,
I am new to linux but tried several distros and now have on one old PC xubuntu and on the other ubuntu server. on this server i am trying to configure eth1 in console to connect to internet. until now i have done  the following:

in   /etc/network/interfaces    added   auto eth0 iface eth0 inet dhcp, after that restarted interface and PC but when trying to ping other pc in the network it says Network is unreachable.

in /etc/resolv.conf added nameserver 192.168.10.1, restarted interface and pc.

when dhclient eth1 it says No DHCPOFFERS received.

the eth card works well on other pc, cable is OK, the link is up.

please help!
tnx

---

### Post by gnjurac on 2008-01-04
it seems that tha LAN card was faulty. replaced with a new one and it works.

---

