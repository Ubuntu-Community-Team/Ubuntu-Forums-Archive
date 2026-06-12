---
title: "Wrong interface used on every boot/reboot"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by BadDolphin on 2006-11-01
New to ubuntu and all forms of linux except some basic bash shell stuff... here's the problem I'm having:

When I boot the computer, it fails to get an IP; I click on the systray icon that looks like two computers, and see two interfaces listed.  I simply switch to the other one, and all is fine.  But I have to switch it on EVERY reboot.

I thought that this PC only has one physical interface because there's only one ethernet jack on the machine.  Obviously it's eth1 that should be used and never eth0 (where/what it is I have no idea, but it must exist since it has a MAC address!)

I've searched various ways on google and in forums, but couldn't find this specific issue.  Is anyone still passing out Halloween Clues?  The ifconfig info is below in case it helps any.

$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:24:E5:33:A5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:168 (168.0 b)
          Interrupt:169 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:01:80:6A:41:F5
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe6a:41f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2711400 (2.5 MiB)  TX bytes:401854 (392.4 KiB)
          Interrupt:209 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

---

### Post by plewisfdx on 2006-11-01
Your /etc/network/interfaces file is commanding "auto eth0."  

Just change this line to "auto eth1" and it will start that interface automatically upon reboot.

---

### Post by BadDolphin on 2006-11-01
Thanks for the response... but it seems to already be set that way... when I open the file, it reads as follows:
---------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
---------------------

---

