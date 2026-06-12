---
title: "NetworkManager+VPN+MTU"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Deksan on 2007-04-19
Hi,

I d like to use NetworkManager for its vpn handy capacities. But I need to set the mtu of the interfaces to 1492. And here is the problem. If I put :

/etc/network/interfaces :

auto eth0
iface eth0 inet dhcp

I am able to connect with the vpn and the NetworkManager Menu proposes it, On left click I have the menu : 
[x] Wired Network
VPN Connections >
Manual Configuration...

If i change /etc/network/interfaces into :

auto eth0
iface eth0 inet dhcp
pre-up /sbin/ifconfig $IFACE mtu 1492

I am unable to connect with NetworkManager as the menu becomes :
Manual Configuration...

Could someone help ? Thanks for your time.

---

### Post by Deksan on 2007-04-20
Sounds like a bug ? Should I create a bug entry in NetworkManager or ubuntu bug tracker ?

---

