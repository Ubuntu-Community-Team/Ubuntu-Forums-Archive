---
title: "Can`t connect to inet trough router"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Feelout on 2007-10-21
I just can`t connect to internet using Ubuntu 6.10 (i tried also 7.04 liveCD but it gave me same results)

I watch many different threads on this forum but they didn`t work.
Here`s output of some commands:

```

1.route -n

&#1056;&#1118;&#1056;°&#1056;±&#1056;»&#1056;&#1105;&#1057;&#8224;&#1056;° &#1056;&#1112;&#1056;°&#1057;&#1026;&#1057;&#8364;&#1057;&#1107;&#1057;&#8218;&#1056;&#1105;&#1056;·&#1056;°&#1057;&#8224;&#1056;&#1105;&#1056;&#1105; &#1057;&#1039;&#1056;&#1169;&#1057;&#1026;&#1056;° &#1056;&#1111;&#1057;&#1026;&#1056;&#1109;&#1057;&#8218;&#1056;&#1109;&#1056;&#1108;&#1056;&#1109;&#1056;»&#1056;° IP
Destination Gateway Genmask Flags Metric Ref Use Iface

2.cat /etc/resolv.conf - did nothing

3.host www.google.com

;; connection timed out; no servers could be reached

4.ping www.google.com

ping: unknown host www.google.com

5.sudo ethtool eth0

Settings for eth0:
No data available

6.ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0F:EA:58:50:B2  
          inet6 addr: fe80::20f:eaff:fe58:50b2/64 &#1056;&#8221;&#1056;&#1105;&#1056;°&#1056;&#1111;&#1056;°&#1056;·&#1056;&#1109;&#1056;&#1029;:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6408 (6.2 KiB)
          Interrupt:177 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1056;&#8221;&#1056;&#1105;&#1056;°&#1056;&#1111;&#1056;°&#1056;·&#1056;&#1109;&#1056;&#1029;:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89756 (87.6 KiB)  TX bytes:89756 (87.6 KiB)

7.lspci

00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0392 (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
04:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

8.lspci -n

00:00.0 0600: 8086:2770 (rev 02)
00:01.0 0604: 8086:2771 (rev 02)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.3 0604: 8086:27d6 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:244e (rev e1)
00:1f.0 0601: 8086:27b8 (rev 01)
00:1f.2 0101: 8086:27c0 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
01:00.0 0300: 10de:0392 (rev a1)
03:00.0 0200: 10ec:8168 (rev 01)
04:01.0 0c00: 1106:3044 (rev 46)

9.ping 192.168.10.1 - ip of my router

connect: Network is unreachable

```

Could you please give me some solution to this?

---

### Post by WedgeHG on 2007-10-21
The first thing I notice is that your network interface doesn't have an IP address on it. Try going to System->Administration->Network and playing around with that. It should be set up for "Automatic configuration (DHCP)". If that doesn't work, assigning it an IP that you know isn't already in use (maybe 192.168.10.2).

---

### Post by Feelout on 2007-10-22
It was set for "Authotic configuration (DHCP)",I changed it to static ip,entered some and it still didn`t work. Maybe I should add something to route table manually?

---

### Post by froy02 on 2007-10-22
It looks like your card is detected because the hardware numbers are there.  Try to move your cable to another slot of your DSL or swap cables.  
I hope that works.


Froy

---

### Post by Feelout on 2007-10-23
Didn`t work as well :(

---

