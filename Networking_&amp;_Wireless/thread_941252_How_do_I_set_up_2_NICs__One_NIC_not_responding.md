---
title: "How do I set up 2 NICs?  One NIC not responding"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by ootoaoo on 2008-10-07
So I have two routers plugged into my ubuntu server (2 NICs)

eth0:  192.168.0.10  <--- my internal network
eth1:  192.168.1.10  <--- to external network

The internal network is functioning correctly (can still connect, IP is actually being set, etc...).  I am unable to connect to the server through eth1 (and I need to be able to through HTTP, SSH, etc...)

Here is my /etc/network/interfaces :
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        gateway 192.168.0.1

auto eth1
iface eth1 inet static
        address 192.168.1.10
        netmask 255.255.255.252

Any ideas?  I read on other forums I shouldn't specify a gateway for eth1 since it will confuse the OS.  And here is my route -n:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.8     0.0.0.0         255.255.255.252 U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


Here is my ifconfig -a:
> eth0      Link encap:Ethernet  HWaddr 00:E0:18:9E:52:00  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe9e:5200/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:734347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:718706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:357467314 (340.9 MiB)  TX bytes:776330370 (740.3 MiB)

eth1      Link encap:Ethernet  HWaddr 00:A0:CC:3A:6A:66  
          inet addr:192.168.1.10  Bcast:192.168.1.11  Mask:255.255.255.252
          inet6 addr: fe80::2a0:ccff:fe3a:6a66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:2 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11090 (10.8 KiB)  TX bytes:7137 (6.9 KiB)
          Interrupt:169 Base address:0x9400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:166592 (162.6 KiB)  TX bytes:166592 (162.6 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Thanks in advance for any help you can provide!!

---

### Post by ootoaoo on 2008-10-08
anyone have any ideas?

---

### Post by seeker1458 on 2008-10-08
You said that your .0.10 is for your internal address...but that is the subnet that your gateway is on?  Your gateway needs to be specified on the nic you want to access the internet.  So if you want your .1.10 to access the internet specify the gateway in that config.  Why did you use a subnet of 255.255.255.252?

---

### Post by ootoaoo on 2008-10-08
I made up .252 - I just thought it had to be different.

I actually want both to be able to handle requests from the internet - I say that .0.1 is internal... but both routers are actually plugged into the internet.  So in theory it should handle requests from both.

What should I change?

---

### Post by seeker1458 on 2008-10-08
Does it matter to you which interface you connect to the internet from?  I don't think you can tell your machine to connect from both devices because it will not make a descision for you.

---

### Post by seeker1458 on 2008-10-08
try changing 255.255.255.252 to 255.255.255.0

---

### Post by seeker1458 on 2008-10-08
Subnetting is VERY complex.  Could you describe you layout in more detail and what you are attempting to accomplish by using two different ip schemes if both are connected to the internet?

---

### Post by ootoaoo on 2008-10-08
What do you mean by subneting?

Basically I just want my server to have 2 public IPs.  And I need it to use the 192.168.0.x network as the gateway as there are other internal PCs it connects to.

---

### Post by cariboo on 2008-10-08
You need to setup nat for your setup to work. Have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

It will walk you through setting up your network.

Jim

---

### Post by ootoaoo on 2008-10-08
But I don't want my Ubuntu machine to be a gateway to my other computers... that's not what I'm trying to do at all.  I just want my Ubuntu machine to respond to requests from either NIC

---

### Post by mbert on 2008-10-09
If you are connecting eth1 to a seperate gateway/router you have to configure it to use that router as a gateway and configure NAT on the router so your external requests get redirected to the proper IP.

i.e.:
auto eth1
iface eth1 inet static

address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

Check your gateway/router settings to see what the gateway ip is and any subnet settings it has.  Then make sure to setup NAT to redirect your requried services to 192.168.1.10

---

