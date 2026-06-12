---
title: "Need both DHCP and Static IP with VirtualBox networking."
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by JoHandsum on 2008-05-12
Hi,

I recently setup my Ubuntu 8.04 host with VirtualBox 1.6 running an Windows XP guest.  I followed the various Host Interface setups and got that working with my host's DHCP networking.  Here is my /etc/network/interfaces configuration:

auto lo
iface lo inet loopback

iface eth0 inet manual

auto br0
iface br0 inet dhcp
	bridge_ports eth0

#auto br0:0
#iface br0:0 inet static
#	address 192.168.2.5
#	netmask 255.255.255.0

The part that I have commented out is where I tried to add the private network that I have setup to communicate with the other computers on my desk so that their network traffic doesn't have to go out on the the company network (they connect through a little D-Link 5 port switch).  When I had the br0:0 stuff uncommented it worked, but when it would end with an error at the end of /etc/init.d/networking start.  The error was "SIOCSIFFLAGS: Cannot assign requested address" which made me think that even though it was allowing me to communicate with the other computers it somehow wasn't set up correctly.  My other computers don't have a br0 setup and they just use and eth0:0 virtual interface to become part of my private network.  I had initially tried creating an eth0:0 interface exactly like the br0:0 interface but that didn't work at all.  Can someone set me straight on how to add a static IP in addition to a DHCP supplied address to a single ethernet card using a virtual bridge?  Below is my ifconfig (which br0:0 commented out).  Thanks!


_ifconfig output_

br0       Link encap:Ethernet  HWaddr 00:18:fe:6a:73:9c  
          inet addr:141.204.60.185  Bcast:141.204.61.255  Mask:255.255.254.0
          inet6 addr: fe80::218:feff:fe6a:739c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22668986 (21.6 MB)  TX bytes:2233423 (2.1 MB)

eth0      Link encap:Ethernet  HWaddr 00:18:fe:6a:73:9c  
          inet6 addr: fe80::218:feff:fe6a:739c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24990901 (23.8 MB)  TX bytes:3442911 (3.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:831960 (812.4 KB)  TX bytes:831960 (812.4 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:0e:aa:9b:73  
          inet6 addr: fe80::2ff:eff:feaa:9b73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36401 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1109180 (1.0 MB)  TX bytes:5002345 (4.7 MB)

---

