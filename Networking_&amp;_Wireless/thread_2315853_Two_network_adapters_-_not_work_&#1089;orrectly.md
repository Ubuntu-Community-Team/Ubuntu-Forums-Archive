---
title: "Two network adapters - not work &#1089;orrectly"
date: 2016-03-03
forum: Networking &amp; Wireless
---

### Post by dmitry46 on 2016-03-03
Hello all!!
I'm use Ubuntu  server 14.04 jo PC with two network adapters (ASUS M2N32 SLI Deluxe).
All ethernet adapters connect to switch, in different network (VLAN) with different DHCP servers. These networks are routed together.
/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


# The secondary network interface
auto eth1
iface eth1 inet dhcp

```
:~$ ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1d:60:86:b6:3d  
          inet addr:192.168.36.2  Bcast:192.168.36.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe86:b63d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60717 errors:11152 dropped:0 overruns:11090 frame:62
          TX packets:24943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17516865 (17.5 MB)  TX bytes:43763863 (43.7 MB)


eth1      Link encap:Ethernet  HWaddr 00:1d:60:86:bc:8d  
          inet addr:192.168.88.2  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe86:bc8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86472 errors:2242 dropped:0 overruns:1987 frame:255
          TX packets:63749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89893044 (89.8 MB)  TX bytes:5911986 (5.9 MB)


lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:142694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:285831556 (285.8 MB)  TX bytes:285831556 (285.8 MB)


virbr0    Link encap:Ethernet  HWaddr 16:38:2a:e8:df:ce  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
:~$ route
```

Destination Gateway Genmask Flags Metric Ref Use Iface
default         192.168.88.1    0.0.0.0         UG    0      0        0 eth1
192.168.36.0    *               255.255.255.0   U     0      0        0 eth0
192.168.88.0    *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0

```
some times default gateway may be 192.168.36.1
Main problem - eht0 work, but often ceases to be available (communication is interrupted for a few minutes, then restores again for a few minutes)
eth1 not work - not available for ping all time.
On DHCP log I see, that both get IP address at same time.
Try to add to /etc/network/interfaces after each adapter:
```
up route add -net 192.168.XX.0 netmask 255.255.255.0 gw 192.168.XX.1
```
but this does not fix the error.
Prompt please the what can be done to ensure the work of the two network interfaces?

---

### Post by SeijiSensei on 2016-03-03
You can have only one default gateway.  Pick the one that points upstream and add a route to that.

---

### Post by dmitry46 on 2016-03-04
Ok, tommorow I'm change /etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.88.2
netmask 255.255.255.0
broadcast 192.168.88.255

```
to remove the gateway from eth1 settings.
route table:
```

Destination Gateway Genmask Flags Metric Ref Use Iface
default         192.168.36.1    0.0.0.0         UG    0      0        0 eth0
192.168.36.0    *               255.255.255.0   U     0      0        0 eth0
192.168.88.0    *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0

```
But this morning I again received several times the problem with drop in the network. Maybe something else?

---

### Post by SeijiSensei on 2016-03-04
Why are you using a bridge?  Can you not create a route to 192.168.122.0/24?  Where is that network located?

---

### Post by dmitry46 on 2016-03-04
> **SeijiSensei said:**
> Why are you using a bridge?  Can you not create a route to 192.168.122.0/24?  Where is that network located?
Bridge cerate by KVM on install. I'm not use it. Network adapters of my VM work in bridge mode with eth1.
Why do I need a route 192.168.122.0/24? Do you think the problem is it?

---

### Post by SeijiSensei on 2016-03-04
> **dmitry46 said:**
> Bridge cerate by KVM on install. I'm not use it. Network adapters of my VM work in bridge mode with eth1.
I'm going to ask a lot of questions.  You need not answer them all here.  I'm giving you things to consider.

How many adapters are on the VM host?  Is the physical eth0 on the VM host in the 192.168.36.0/24 network as well?  Is there a physical eth1?  Is it on the 192.168.88.0/24 network?  Is the routing on the physical host the same as on the VM?  Suppose you bring down eth1 on the virtual host with
```
sudo ifconfig eth0 down
```
Can you ping machines in the 192.168.88.0/24 network?  What else can you see then?  Machines in 88.0?  Machines on the Internet?  Nothing at all?

Why are you using two virtual interfaces?  What application(s) are you trying to support?  Do you need to route packets through the VM?  If so, is tcp forwarding enabled in /etc/sysctl.conf?

---

### Post by dmitry46 on 2016-03-04
Hello.

Yesterday I'm remove VM network adapter and set static eth1. /etc/network/interfaces :
```

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.36.2
netmask 255.255.255.0
gateway 192.168.36.1
broadcast 192.168.36.255


# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.88.2
netmask 255.255.255.0
broadcast 192.168.88.255

```
Now work quite stable after some test reboot within a day. I will watch and wait.
In an extreme case I'm reinstall system without automaticaly (in installation mode) KVM install and set static IP on eth1 initially.
It is of course "dancing with tambourines", but it's the Linux.

Main and one problem now - not available eth1 from my network (ping to 192.168.88.2 not work).
But all virtual machines on 192.168.88.0/24 is available (connect to it pass).
I'm try to disable eth0, but It does not change anything.

Thank for your help.
I'm will wait 16.04 LTS (end of aplril'16). May be it will work more stable.

---

### Post by SeijiSensei on 2016-03-05
All of these technologies are decades old; they won't change when 16.04 is released.  You just need to figure out the correct routing for your network configuration.

---

### Post by dmitry46 on 2016-03-18
Hello.
I'm install Ubuntu Server 15.10 on my computer 1 week ago and have no problem with disconnect on first network adapter on all of this time.
I'm think thant the broblem was in hardware. As I\m write, I'm use for my home server [https://www.asus.com/Motherboards/M2N32SLI_DeluxeWireless_Edition/](https://www.asus.com/Motherboards/M2N32SLI_DeluxeWireless_Edition/) (ASUS M2N32 SLI Deluxe). But It very old motherboard, and I'm not uderstend, whie this problem was be solved only on 15.10 version. May be on 14.04 need addition manual configuration of network adapters?
It made me very upset, because I have great pleasure in working on version 14.10.

---

