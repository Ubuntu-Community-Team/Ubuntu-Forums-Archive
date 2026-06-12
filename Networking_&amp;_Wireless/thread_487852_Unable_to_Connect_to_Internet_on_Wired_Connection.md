---
title: "Unable to Connect to Internet on Wired Connection"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by XCrawler on 2007-06-29
Hi,

I recently just upgraded from Edgy to Feisty Fawn on my old laptop (no wireless). Everything is working fine except my internet connection. I can't even ping my gateway. I've tried the solution from some article on the internet by commenting out the eth0 and leaving only the loopback interface then do dhclient, but it didn't work. I've also tried to use the static IP address. It also didn't work.

I've been spending few days to search for the solution from google, ubuntuforums, etc. with no help. I don't feel like downgrading to Edgy again. So, hopefully you guys can help me.

ifconfig
```

eth0   Link encap:Ethernet  HWaddr 00:00:E2:8D:4C:9E  
          inet6 addr: fe80::200:e2ff:fe8d:4c9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:3314 dropped:0 overruns:0 frame:0
          TX packets:460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:660 (660.0 b)  TX bytes:99029 (96.7 KiB)
          Interrupt:10 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:00:E2:8D:4C:9E  
          inet addr:169.254.7.178  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120724 (117.8 KiB)  TX bytes:120724 (117.8 KiB)


```

lspci
```

00:00.0 Host bridge: ALi Corporation M1671 Super P4 Northbridge [AGP4X,PCI and SDR/DDR] (rev 02)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:13.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#address 192.168.1.70
#netmask 255.255.255.0
#gateway 192.168.1.254

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

dhclient
```

There is already a pid file /var/run/dhclient.pid with pid 10251
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:00:e2:8d:4c:9e
Sending on   LPF/eth0/00:00:e2:8d:4c:9e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Thanks.

---

### Post by Dark Hornet on 2007-12-20
I am having the EXACT same issue.

---

