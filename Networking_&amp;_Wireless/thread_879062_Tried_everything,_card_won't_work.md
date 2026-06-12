---
title: "Tried everything, card won't work"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Boompat on 2008-08-03
Hi, I'm trying to get my wireless card running on my R31 Thinkpad. I've downloaded and installed ndiswrapper-utils and ndisgtk. I've also installed the windows driver using the Windows Wireless Drivers. After all this, my card still doesn't seem to work. Did I forget to do something?

---

### Post by tamoneya on 2008-08-03
run these commands in terminal (applications -> accessories -> terminal) and please tell us the output:```
sudo lshw -C network
ifconfig
lspci
```

---

### Post by Boompat on 2008-08-03
> **tamoneya said:**
> run these commands in terminal (applications -> accessories -> terminal) and please tell us the output:```
sudo lshw -C network
ifconfig
lspci
```

Alright,

This is for sudo lshw-c network-
```
Hardware Lister (lshw) - B.02.12.01

usage: lshw [-format] [-options ...]

       lshw -version



	-version        print program version (B.02.12.01)



format can be

	-html           output hardware tree as HTML

	-xml            output hardware tree as XML

	-short          output hardware paths

	-businfo        output bus information



options can be

	-class CLASS    only show a certain class of hardware

	-C CLASS        same as '-class CLASS'

	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )

	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

	-quiet          don't display status

	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


```

lspci-
```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)

00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)

01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

01:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

```

ifconig-
```
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:4f:85:0b  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1960 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1960 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:98000 (95.7 KB)  TX bytes:98000 (95.7 KB)

```

---

### Post by tamoneya on 2008-08-03
rerun the first one.  Capitalization counts.  That is a capital "C".

---

### Post by Boompat on 2008-08-03
> **tamoneya said:**
> rerun the first one.  Capitalization counts.  That is a capital "C".

Alright, I reran the first one and got:
```
 I re  *-network               

       description: Ethernet interface

       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@0000:01:08.0

       logical name: eth0

       version: 42

       serial: 00:0a:e4:4f:85:0b

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

  *-network UNCLAIMED

       description: Ethernet controller

       product: RTL8180L 802.11b MAC

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 1

       bus info: pci@0000:02:00.0

       version: 20

       width: 32 bits

       clock: 33MHz

       capabilities: pm cap_list

       configuration: latency=0 maxlatency=64 mingnt=32


```

---

### Post by tamoneya on 2008-08-03
have you done this: [https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L)

specifically the blacklisting

---

### Post by Boompat on 2008-08-03
I blacklisted the two things on the list, and nothing happened.

---

### Post by Boompat on 2008-08-03
Does anyone know anything that I could do?

---

### Post by dvdljns on 2009-10-19
I have the same problem so if you find an answer please post it.
Thanks.

---

