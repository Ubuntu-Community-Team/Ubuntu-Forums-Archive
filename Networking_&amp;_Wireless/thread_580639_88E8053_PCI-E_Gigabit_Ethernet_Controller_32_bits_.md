---
title: "88E8053 PCI-E Gigabit Ethernet Controller 32 bits problem"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by Pipotchi on 2007-10-18
Hi all,

I bought a computer last february (ASUS motherboard with integrated Ethernet port named 88E8053 PCI-E Gigabit Ethernet Controller). I always used Linux 64 bits with it (I never paid the Windows tax :D), first OpenSuse and then Ubuntu 7.04. I never had any problem with my Internet with those 64 bits distribution. 

However, I discovered that Linux 64 bits is not quite ready for mainstream user like me (and opensource game like me... there is no ****** package for 64 bits game... but that's for another post). So I decided to switch to Linux 32 bits. I installed PCLinuxOS 2007 and Ubuntu 7.10 (clean install each and every time) and since then, I am not able to connect to the web. I even switched back to Linux 64 bits just to make sure that my card has not broken, and I was able to access instantly the net. 

So here is the problem. I have a wireless router that is connected to my DSL modem. My computer is wire-connected to the router. With 32 bits Linux, I can configure my router (at address 192.168.0.1) and I can even connect to my DSL modem and configure it (at address 192.168.1.1). However, I cannot connect to any website. Even the update manager in Ubuntu is not able to connect to any server. I wonder if there is any way I can configure my ethernet card, if there is any special driver for my ethernet card or if I must go back to Linux 64 bits and unfortunatly consider buying a Windows license since package support is crappy for games in 64 bits Linux (and I sincerely not missing Windows...). Thank you for help.

Raf

---

### Post by anubhavrocks on 2007-10-18
since you can reach your Router and modem,your Network card is working.Check your nameserver, most probably you haven't set it right.

---

### Post by RC211V on 2007-10-20
I have the same card and my internet works with the 7.10 beta live cd but it doesn't with the final 7.10 released 1-2 days ago. What's happening?

---

### Post by anubhavrocks on 2007-10-21
Post the output of 
```
ifconfig -a
cat /etc/network/interfaces 
cat /etc/resolv.conf
route -n
```

---

### Post by RC211V on 2007-10-22
> **anubhavrocks said:**
> Post the output of 
```
ifconfig -a
cat /etc/network/interfaces 
cat /etc/resolv.conf
route -n
```

```
sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:20:C1:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          inet6 addr: fe80::212:f0ff:fe83:7020/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000 Memory:b000b000-b000bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6288 (6.1 KB)  TX bytes:6288 (6.1 KB)
--------------------------------------------------------------------------
cat /etc/network/interfaces
auto lo
iface lo inet loopback
--------------------------------------------------------------------------
sudo cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory
--------------------------------------------------------------------------
sudo route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
--------------------------------------------------------------------------
```

Hope you can help mate.

---

### Post by anubhavrocks on 2007-10-23
Edit the interfaces  file to look like like this
sudo gedit /etc/network/interfaces

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0


```

---

### Post by RC211V on 2007-10-23
```
feanor@valinor:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:20:C1:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2000 Memory:b000b000-b000bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30040 (29.3 KB)  TX bytes:30040 (29.3 KB)




feanor@valinor:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0


feanor@valinor:~$ cat /etc/resolv.conf
search halls.manchester.ac.uk
nameserver 130.88.203.7
nameserver 130.88.13.7
nameserver 130.88.200.6
nameserver 130.88.94.110
feanor@valinor:~$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

I still don't have connectivity even though i get an ip. I disabled ipv6 in firefox and deleted the ip6 things in the connections manager under hosts. What next? I think we are getting closer. BTW the first time i changed the interfaces as you instructed eth0:avah appeared with the correct ip addresses but still no internet.

---

### Post by anubhavrocks on 2007-10-23
Please provide the outputs  of
```
sudo dhclient eth0 
ping -c3 ubuntu.com
route -n
```

I am assuming that DHCP is enabled.

---

### Post by RC211V on 2007-10-23
```
feanor@valinor:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:a0:d1:20:c1:4e
Sending on   LPF/eth0/00:a0:d1:20:c1:4e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
feanor@valinor:~$ ping -c3 ubuntu.com
ping: unknown host ubuntu.com
feanor@valinor:~$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
feanor@valinor:~$ 



```

---

### Post by froy02 on 2007-10-23
It seems like your router is not assigning IP address to your network cards. because 192.168.0.1 is your internet address.  When your router assigns IP addresses to wired lan they would be something 192.168.0.1xx. The numbers always higher than 1. Try to configure your card to 192.168.0.101.

Or better yet set your router for automatic DHCP server so that whenever you plug in anything it would just automatically give it its own ip address.  Very much less work.  

Froy

---

### Post by RC211V on 2007-10-23
I don' have a router. I am connected directly to a LAN. My internet worked with 7.10 Beta and works with Fedora and Sabayon. Why must Ubuntu give me a hard time?

---

