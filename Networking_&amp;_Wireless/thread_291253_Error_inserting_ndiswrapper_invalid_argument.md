---
title: "Error inserting ndiswrapper: invalid argument"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by WebDrake on 2006-11-02
Hello all,

I'm trying to set up my wireless card, a Dell Truemobile 1450, as per instructions at [http://www.ubuntuforums.org/showthread.php?p=255533](http://www.ubuntuforums.org/showthread.php?p=255533)

When I type sudo modprobe ndiswrapper, I get an error message:
```

WARNING: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

I'm not experienced with working with kernel modules, so don't know how to interpret this.

ifconfig -a gives,
```

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:10:58:D0
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe10:58d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1123332 (1.0 MiB)  TX bytes:157459 (153.7 KiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:90:96:98:F3:60
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
So I wonder if perhaps the eth1 (which thinks it's a wireless connection) is causing the trouble.

Any ideas?  Many thanks in advance for any help. :)

---

### Post by WebDrake on 2006-11-02
Blacklisting the bcm43xx module seemed to help here.

modprobe now accepts ndiswrapper, but it still seems impossible to connect to the network.  Here's the results of tail /var/log/messages :
```

Nov  2 16:13:24 wakeling kernel: [17179702.588000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Nov  2 16:13:25 wakeling kernel: [17179702.692000] ndiswrapper: driver bcmwl5 () loaded
Nov  2 16:13:25 wakeling kernel: [17179702.692000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
Nov  2 16:13:25 wakeling kernel: [17179702.696000] ndiswrapper: using irq 7
Nov  2 16:13:25 wakeling kernel: [17179703.520000] wlan0: vendor: ''
Nov  2 16:13:25 wakeling kernel: [17179703.520000] wlan0: ethernet device 00:90:96:98:f3:60 using NDIS driver bcmwl5, 14E4:4324.5.conf
Nov  2 16:13:25 wakeling kernel: [17179703.520000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Nov  2 16:13:25 wakeling kernel: [17179703.572000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Nov  2 16:13:25 wakeling kernel: [17179703.668000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```
... so, it seems that the new wireless interface is named eth1.  But if I try to enable eth1 via System -> Administration -> Networking, it fails to activate.

sudo ifdown eth1 gives,
```

killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:90:96:98:f3:60
Sending on   LPF/eth1/00:90:96:98:f3:60
Sending on   Socket/fallback

```
while sudo ifup eth1 gives,
```

There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:90:96:98:f3:60
Sending on   LPF/eth1/00:90:96:98:f3:60
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I don't follow what could be the issue here.  The Windows driver used with ndiswrapper works on another Linux distro (SUSE) so I don't think that's at fault.

---

