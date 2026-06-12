---
title: "wired network connection"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by huncheeg on 2008-01-21
Hello everybody (first message!)
I'm using Gutsy, dual booting with Suse 10.0 ( net-working perfectly..).Ethernet Adsl. wired. DHCP (roaming mode, no difference).
The problem:
I need to add manually the gateway, everytime I reboot or if I type "dhclient"

Here are the output of the following:

Route -n after booting (no network connection)
 
oloap@oloap-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
x.y.z.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
 
Ip route after booting: (no network connection)

oloap@oloap-desktop:~$ ip route
x.y.z.0/24 dev eth0  proto kernel  scope link  src x.y.z.208 

Adding manually the gw:

oloap@oloap-desktop:~$ sudo route add -net default gw x.y.z.1

Route -n after: (I can access the network):

oloap@oloap-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
x.y.z.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         x.y.z.1     0.0.0.0         UG    0      0        0 eth0
 
I think it's a problem related with dhcp and network manager...or a routing issue.. I can of course bypass the problem, but I would like to fix it.
I don't know how.. can someboby help me?

---

