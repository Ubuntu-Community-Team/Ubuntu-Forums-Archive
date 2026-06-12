---
title: "Trouble with Static IP's with VirtualBox"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by tennis_mutt on 2008-06-19
I am setting up a system to test various platform with.  I am using Ubuntu 
8.04 64 with VirtualBox os a system with 1 network card.  I want to use static ip addresses which is giving me a lot of problems.  The setup I would like is as follows:
   Ubuntu host ip is 192.168.1.140
   Windows XP is 192.168.1.141
   Open Solaris is 192.168.1.142
   Red Hat Enterprise Linux is 192.168.1.143

I have installed all these guests using NAT and they all loaded and work OK.
When I try to add the bridges to the interfaces file I run into problems even before I try to add then to the VirtualBox.  When the first bridge br0 is added it removes the ststic IP from the host.  The first bridge also has the same MAC address as the host network card eth0.

**The "interfaces" file**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.140
    netmask 255.255.255.0
    gateway 192.168.1.110

auto br0
iface br0 inet static
    address 192.168.1.141
    netmask 255.255.255.0
    gateway 192.168.1.110
    bridge_ports eth0

auto br1
iface br1 inet static
    address 192.168.1.142
    netmask 255.255.255.0
    gateway 192.168.1.110
    bridge_ports eth0

auto br2
iface br2 inet static
    address 192.168.1.143
    netmask 255.255.255.0
    gateway 192.168.1.110
    bridge_ports eth0



**The output of ifconfig**

br0       Link encap:Ethernet  HWaddr 00:1b:b9:c6:d5:6b
          inet addr:192.168.1.141  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:fec6:d56b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:51054 (49.8 KB)  TX bytes:5653 (5.5 KB)

br1       Link encap:Ethernet  HWaddr e2:94:4a:19:48:6d
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e094:4aff:fe19:486d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:3951 (3.8 KB)

br2       Link encap:Ethernet  HWaddr 42:80:89:fd:46:89
          inet addr:192.168.1.143  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4080:89ff:fefd:4689/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:3951 (3.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:1b:b9:c6:d5:6b
          inet6 addr: fe80::21b:b9ff:fec6:d56b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:59072 (57.6 KB)  TX bytes:6195 (6.0 KB)
          Interrupt:20 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88300 (86.2 KB)  TX bytes:88300 (86.2 KB)



I have read just about everything I cound fing in these forums over the last 2 weeks and have come up with no solutions.

I am not showing all the VirtoulBox info because the host network is not working at this point.  

If anyone has something like this working I would like to see the "interfaces" file and the output of ifconfig to study.  

I sure that I am doing something wrong but I ams at a loss now.

I have tried this with vmware and it worked without any problem.  If I can see the ifconfig output of a working system with static IP address it may help.

---

### Post by superprash2003 on 2008-06-19
why dont you try doing this via system->administration->network

---

### Post by tennis_mutt on 2008-06-19
I looked at the network utility, but I can see no way to create the bridges with it.  Is there an option I am missing?

---

