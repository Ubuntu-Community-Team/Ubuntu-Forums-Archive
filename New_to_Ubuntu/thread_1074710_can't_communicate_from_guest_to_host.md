---
title: "can't communicate from guest to host"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-19
Hey all,

I'm running Ubuntu 8.10  and running a windows xp virtual machine on top of that. I gave the virtual machine internet by passing it a virtual interface, and that seems to work fine. I can access the web, and ping everything on my network, except the host machine. The host can ping the guest, an in fact, so can everything else on the network. I'm having trouble understanding what the problem is. I think maybe something I messed up in setting up my interfaces? Idk. I'm posting ifconfig and /etc/network/interfaces

```
/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto tap0
	iface tap0 inet manual
	tunctl_user rgb
	uml_proxy_arp 10.x.xx.xxx
	uml_proxy_ether eth0

auto br0
	iface br0 inet static
	address 10.x.xx.xxx
	netmask 255.255.255.0
	gateway 10.x.xx.254
	bridge_ports eth0 tap0
	bridge_maxwait 0

ifconfig:
br0       Link encap:Ethernet  HWaddr 00:0c:6e:bb:a0:68  
          inet addr:10.x.xx.xxx  Bcast:10.x.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:febb:a068/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8146636 (8.1 MB)  TX bytes:924931 (924.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:bb:a0:68  
          inet6 addr: fe80::20c:6eff:febb:a068/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71750684 (71.7 MB)  TX bytes:13841565 (13.8 MB)
          Interrupt:22 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14178 (14.1 KB)  TX bytes:14178 (14.1 KB)

tap0      Link encap:Ethernet  HWaddr 76:64:f0:28:cf:db  
          inet6 addr: fe80::7464:f0ff:fe28:cfdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100048 errors:0 dropped:370 overruns:2 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4352917 (4.3 MB)  TX bytes:14531954 (14.5 MB)


```

Any ideas why I can't communicate back to the host? Thanks in advance for any help provided.

---

### Post by Peter09 on 2009-02-19
The latest versions of VirtualBox do not need bridging enabled to have a virtual interface, its a lot simpler. For your setup, have you set your interface to promiscuous?

---

