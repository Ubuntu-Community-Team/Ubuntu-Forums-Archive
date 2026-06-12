---
title: "RTL8187 annoyance"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by bluefightingcat on 2007-11-26
Hi,

I have recently god hold of an ASUS M2N32-SLI Deluxe/Wireless Motherboard. The motherboard comes with a built in Wireless device. The device seems to be connect via some sort USB system. The motherboard has an external antenna. The Wireless device is a RealTek 8187.

lsusb: 

> Bus 001 Device 003: ID 068e:00ff CH Products, Inc. Flight Sim Yoke
Bus 001 Device 001: ID 0000:0000
Bus 001 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 001 Device 004: ID 03f0:0704 Hewlett-Packard DeskJet 825c
Bus 002 Device 005: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 002 Device 001: ID 0000:0000


I am running Gutsy AMD64. The wireless device is recognised and it connects to my router. However it keeps disconnecting and having a difficult time reconnecting. So I was wondering whether anybody has any idea what might be causing thing.

ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:1D:60:4F:04:A5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:1D:60:4F:1D:19
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11795 (11.5 KB)  TX bytes:11795 (11.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:29:2E:51
          inet addr:62.78.150.23  Bcast:62.78.151.255  Mask:255.255.248.0
          inet6 addr: fe80::215:afff:fe29:2e51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14430581 (13.7 MB)  TX bytes:7069009 (6.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-29-2E-51-00-00-00-00-00-00-00-00-00                                                              -00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



iwconfig:

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Malta"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:90:4B:7A:D1:9B
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=43/64  Signal level=17/65
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


/etc/network/interfaces:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Malta
wireless-key s:xxxxxxxxxxxxxxxxx


---

### Post by daengbo on 2007-11-26
Are you sure that your problem doesn't lie here?

Link Quality=43/64 Signal level=17/65

---

### Post by bluefightingcat on 2007-11-27
Well thats the wierd thing. In Windows my wireless works fine. I haven't had to move the router or anything to get my wireless to work in Windows. 

Does the Linux Wireless driver have anything to do with catching a signal?

BFC

---

### Post by daengbo on 2007-11-27
It should be irrelevent.

---

### Post by bluefightingcat on 2007-11-27
I blacklisted ipv6. So far so good. I've got my fingers crossed. If this doesn't work then I will try ndiswrapper. 

BFC

---

### Post by Tlingit on 2008-05-25
If you get this? I have that same set up and my connect doesn't work?

I will try un hiding my ssid but that is strange. ndiswrapper doesn't work.

---

