---
title: "dhcp dhclient reject offered gateway route"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by heze on 2007-05-04
Hi all,

I'm trying to install Feisty on my desktop PC with two network interfaces. The eth0 is connected to my private LAN and configured by DHCP. DHCP offers a route.

The eth1 is connected to my bridging DSL modem and is statically set to a public IP address dedicated to this computer. Gateway address is configured in Network Manager properties.

Here's what I get with using Network Manager settings:

<snip>
$ ip ad sh
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:11:22:33:44:55 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.2/24 brd 192.168.0.255 scope global eth0
    <inet6 scope link line removed>
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:22:33:44:55:66 brd ff:ff:ff:ff:ff:ff
    inet 123.123.123.2/24 brd 123.123.123.255 scope global eth1
    <inet6 scope link line removed>
       valid_lft forever preferred_lft forever

$ ip route sh
123.123.123.0/24 dev eth1  proto kernel  scope link  src 123.123.123.2 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.2 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 192.168.0.1 dev eth0 
default via 123.123.123.1 dev eth1 
</snip>

Browsing internet works but via eth0 (because it's before the second default route in the routing table?).

Here's what I get with "routers" removed from 'request' option in dhclient.conf and exact same interface settings as before:

<snip>
$ ip ad sh
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:11:22:33:44:55 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.2/24 brd 192.168.0.255 scope global eth0
    <inet6 scope link line removed>
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:22:33:44:55:66 brd ff:ff:ff:ff:ff:ff
    inet 123.123.123.2/24 brd 123.123.123.255 scope global eth1
    <inet6 scope link line removed>
       valid_lft forever preferred_lft forever

$ ip route sh
123.123.123.0/24 dev eth1  proto kernel  scope link  src 123.123.123.2 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.2 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 192.168.0.1 dev eth0 
</snip>

Obviously browsing and all works, but thru NAT @ 192.168.0.1 which I don't want.

What should I do to have default route via 123.123.123.1 and both eth0 and eth1 configured?

Thanks for any help,

Heikki

---

