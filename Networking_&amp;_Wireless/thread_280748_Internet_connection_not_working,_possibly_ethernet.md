---
title: "Internet connection not working, possibly ethernet not installed?"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by platinummonkey on 2006-10-19
hey, i am having internet connection problems, i just installed ubuntu the other day, and was using windows xp. I cannot seem to get any sort of connection, and the networking tools do not show an etherenet connection, only a modem that i have the option of enabling (i am not connected through a modem) i am connected to a college network, and once i have connection i should be able to register my computer to the network and have internet access, but thats the problem, i do not know how to get it too connect. :P I am using ubuntu 6.06

From a similar thread: 
> wieman01

Please run these commands from a terminal window & post the output:

Quote:
ifconfig  

Quote:
iwconfig  

Quote:
iwlist scan  

Quote:
sudo /etc/init.d/networking restart  

Quote:
route  

Quote:
sudo gedit /etc/network/interfaces  

Quote:
sudo lspci  

Quote:
sudo lshw  

Then we'll see what's going on. Also tell me a bit more about your network: DHCP vs. Static IP, encryption (e.g. WEP, WPA), etc.

i typed in the commands from the previous thread here into my system and i got:

platinummonkey@platinummonkeydsk:~$
ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1343 errors:0 dropped:0 overruns:0 frame:0
TX packets:1343 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:101416 (99.0 KiB) TX bytes:101416 (99.0 KiB)
platinummonkey@platinummonkeydsk:~$
iwconfig
lo no wireless extensions.
sit0 no wireless extensions.
platinummonkey@platinummonkeydsk:~$
iwlistscan
bash: iwlistscan: command not found
platinummonkey@platinummonkeydsk:~$
iwlist scan
lo Interface doesn't support scanning.
sit0 Interface doesn't support scanning.
platinummonkey@platinummonkeydsk:~$
sudo /etc/init.d/networking restart
Password:
* Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
[ ok ]
platinummonkey@platinummonkeydsk:~$
route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
platinummonkey@platinummonkeydsk:~$
sudo gedit /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
platinummonkey@platinummonkeydsk:~$
sudo lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2
RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM
memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory:
nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia
Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation
MCP2A ISA bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev
a1)
0000:00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
0000:00:0b.0 IDE interface: nVidia Corporation nForce2 Serial ATA Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
0000:02:0b.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 (rev 31)
platinummonkey@platinummonkeydsk:~$
sudo lshw
platinummonkeydsk
description: Desktop Computer
width: 32 bits
capabilities: smbios2.2
dmi2.2
configuration: boot=normal chassis=desktop uuid=0000000000000000000000508D7594A8
*core
description: Motherboard
product: NF7II series(Nvidia nForceMCP2S)
vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)
physical id: 0
version: v0.1
slot: PCI4
*firmware
description: BIOS
vendor: Phoenix Technologies, LTD
physical id: 0
version: 6.00 PG (04/07/2005)
size: 128KB
capacity: 448KB
capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd
int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard
int14serial int17printer int10video acpi usb agp ls120boot zipboot
*cpu
description: CPU
product: AMD Athlon(tm) XP 2600+
vendor: Advanced Micro Devices [AMD]
physical id: 4
bus info: cpu@0
version: 6.8.1
slot: Socket A
size: 2083MHz
capacity: 3GHz
width: 32 bits
clock: 166MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
*cache:
0
description: L1 cache
physical id: 9
slot: Internal Cache
size: 128KB
capacity: 128KB
capabilities: synchronous internal writeback
*cache:
1
description: L2 cache
physical id: a
slot: External Cache
size: 256KB
capacity: 256KB
capabilities: synchronous external writeback
*memory
description: System Memory
physical id: 1a
slot: System board or motherboard
size: 1536MB
capacity: 1536MB
*bank:
0
description: DIMM
physical id: 0
slot: A0
size: 512MB
*bank:
1
description: DIMM
physical id: 1
slot: A1
size: 512MB
*bank:
2
description: DIMM
physical id: 2
slot: A2
size: 512MB
*pci
description: Host bridge
product: nForce2 AGP (different version?)
vendor: nVidia Corporation
physical id: d0000000
bus info: pci@00:00.0
version: c1
width: 32 bits
clock: 66MHz
resources: iomemory:d0000000dfffffff
*memory:
0 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 1
vendor: nVidia Corporation
physical id: 0.1
bus info: pci@00:00.1
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
1 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 4
vendor: nVidia Corporation
physical id: 0.2
bus info: pci@00:00.2
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
2 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 3
vendor: nVidia Corporation
physical id: 0.3
bus info: pci@00:00.3
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
3 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 2
vendor: nVidia Corporation
physical id: 0.4
bus info: pci@00:00.4
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
4 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 5
vendor: nVidia Corporation
physical id: 0.5
bus info: pci@00:00.5
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*isa
UNCLAIMED
description: ISA bridge
product: MCP2A ISA bridge
vendor: nVidia Corporation
physical id: 1
bus info: pci@00:01.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: isa bus_master cap_list
*serial
description: SMBus
product: MCP2A SMBus
vendor: nVidia Corporation
physical id: 1.1
bus info: pci@00:01.1
version: a1
width: 32 bits
clock: 66MHz
capabilities: cap_list
configuration: driver=nForce2_smbus
resources: ioport:ec00ec1f
irq:5
*usb:
0
description: USB Controller
product: MCP2A USB Controller
vendor: nVidia Corporation
physical id: 2
bus info: pci@00:02.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master cap_list
configuration: driver=ohci_hcd
resources: iomemory:e2002000e2002fff
irq:185
*usbhost
product: OHCI Host Controller
vendor: Linux 2.6.1526386
ohci_hcd
physical id: 1
bus info: usb@1
logical name: usb1
version: 2.06
capabilities: usb1.10
configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
*usb
description: Keyboard
product: USB Gaming Keyboard Pro
vendor: Chicony
physical id: 4
bus info: usb@1:4
version: 1.20
capabilities: usb2.00
configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
*usb:
1
description: USB Controller
product: MCP2A USB Controller
vendor: nVidia Corporation
physical id: 2.1
bus info: pci@00:02.1
version: a1
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master cap_list
configuration: driver=ohci_hcd
resources: iomemory:e2003000e2003fff
irq:193
*usbhost
product: OHCI Host Controller
vendor: Linux 2.6.1526386
ohci_hcd
physical id: 1
bus info: usb@2
logical name: usb2
version: 2.06
capabilities: usb1.10
configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
*usb
UNCLAIMED
description: Generic USB device
product: Microsoft
vendor: Microsoft
physical id: 3
bus info: usb@2:3
version: 1.00
capabilities: usb2.00
configuration: maxpower=260mA speed=12.0MB/s
*usb:
2
description: USB Controller
product: MCP2A USB Controller
vendor: nVidia Corporation
physical id: 2.2
bus info: pci@00:02.2
version: a2
width: 32 bits
clock: 66MHz
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd
resources: iomemory:e2004000e20040ff
irq:185
*usbhost
product: EHCI Host Controller
vendor: Linux 2.6.1526386
ehci_hcd
physical id: 1
bus info: usb@3
logical name: usb3
version: 2.06
capabilities: usb2.00
configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
*usb
description: Mass storage device
product: JUMPDRIVE SPORT
vendor: LEXAR MEDIA
physical id: 4
bus info: usb@3:4
logical name: scsi2
version: 1.00
serial: 33000001217000016827
capabilities: usb2.00
scsi emulated scsihost
configuration: driver=usbstorage
maxpower=100mA speed=480.0MB/s
*disk
description: SCSI Disk
product: JUMPDRIVE SPORT
vendor: LEXAR
physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sda
version: 1000
serial: 1000S &#65533;&#65533;&#65533;&#65533; &#65533;*F&#65533;W&#65533;&#65533;&#65533;B,&#65533;&#65533;&#65533;&#65533;Pn&#65533;&#65533; &#65533;&#65533;
size: 123MB
capabilities: removable
*disc
physical id: 0
logical name: /dev/sda
size: 123MB
capabilities: partitioned partitioned:dos
*volume
description: FAT16 <32M partition
physical id: 1
logical name: /dev/sda1
capacity: 123MB
capabilities: primary bootable
*multimedia
description: Multimedia audio controller
product: MCP2S AC'97 Audio Controller
vendor: nVidia Corporation
physical id: 6
bus info: pci@00:06.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: driver=Intel ICH
resources: ioport:d800d8ff
ioport:dc00dc7f
iomemory:e2005000e2005fff
irq:193
*pci:
0
description: PCI bridge
product: MCP2A PCI Bridge
vendor: nVidia Corporation
physical id: 8
bus info: pci@00:08.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: pci normal_decode bus_master
*network
UNCLAIMED
description: Ethernet controller
product: Sundance Technology Inc
vendor: Sundance Technology Inc
physical id: b
bus info: pci@02:0b.0
version: 31
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: ioport:b000b07f
iomemory:e0010000e00101ff
irq:201
*ide:
0
description: IDE interface
product: MCP2A IDE
vendor: nVidia Corporation
physical id: 9
bus info: pci@00:09.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: ide bus_master cap_list
configuration: driver=AMD_IDE
resources: ioport:f000f00f
*ide:
0
description: IDE Channel 0
physical id: 0
bus info: ide@0
logical name: ide0
clock: 66MHz
*disk
description: ATA Disk
product: SAMSUNG SP1604N
physical id: 0
bus info: ide@0.0
logical name: /dev/hda
version: TM10031
serial: S013J10YB42097
size: 149GB
capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
configuration: mode=udma5 smart=on
*volume:
0
description: Linux filesystem partition
physical id: 1
bus info: ide@0.0,1
logical name: /dev/hda1
capacity: 144GB
capabilities: primary bootable
*volume:
1
description: Extended partition
physical id: 2
bus info: ide@0.0,2
logical name: /dev/hda2
capacity: 4447MB
capabilities: extended partitioned partitioned:extended
*ide:
1
description: IDE Channel 1
physical id: 1
bus info: ide@1
logical name: ide1
clock: 66MHz
*cdrom
description: DVD writer
product: _NEC DVD_RW ND3500AG
physical id: 0
bus info: ide@1.0
logical name: /dev/hdc
version: 2.18
capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cdr
cdrw
dvd dvdr
configuration: mode=udma2
*disc
physical id: 0
logical name: /dev/hdc
*ide:
1
description: IDE interface
product: nForce2 Serial ATA Controller
vendor: nVidia Corporation
physical id: b
bus info: pci@00:0b.0
logical name: scsi0
logical name: scsi1
version: a3
width: 32 bits
clock: 66MHz
capabilities: ide bus_master cap_list scsihost
configuration: driver=sata_nv
resources: ioport:9f09f7
ioport:bf0bf3
ioport:970977
ioport:b70b73
ioport:cc00cc0f
ioport:d000d07f
irq:177
*pci:
1
description: PCI bridge
product: nForce2 AGP
vendor: nVidia Corporation
physical id: 1e
bus info: pci@00:1e.0
version: c1
width: 32 bits
clock: 66MHz
capabilities: pci normal_decode bus_master
*display:
0
description: VGA compatible controller
product: RV350 AR [Radeon 9600]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@01:00.0
version: 00
size: 256MB
width: 32 bits
clock: 66MHz
capabilities: vga bus_master cap_list
resources: iomemory:b0000000bfffffff
ioport:a000a0ff
iomemory:e1030000e103ffff
irq:209
*display:
1 UNCLAIMED
description: Display controller
product: RV350 AR [Radeon 9600] (Secondary)
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@01:00.1
version: 00
size: 256MB
width: 32 bits
clock: 66MHz
capabilities: cap_list
resources: iomemory:c00

my ehternet port came as part of my mobo (abit nf7-s2)
any help would be great, i think my ethernet port is not installed yet, but thats just a guess, since this is day 2 of using linux :P
any help is greatly appreciated!

---

### Post by lloyd_b on 2006-10-20
I think the answer lies here:

> SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

When you see messages like that, it usually means that there isn't a driver loaded for the ethernet.  Everything else in your post supports that idea.

> 0000:02:0b.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 (rev 31)

Okay, so there is definitely an ethernet controller in there.  The question is: what driver does it take?

A quick search turned up this thread.  It's discussing the driver that you need ("sundance.ko" or "sundance.o"):
[http://www.ubuntuforums.org/showthread.php?t=184201]("http://www.ubuntuforums.org/showthread.php?t=184201")

Take a look at that, and see if it helps.

Lloyd B.

---

### Post by platinummonkey on 2006-10-20
well, didnt quite work, but i had a pci ethernet card leftover and plugged it in to see if it would detect automatically and to my luck it did. now my only problem is actually connecting to the internet :P ill run those commands again, but i think my problem now is that loopback is still enabled, and i have no idea how to turn it off :P ill edit this post with the output of the commands.

-edit-
here is the output:

platinummonkey@platinummonkeydsk:~$
ifconfig
eth0 Link encap:Ethernet HWaddr 00:15:E9:F9:ED:F0
inet6 addr: fe80::215:e9ff:fef9:edf0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:385 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:57176 (55.8 KiB) TX bytes:468 (468.0 b)
Interrupt:201 Base address:0xb000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:237 errors:0 dropped:0 overruns:0 frame:0
TX packets:237 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:17548 (17.1 KiB) TX bytes:17548 (17.1 KiB)
platinummonkey@platinummonkeydsk:~$
iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
sit0 no wireless extensions.
platinummonkey@platinummonkeydsk:~$
iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
sit0 Interface doesn't support scanning.
platinummonkey@platinummonkeydsk:~$
sudo /etc/init.d/networking restart
Password:
* Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Listening on LPF/eth0/00:15:e9:f9:ed:f0
Sending on LPF/eth0/00:15:e9:f9:ed:f0
Sending on Socket/fallback
DHCPRELEASE on eth0 to 128.194.177.199 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Listening on LPF/eth0/00:15:e9:f9:ed:f0
Sending on LPF/eth0/00:15:e9:f9:ed:f0
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 20042005
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
[ ok ]
platinummonkey@platinummonkeydsk:~$
route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
platinummonkey@platinummonkeydsk:~$
sudo gedit /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
platinummonkey@platinummonkeydsk:~$
sudo lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2
RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM
memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory:
nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia
Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation
MCP2A ISA bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev
a1)
0000:00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
0000:00:0b.0 IDE interface: nVidia Corporation nForce2 Serial ATA Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
0000:02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [RhineIII]
(rev 86)
0000:02:0b.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 (rev 31)
platinummonkey@platinummonkeydsk:~$
sudo lshw
platinummonkeydsk
description: Desktop Computer
width: 32 bits
capabilities: smbios2.2
dmi2.2
configuration: boot=normal chassis=desktop uuid=0000000000000000000000508D7594A8
*core
description: Motherboard
product: NF7II series(Nvidia nForceMCP2S)
vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)
physical id: 0
version: v0.1
slot: PCI4
*firmware
description: BIOS
vendor: Phoenix Technologies, LTD
physical id: 0
version: 6.00 PG (04/07/2005)
size: 128KB
capacity: 448KB
capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd
int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard
int14serial int17printer int10video acpi usb agp ls120boot zipboot
*cpu
description: CPU
product: AMD Athlon(tm) XP 2600+
vendor: Advanced Micro Devices [AMD]
physical id: 4
bus info: cpu@0
version: 6.8.1
slot: Socket A
size: 2083MHz
capacity: 3GHz
width: 32 bits
clock: 166MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
*cache:
0
description: L1 cache
physical id: 9
slot: Internal Cache
size: 128KB
capacity: 128KB
capabilities: synchronous internal writeback
*cache:
1
description: L2 cache
physical id: a
slot: External Cache
size: 256KB
capacity: 256KB
capabilities: synchronous external writeback
*memory
description: System Memory
physical id: 1a
slot: System board or motherboard
size: 1536MB
capacity: 1536MB
*bank:
0
description: DIMM
physical id: 0
slot: A0
size: 512MB
*bank:
1
description: DIMM
physical id: 1
slot: A1
size: 512MB
*bank:
2
description: DIMM
physical id: 2
slot: A2
size: 512MB
*pci
description: Host bridge
product: nForce2 AGP (different version?)
vendor: nVidia Corporation
physical id: d0000000
bus info: pci@00:00.0
version: c1
width: 32 bits
clock: 66MHz
resources: iomemory:d0000000dfffffff
*memory:
0 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 1
vendor: nVidia Corporation
physical id: 0.1
bus info: pci@00:00.1
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
1 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 4
vendor: nVidia Corporation
physical id: 0.2
bus info: pci@00:00.2
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
2 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 3
vendor: nVidia Corporation
physical id: 0.3
bus info: pci@00:00.3
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
3 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 2
vendor: nVidia Corporation
physical id: 0.4
bus info: pci@00:00.4
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*memory:
4 UNCLAIMED
description: RAM memory
product: nForce2 Memory Controller 5
vendor: nVidia Corporation
physical id: 0.5
bus info: pci@00:00.5
version: c1
width: 32 bits
clock: 66MHz (15.1515ns)
*isa
UNCLAIMED
description: ISA bridge
product: MCP2A ISA bridge
vendor: nVidia Corporation
physical id: 1
bus info: pci@00:01.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: isa bus_master cap_list
*serial
description: SMBus
product: MCP2A SMBus
vendor: nVidia Corporation
physical id: 1.1
bus info: pci@00:01.1
version: a1
width: 32 bits
clock: 66MHz
capabilities: cap_list
configuration: driver=nForce2_smbus
resources: ioport:ec00ec1f
irq:5
*usb:
0
description: USB Controller
product: MCP2A USB Controller
vendor: nVidia Corporation
physical id: 2
bus info: pci@00:02.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master cap_list
configuration: driver=ohci_hcd
resources: iomemory:e2002000e2002fff
irq:185
*usbhost
product: OHCI Host Controller
vendor: Linux 2.6.1526386
ohci_hcd
physical id: 1
bus info: usb@1
logical name: usb1
version: 2.06
capabilities: usb1.10
configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
*usb:
0
description: Audio device
vendor: Logitech, Inc.
physical id: 1
bus info: usb@1:1
version: 1.00
capabilities: usb1.10
audiocontrol
configuration: driver=sndusbaudio
maxpower=100mA speed=12.0MB/s
*usb:
1
description: Keyboard
product: USB Gaming Keyboard Pro
vendor: Chicony
physical id: 4
bus info: usb@1:4
version: 1.20
capabilities: usb2.00
configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
*usb:
1
description: USB Controller
product: MCP2A USB Controller
vendor: nVidia Corporation
physical id: 2.1
bus info: pci@00:02.1
version: a1
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master cap_list
configuration: driver=ohci_hcd
resources: iomemory:e2003000e2003fff
irq:193
*usbhost
product: OHCI Host Controller
vendor: Linux 2.6.1526386
ohci_hcd
physical id: 1
bus info: usb@2
logical name: usb2
version: 2.06
capabilities: usb1.10
configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
*usb
UNCLAIMED
description: Generic USB device
product: Microsoft
vendor: Microsoft
physical id: 3
bus info: usb@2:3
version: 1.00
capabilities: usb2.00
configuration: maxpower=260mA speed=12.0MB/s
*usb:
2
description: USB Controller
product: MCP2A USB Controller
vendor: nVidia Corporation
physical id: 2.2
bus info: pci@00:02.2
version: a2
width: 32 bits
clock: 66MHz
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd
resources: iomemory:e2004000e20040ff
irq:185
*usbhost
product: EHCI Host Controller
vendor: Linux 2.6.1526386
ehci_hcd
physical id: 1
bus info: usb@3
logical name: usb3
version: 2.06
capabilities: usb2.00
configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
*multimedia
description: Multimedia audio controller
product: MCP2S AC'97 Audio Controller
vendor: nVidia Corporation
physical id: 6
bus info: pci@00:06.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: driver=Intel ICH
resources: ioport:d800d8ff
ioport:dc00dc7f
iomemory:e2005000e2005fff
irq:193
*pci:
0
description: PCI bridge
product: MCP2A PCI Bridge
vendor: nVidia Corporation
physical id: 8
bus info: pci@00:08.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: pci normal_decode bus_master
*network:
0
description: Ethernet interface
product: VT6105 [RhineIII]
vendor: VIA Technologies, Inc.
physical id: 6
bus info: pci@02:06.0
logical name: eth0
version: 86
serial: 00:15:e9:f9:ed:f0
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10btfd
100bt 100btfd
autonegociation
configuration: autonegociation=on broadcast=yes driver=viarhine
driverversion=1.2.02.6
duplex=half link=no multicast=yes port=MII speed=10MB/s resources: ioport:b000b0ff
iomemory:e0011000e00110ff
irq:201
*network:
1 UNCLAIMED
description: Ethernet controller
product: Sundance Technology Inc
vendor: Sundance Technology Inc
physical id: b
bus info: pci@02:0b.0
version: 31
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: ioport:b400b47f
iomemory:e0010000e00101ff
irq:201
*ide:
0
description: IDE interface
product: MCP2A IDE
vendor: nVidia Corporation
physical id: 9
bus info: pci@00:09.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: ide bus_master cap_list
configuration: driver=AMD_IDE
resources: ioport:f000f00f
*ide:
0
description: IDE Channel 0
physical id: 0
bus info: ide@0
logical name: ide0
clock: 66MHz
*disk
description: ATA Disk
product: SAMSUNG SP1604N
physical id: 0
bus info: ide@0.0
logical name: /dev/hda
version: TM10031
serial: S013J10YB42097
size: 149GB
capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
configuration: mode=udma5 smart=on
*volume:
0
description: Linux filesystem partition
physical id: 1
bus info: ide@0.0,1
logical name: /dev/hda1
capacity: 144GB
capabilities: primary bootable
*volume:
1
description: Extended partition
physical id: 2
bus info: ide@0.0,2
logical name: /dev/hda2
capacity: 4447MB
capabilities: extended partitioned partitioned:extended
*ide:
1
description: IDE Channel 1
physical id: 1
bus info: ide@1
logical name: ide1
clock: 66MHz
*cdrom
description: DVD writer
product: _NEC DVD_RW ND3500AG
physical id: 0
bus info: ide@1.0
logical name: /dev/hdc
version: 2.18
capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cdr
cdrw
dvd dvdr
configuration: mode=udma2
*disc
physical id: 0
logical name: /dev/hdc
*ide:
1
description: IDE interface
product: nForce2 Serial ATA Controller
vendor: nVidia Corporation
physical id: b
bus info: pci@00:0b.0
logical name: scsi0
logical name: scsi1
version: a3
width: 32 bits
clock: 66MHz
capabilities: ide bus_master cap_list scsihost
configuration: driver=sata_nv
resources: ioport:9f09f7
ioport:bf0bf3
ioport:970977
ioport:b70b73
ioport:cc00cc0f
ioport:d000d07f
irq:177
*pci:
1
description: PCI bridge
product: nForce2 AGP
vendor: nVidia Corporation
physical id: 1e
bus info: pci@00:1e.0
version: c1
width: 32 bits
clock: 66MHz
capabilities: pci normal_decode bus_master
*display:
0
description: VGA compatible controller
product: RV350 AR [Radeon 9600]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@01:00.0
version: 00
size: 256MB
width: 32 bits
clock: 66MHz
capabilities: vga bus_master cap_list
resources: iomemory:b0000000bfffffff
ioport:a000a0ff
iomemory:e1030000e103ffff
irq:209
*display:
1 UNCLAIMED
description: Display controller
product: RV350 AR [Radeon 9600] (Secondary)
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@01:00.1
version: 00
size: 256MB
width: 32 bits
clock: 66MHz
capabilities: cap_list
resources: iomemory:c0000000cfffffff
iomemory:e1020000e102ffff
platinummonkey@platinummonkeydsk:~$

ignore the sundance ethernet affixed to my motherboard, i have a d-link ethernet adapter in a pci slot, this is the one that it reckognizes and has assigned eth0 to.

---

### Post by Iowan on 2006-10-20
> **platinummonkey said:**
> ...but i think my problem now is that loopback is still enabled, and i have no idea how to turn it off 
That's a good thing - loopback (AKA lo) is needed by the system.
You can try searching for "No DHCPOFFERS received". Sounds like no DHCP server exists, card or cable is not communicating, wrong type cable, etc.  I find it odd that it'd get an IPV6 address, but no IPV4.  
Another option might be to disable IPV6 (I need to get back to what I'm actually being paid to do - or I'd post some "how-to disable IPv6" links).  You can search for "disable ipv6".

---

### Post by platinummonkey on 2006-10-20
ended up figuring it out. okay so the real problem was that my schools network wasnt allowing me to the registration site, bc according the the IT, i would have to bring the computer to them (which is a good 3/4 - 1 mile treck) so they can make an exception in their firewall.  
I do not know if this will help anyone, but this is how I did it:
Typing "ipconfig -all" in the command windows(Start>Run>"cmd") on my windows laptop copy down the ip, subnet, gateway, and dns server.
Then back to linux:
System>Administration>networking select eth0 or w/e yours is, and click 'properties', make sure the "enable this connection" box is checked; change to 'static ip' from the drop down menu; copy ip, subnet, and gateway addresses that you just wrote down, click 'ok'. Now click the "DNS" tab and click teh "add" button in the dns section and copy of the dns #'s that you had written down from your laptop, repeat until all the written #'s are copied by adding a new entry for each. Click "ok" and now try :P, worked for me the very first time, and i nearly made my roomate deaf screaming from joy :P

and thank you all so much who helped me! greatly appreciated!:D :D :D

---

