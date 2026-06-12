---
title: "routing table periodically reset"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by avfangel on 2007-02-15
hey all!

I've successfully set up a pptp connection to my ISP over a calbe modem connect on a usb port. to accomplish the connection i had to insert the following lines into /etc/network/interfaces :

auto eth1
iface eth1 inet dhcp
up ip route replace 172.26.255.17 dev eth1
up ip route replace 10.205.192.1 dev eth1

these set up routing to my dhcp and pptp server. however, periodically the routes reset to:
~$ ip route
172.26.255.17 dev ppp0  proto kernel  scope link  src 89.0.88.60 
172.25.160.0/19 dev eth1  proto kernel  scope link  src 172.25.162.66 
default dev ppp0  scope link 

the correct configuration is:
~$ ip route
10.205.192.1 dev eth1  scope link 
172.26.255.17 dev eth1  scope link 
172.26.255.17 dev ppp0  proto kernel  scope link  src 89.0.88.60 
172.25.160.0/19 dev eth1  proto kernel  scope link  src 172.25.162.66 
default dev ppp0  scope link 

i have another network card and i suspect the problem is the dhcp reseting the routes when it reacquires leases.
any ideas on how i can make the route stick?

thanks, avishai

---

