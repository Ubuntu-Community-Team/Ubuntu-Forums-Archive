---
title: "Multiple Network cars and internet sharing"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Mickeysofine1972 on 2007-01-13
Hi 

I need to setup a main gateway computer with three Ethernet NICs this box will also connect to the internet through a BB box that connects with a Ethernet cable and assigns the one of the card an IP of 192.168.1.4, the BB box has an IP 192.168.1.1 and allocates by dhcp for the box.

i want to be able to share the internet bandwidth to two othe machines via the other two cards . How do i set this up? and what ip can i set on each card to make this work?


Mike

---

### Post by hectare on 2007-01-13
Set **/proc/sys/net/ipv4/ip_forward set it to 1**

Simple way:
Machine 1:
eth0->192.168.1.4 (by dhcp,default gateway 192.168.1.1)
eth1->192.168.1.10,subnet 255.255.255.0
eth3->192.168.1.20,subnet 255.255.255.0
On Other Machines(which need internet access):
192.168.1.30 ,subnet 255.255.255.0 ,default gateway 192.168.1.1,dns ->isp dns

Another way
eth0->192.168.1.4 (by dhcp,default gateway 192.168.1.1)
eth1->172.16.0.10, subnet 255.255.0.0
eth3->172.16.0.20,subnet 255.255.0.0
** iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 192.168.1.4 **
On Other Machines:
172.16.0.30 ,subnet 255.255.0.0 ,default gateway 172.16.0.10 Or 172.16.0.20 dns ->isp dns
172.16.0.31 ,subnet 255.255.0.0 ,default gateway 172.16.0.10 Or 172.16.0.20 dns ->isp dns

There are other ways also ..

don't forget  **/proc/sys/net/ipv4/ip_forward set it to 1**


why dont you plug everything into a hub and let the BB box assign dhcp and gateway to all machines.

---

### Post by Mickeysofine1972 on 2007-01-13
> **hectare said:**
> Set **/proc/sys/net/ipv4/ip_forward set it to 1**

Simple way:
Machine 1:
eth0->192.168.1.4 (by dhcp,default gateway 192.168.1.1)
eth1->192.168.1.10,subnet 255.255.255.0
eth3->192.168.1.20,subnet 255.255.255.0
On Other Machines(which need internet access):
192.168.1.30 ,subnet 255.255.255.0 ,default gateway 192.168.1.1,dns ->isp dns

Another way
eth0->192.168.1.4 (by dhcp,default gateway 192.168.1.1)
eth1->172.16.0.10, subnet 255.255.0.0
eth3->172.16.0.20,subnet 255.255.0.0
** iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 192.168.1.4 **
On Other Machines:
172.16.0.30 ,subnet 255.255.0.0 ,default gateway 172.16.0.10 Or 172.16.0.20 dns ->isp dns
172.16.0.31 ,subnet 255.255.0.0 ,default gateway 172.16.0.10 Or 172.16.0.20 dns ->isp dns

There are other ways also ..

don't forget  **/proc/sys/net/ipv4/ip_forward set it to 1**


why dont you plug everything into a hub and let the BB box assign dhcp and gateway to all machines.

do eth1 and eth2 have the same gateway as eth0 ?

Mike

---

### Post by hectare on 2007-01-13
> do eth1 and eth2 have the same gateway as eth0 ?

you don't need to setup gateway for eth1 and eth2 .
since there is already a default route(gateway)(on eth0) all packets will be routed to default route.

---

### Post by Mickeysofine1972 on 2007-01-13
ok so i did that but now when i ping the addresses from another machine it says the connection is there but the ping says 'destination unreachable' which is weird because i placed a network monitor on the task bar and it blinks every time the ping triggers. the only thing is the NIC does'nt answer the ping

Mike

---

### Post by Mickeysofine1972 on 2007-01-14
whats really weird is that i have the ipmasq and dnsmasq programs installed to handle the connection sharing. but when i try to even ping through the ethernet cards its like some thing is stopping them from answering each other.

The other weird thing is that during the shut down of the internet connected pc's shutdown, the other pings suddenly start working, but during bootup they dont!

Strange things are afoot!

Mike

---

