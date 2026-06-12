---
title: "Changed NICs - new one not recognised"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by Grantley on 2006-10-14
Hi

Changed the hardware for my UBUNTU server (no gui). The new server works great except for the Network card. ifconfig shows the NIC as eth1. Interfaces only has commands for eth0. How do I get my NIC to change from being eth1 to eth0?

Thanks
Grantley

ifconfig -a

eth1      Link encap:Ethernet  HWaddr 00:16:76:27:69:13  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Contents of /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.81.1.5
	netmask 255.255.255.0
	network 10.81.1.0
	broadcast 10.81.1.255
	gateway 10.81.1.3
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 10.81.1.1 10.81.1.3

---

