---
title: "Cant find second Network device (I think)"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by Bill007 on 2006-11-20
Kia ora (Maori languge greeting for Hello)

I have set up a server for production ubuntu 5.10 base system

after installing all the neccasry packages

One of them being Webmin which I want to configure thru a remote machine

But I cant even see the the machine

The server has

two network cards

eth0 set for dhcp {INTERGRATED ONBOARD NETWORK DEVICE working on the net fine}

eth1 for networking (not working at all PCI DEVICE)

The default interface is set to eth0 which is working fine

**/etc/network/interfaces**

auto lo
iface lo inet loopback

mapping hotplug
script grep
map eth0

#the primary network interface

inface eth0 inet dhcp


auto eth1
iface eth1 inet static
address 192.168.2.100
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255

**ifconfig**

eth0

Link encap:Ethernet HWaddr 00:14:855:18:6F
inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 :fe80::214:85ff:fed5:186f/64 scope:link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:282 errors:0 dropped:0 overruns:0 frame:0
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:31713 (38.9 KiB) TX bytes:2430 (2.3 KiB)
Interrupt:23 Base address:0xc400


lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/126 scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 KiB) TX bytes:0 (0.0 KiB)

**route**

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 * 255.255.255.0 U 0 0 0 eth0
default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

**ifdown eth1**

Failed to open stat interface eth1 not configured


[B]ifup eth1
[/B]
error while getting interface flags nosuch device
SIOCIFNETMASK No such device
192.168.2.255 Uknown Host

Failed to bring up device

**lspci -v**

0000: 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
flags:fast devsel
capabilities: <available only to root>

0000: 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
flags:fast devsel

0000: 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
flags:fast devsel

0000: 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
flags:fast devsel

0000:01:00.0 VGA Compatable controller :via Technologies, Inc :: Unknowen dvice 3 108 (rev 01(prog if 00 [VGA])
Sub system:Giga-byte Technology:device unknowen d000
flags:bus master, 66MHZ, medium devsel,latency 32 IRQ 10
memory at e4000000 (32-bit prefetchable)[size=64M]
memory at e8000000 (32-bit non prefetchable)[size=16M]
capabilities:<available only to root>


after hours of searching and chasing my tail my conclusion is

UBUNTU does not seem to see the second network device at all so how does one get this sorted so ubuntu will see the device

Im out of solutions

---

