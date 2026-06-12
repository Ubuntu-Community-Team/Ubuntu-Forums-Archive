---
title: "Dynamically switching between two NICs"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by sigmanu_nyte on 2007-11-20
Here is my problem.  My laptop is connected to two different networks(1 wireless & 1 Hardwired)
When i am connected to the hardwired connection, i'd like that connection to be used no matter what.  When i disconnect, I'd like to "auto-magically" be able to use my wireless adapter with out any configuration like having to restart network services or ifdown/ifup etc.  There in lies my problem.  When i disconnect from my hardwired connection, I have to go thru all kinds of gyration to get traffic moving to my wireless card, instead of the laptop just recognizing that the connection is gone and moving traffic over.  The same is true if i am working wirelessly and i plug into my hardwired connection.  Just to make sure i'm clear, I am connected and have received ip addresses on both interfaces from DHCP. 

**_Dell D830 running Kubuntu 7.10_**
[B][U]
uname -a output
[/U][/B]

Linux wookibuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
 
**_lspci output_**

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


**_/etc/network/interfaces _**

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp
wireless-essid EagleAir Network

auto eth0
iface eth0 inet dhcp


**_ifconfig output_**

eth0      Link encap:Ethernet  HWaddr 00:19:B9:7C:11:91
          inet addr:131.95.203.182  Bcast:131.95.203.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe7c:1191/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:55697218 (53.1 MB)  TX bytes:8107446 (7.7 MB)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 00:1B:77:52:C2:76
          inet addr:131.95.175.213  Bcast:131.95.175.255  Mask:255.255.240.0
          inet6 addr: fe80::21b:77ff:fe52:c276/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:199 dropped:3914 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1152191 (1.0 MB)  TX bytes:548749 (535.8 KB)
          Interrupt:17 Base address:0xe000 Memory:fe8ff000-fe8fffff

**_route output_**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.95.203.0    *               255.255.255.0   U     0      0        0 eth0
131.95.160.0    *               255.255.240.0   U     0      0        0 eth1
default         131.95.203.1    0.0.0.0         UG    100    0        0 eth0
default         131.95.160.1    0.0.0.0         UG    100    0        0 eth1

---

