---
title: "Wired Connection Problem"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by gmoeck on 2007-06-18
I recently moved, and instead of using a wireless,my new roommates use a wired dsl setup. When I plug the ethernet cable into my tablet pc running xptablet, I amable to connect to the network just fine(how I'm typing this),but when I plug it into my desktop, I get no dchp response. Any help would be appreciated.

[PHP]gmoeck@gmoeck-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:B5:55:32  
          inet6 addr: fe80::240:caff:feb5:5532/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51118 (49.9 KiB)  TX bytes:24773 (24.1 KiB)
          Interrupt:18 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:CA:B5:55:32  
          inet addr:169.254.6.66  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7715 (7.5 KiB)  TX bytes:7715 (7.5 KiB)

ra1       Link encap:Ethernet  HWaddr 00:18:F8:2E:4E:0C  
          inet6 addr: fe80::218:f8ff:fe2e:4e0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:216608 (211.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:17 

ra1:avahi Link encap:Ethernet  HWaddr 00:18:F8:2E:4E:0C  
          inet addr:169.254.4.7  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

gmoeck@gmoeck-desktop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6536
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra1/00:18:f8:2e:4e:0c
Sending on   LPF/ra1/00:18:f8:2e:4e:0c
Listening on LPF/eth0/00:40:ca:b5:55:32
Sending on   LPF/eth0/00:40:ca:b5:55:32
Sending on   Socket/fallback
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[/PHP]

---

### Post by dannyboy79 on 2007-06-18
can you please show us the output of 

lspci -v

also, you don't by chance 2 interfaces that are set to auto within your /etc/network/interfaces file do you?

---

### Post by gmoeck on 2007-06-18
[PHP]gmoeck@gmoeck-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
gmoeck@gmoeck-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e4000000-e6ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e7000000-e8ffffff
        Prefetchable memory behind bridge: 40000000-400fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12) (prog-if 80 [Master])
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12) (prog-if 00 [UHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at d000 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: medium devsel, IRQ 11
        I/O ports at 5000 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12) (prog-if 00 [UHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at d800 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=64]

01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e5000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e6000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Linksys WMP54G ver 4.1
        Flags: bus master, slow devsel, latency 32, IRQ 17
        Memory at e8000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c000 [size=256]
        Memory at e8008000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 40000000 [disabled] [size=64K]
        Capabilities: <access denied>

[/PHP]

---

### Post by dannyboy79 on 2007-06-18
> **gmoeck said:**
> [PHP]gmoeck@gmoeck-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
gmoeck@gmoeck-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e4000000-e6ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e7000000-e8ffffff
        Prefetchable memory behind bridge: 40000000-400fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12) (prog-if 80 [Master])
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12) (prog-if 00 [UHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at d000 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: medium devsel, IRQ 11
        I/O ports at 5000 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12) (prog-if 00 [UHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at d800 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 900c
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=64]

01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e5000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e6000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Linksys WMP54G ver 4.1
        Flags: bus master, slow devsel, latency 32, IRQ 17
        Memory at e8000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c000 [size=256]
        Memory at e8008000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 40000000 [disabled] [size=64K]
        Capabilities: <access denied>

[/PHP]
Yeap, I was afraid of that. You got a ralink wireless nic. You'll have to check this out as the Ubuntu's drivers provided by the install do not work.
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61)

and instead of using the rt73, use the rt61 provided here:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
you can just use your wired connection to download it. good luck

---

### Post by gmoeck on 2007-06-18
Just want to make sure I'm following. My wireless card drivers are causing the problem, or the nic drivers? I assume that if there was a wireless router I could access I could get that working, but there isn't, so i'm using the wired. So to clarify, dl different driver on my tablet using the wired, and transfer it to my desktop?

---

### Post by gmoeck on 2007-06-18
> **dannyboy79 said:**
> Yeap, I was afraid of that. You got a ralink wireless nic. You'll have to check this out as the Ubuntu's drivers provided by the install do not work.
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61)

and instead of using the rt73, use the rt61 provided here:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
you can just use your wired connection to download it. good luck

I'm not using the wireless card at all,as there is no wireless network present. When the wired is plugged into the desktop running ubuntu, i get no dhcp response from the router,but when it's plugged into my tablet pc running xp tablet,it works fine.

---

### Post by gmoeck on 2007-06-18
When I set up the connection with a static ip that is the same as my tablet pc's when it works(ipconfig for info) it still doesn't work. However, when i ping 192.168.0.1(router ip)the light on my cpu blinks out a yellow, and the router blinks, which I assume means it is recieving the packet,since when i ping it from the tablet it does the same thing. But it's not sending the return packet for some reason to the desktop. Any ideas?

---

### Post by gmoeck on 2007-06-18
bump

---

### Post by dannyboy79 on 2007-06-18
try to blacklist the rt61 module within the /etc/modules/blacklist
and see if that helps. also, do a search around these forums regarding your wired connection NIC card, which is the Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10). I thought you were saying that you wanted to get wireless working but since you're not, you shou;d blacklist it since there's known problems with it which might be causing problems.

---

