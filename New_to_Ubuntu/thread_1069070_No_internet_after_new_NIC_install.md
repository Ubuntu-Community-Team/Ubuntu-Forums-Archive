---
title: "No internet after new NIC install"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by bandy on 2009-02-13
I am running a file server, a Ubuntu desktop, Windows desktop and a laptop.

I have just installed a new Netgear (RTL88169)Gigabit NIC which appears to be working for file sharing but - on the Intrepid based desktop which has the new NIC - without any connections to the internet or email systems.

Obviously I have missed something, or don't yet have the ability to spot the problem.  Hence this plea for help.

For your information I show the contenets of the amended sections.

ifconfig

eth1      Link encap:Ethernet  HWaddr 00:1e:2a:c8:e7:33  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:fec8:e733/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17350 (17.3 KB)  TX bytes:21093 (21.0 KB)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7088 (7.0 KB)  TX bytes:7088 (7.0 KB)

pan0      Link encap:Ethernet  HWaddr a6:46:45:0e:49:09  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vbox0     Link encap:Ethernet  HWaddr 3a:21:34:a3:37:67  
          inet6 addr: fe80::3821:34ff:fea3:3767/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Interfaces

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

Resolve.conf

nameserver 192.168.0.1

Route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth1

Thanks in advance for any advice you are able to offer

---

### Post by cerealtx on 2009-02-14
> **bandy said:**
> I am running a file server, a Ubuntu desktop, Windows desktop and a laptop.

I have just installed a new Netgear (RTL88169)Gigabit NIC which appears to be working for file sharing but - on the Intrepid based desktop which has the new NIC - without any connections to the internet or email systems.

Obviously I have missed something, or don't yet have the ability to spot the problem.  Hence this plea for help.

For your information I show the contenets of the amended sections.

ifconfig

eth1      Link encap:Ethernet  HWaddr 00:1e:2a:c8:e7:33  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:fec8:e733/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17350 (17.3 KB)  TX bytes:21093 (21.0 KB)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7088 (7.0 KB)  TX bytes:7088 (7.0 KB)

pan0      Link encap:Ethernet  HWaddr a6:46:45:0e:49:09  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vbox0     Link encap:Ethernet  HWaddr 3a:21:34:a3:37:67  
          inet6 addr: fe80::3821:34ff:fea3:3767/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Interfaces

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

Resolve.conf

nameserver 192.168.0.1

Route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth1

Thanks in advance for any advice you are able to offer
so you can stay in the network but not get out, possible DNS issue, have you tried pinging? what kind of router do you have? 198.168.0 is abnormal most routhers default to 192.168.1/100 or 192.168.254/255

---

### Post by superprash2003 on 2009-02-14
are you able to open [http://74.125.45.100](http://74.125.45.100) .. is eth1 your netgear NIC card?

---

### Post by bandy on 2009-02-15
First; my apologies for not coming back sooner.  My wife has ulcers on her feet and they've been rather a nuisance to her over the last few days.

Second;  The router address is correct at 192.168.0.1 it is a Netgear DG834PN.

Third; With regard to [http://74.125.45.100](http://74.125.45.100)  I could ping the address but not open it.

Fourth; Yesterday I noticed that the Ubuntu desktop was not recognizing a usb and an esata hard drive.   Later I re-enabled the old (onboard) lan interface in the bios and to my surprise found that everything was working again.   I then disabled the onboard lan and the problems began again.

Fifth;  Today I downloaded some 20 updates and suddenly all seems to be working again - with the onboard lan disabled.

I have absolutely no idea whether this has permanently solved whatever the problem is/was but it certainly appears to have done so at the moment.

Thank you for your help

---

