---
title: "New user - Network problems"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by KenLane on 2010-01-05
I am completely new to Ubuntu.

The PC is new and dual booting Windows 7 and Ubuntu 9.10 (using Gnome) - both 64 bit
There are no issues with Windows, suggesting hardware is sound

In Ubuntu:

I can ping an external site such as bbc.co.uk
I can ping an internal object on the LAN using an IP address such as 192.168.0.3
If I ping the same object using its name I get device unreachable
(If I ping the Ubuntu PC by name from another PC on the LAN it is not found.)

If I go to Places, Network, Windows network and try to drill through sometimes I just get a blank screen; other times I see two objects:
(a) my Windows workgroup
(b) something called CS_UKNET which means nothing to me but drilling through that shows an object LT-102A which again means nothing

If I check the graphical interface for network connections I see Wired Network - Device Not Managed
Under wired network connections I see lfupdown (eth0) with Last Used showing never

etc/network/interfaces reads:

> auto eth0
iface eth0 inet dhcp

auto lo
iface lo inet loopbackI added the first two lines to see if they would help but there was no obvious effect

There is no file /etc/modprobe.d/aliases

The following output is the result of trying various ideas read in the forum:

> kenneth@LH7UB:~$ sudo dhclient eth0
[sudo] password for kenneth: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:26:18:a9:3b:51
Sending on   LPF/eth0/00:26:18:a9:3b:51
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.9 from 192.168.0.1
DHCPREQUEST of 192.168.0.9 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.9 from 192.168.0.1
bound to 192.168.0.9 -- renewal in 123198 seconds.> kenneth@LH7UB:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:26:18:a9:3b:51
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.9 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:35 ioport:c800(size=256) memory:fafff000-faffffff(prefetchable) memory:faff8000-faffbfff(prefetchable) memory:fbcf0000-fbcfffff(prefetchable)
> kenneth@LH7UB:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:26:18:a9:3b:51  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fea9:3b51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2650687 (2.6 MB)  TX bytes:366802 (366.8 KB)
          Interrupt:35 Base address:0xe000 Background

---

### Post by VastOne on 2010-01-05
> **KenLane said:**
> I am completely new to Ubuntu.

The PC is new and dual booting Windows 7 and Ubuntu 9.10 (using Gnome) - both 64 bit
There are no issues with Windows, suggesting hardware is sound

In Ubuntu:

I can ping an external site such as bbc.co.uk
I can ping an internal object on the LAN using an IP address such as 192.168.0.3
If I ping the same object using its name I get device unreachable
(If I ping the Ubuntu PC by name from another PC on the LAN it is not found.)

If I go to Places, Network, Windows network and try to drill through sometimes I just get a blank screen; other times I see two objects:
(a) my Windows workgroup
(b) something called CS_UKNET which means nothing to me but drilling through that shows an object LT-102A which again means nothing

If I check the graphical interface for network connections I see Wired Network - Device Not Managed
Under wired network connections I see lfupdown (eth0) with Last Used showing never

etc/network/interfaces reads:

I added the first two lines to see if they would help but there was no obvious effect

There is no file /etc/modprobe.d/aliases

The following output is the result of trying various ideas read in the forum:

Background

Are you going through a router and or a proxy?  Is this at school, work?  ISP information?

---

### Post by KenLane on 2010-01-05
This is a home network with a Netgear DGN2000 ADSL wireless router but I am connecting over wire.  The network also includes a Sinology NAS box, a network printer, a windows PC and a switch so that I can plug in my work laptop as the router only has 4 ports.

There are no problems connecting to the internet.  I can download Ubuntu updates and browse the web with Firefox.  The fundamental issues are that from Ubuntu I cannot see my own LAN which creates problems for network printing or accessing data on the NAS box.  In addition, Ubuntu is saying that the network is not managed in the graphical interface.

---

