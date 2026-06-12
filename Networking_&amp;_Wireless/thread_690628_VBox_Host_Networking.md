---
title: "VBox Host Networking"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by ovvyblabla on 2008-02-07
Hello,

I am running Gutsy as host, with XP Professional as Guest. I want to be able to access my dorm LAN (100+ comps) from my guest OS, so I need Host Networking. The only problem is, I can't get the guest to see any computer EXCEPT the host. Well, not quite: I can ping internet hosts (ping [www.google.com](www.google.com) works from guest) but I can't recieve anything from them. Strangely enough, while ping-ing internet hosts works, I can't ping any of the computers on the LAN.

Here is my /etc/network/interfaces .
NOTE: eth1 is my wireless card (the one I use to connect to the LAN), I use static IPs, and you can ignore the part about dsl-provider since I don't think it has anything to do with my problem.

```

# real network, works
auto lo

iface lo inet loopback

iface eth1 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ZIO


# dsl , also works, I use this from home
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth1


# VBox stuff
# the following lines do manage to connect my guest OS to my host OS, but the rest of the world
# is still out-of-reach as far as the guest is concerned

auto tap0
iface tap0 inet static
tunctl_user ovidiu
address 192.168.1.228
netmask 255.255.255.0
gateway 192.168.1.1
uml_proxy_arp 192.168.1.224
uml_proxy_ether eth1

auto br0
iface br0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports eth1 tap0
bridge_maxwait 0

```

I've been cracking at this for quite some time, trying various combinations and examples from the net, and this is as far as I've gotten. Please help me. Any pointers/advices are greatly appreciated.

EDIT: I found a hack : on my guest I have installed two interfaces : the Host Interface above and one using NAT to connect to the internet. And then I bridged them. And it works now. But if I remove the bridge, I loose access to my LAN. So, while this works, it's still a hack and I am still looking for a proper solution.

---

