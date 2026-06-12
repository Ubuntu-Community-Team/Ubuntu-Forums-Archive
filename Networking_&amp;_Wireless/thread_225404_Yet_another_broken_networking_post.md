---
title: "Yet another broken networking post"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by blake7_uk on 2006-07-29
If I boot from the live cd, I can access the Internet, however after installing Dapper and booting from the hard disk, I can no longer access the Internet.  I have looked through some of the other posts, and frankly im still baffled.

gerry@gerry-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:60:6E:75:75:69
          inet addr:10.0.0.14  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::260:6eff:fe75:7569/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2064 (2.0 KiB)
          Interrupt:10 Base address:0xa400

gerry@gerry-desktop:~$ lspci | grep Eth
0000:00:0e.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)

gerry@gerry-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth0

gerry@gerry-desktop:~$ cat /etc/resolv.conf
nameserver 10.0.0.2

gerry@gerry-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.14
netmask 255.0.0.0
gateway 10.0.0.2

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


gerry@gerry-desktop:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


Windows IP Configuration

	Host Name					: madmonk-ft85uts
	Primary Dns Suffix			: 
	Node Type					: Unknown
	IP Routing Enabled			: No
	WINS Proxy Enabled			: No

Ethernet adapter Local Area Connection:

	Connection-specific DNS Suffix	:
	Description					: DAVICOM 9102-Based PCI Fast Ethernet Adapter
	Physical Address				: 00-60-6E-75-75-69
	Dhcp Enabled				: Yes
	Autoconfiguration Enabled		: Yes
	IP Address					: 10.0.0.14
	Subnet Mask					: 255.0.0.0
	Default Gateway				: 10.0.0.2
	DHCP Server					: 10.0.0.2
	DNS Servers					: 10.0.0.2
	Lease Obtained				: 29 July 2006 20:07:16
	Lease Expires				: 30 July 2006 20:07:16



gerry@gerry-desktop:~$ sudo dmesg
Password:
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
[4294667.296000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
[4294667.296000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 131052
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126956 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6b80
[4294667.296000] ACPI: RSDT (v001 ASUS   A7V-E    0x30303031 MSFT 0x31313031) @ 0x1ffec000
[4294667.296000] ACPI: FADT (v001 ASUS   A7V-E    0x30303031 MSFT 0x31313031) @ 0x1ffec080
[4294667.296000] ACPI: BOOT (v001 ASUS   A7V-E    0x30303031 MSFT 0x31313031) @ 0x1ffec040
[4294667.296000] ACPI: DSDT (v001   ASUS A7V-E    0x00001000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0xe408
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda4 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01402000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1312.251 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.496000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.499000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.529000] Memory: 508596k/524208k available (1976k kernel code, 15024k reserved, 606k data, 288k init, 0k highmem)
[4294670.529000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.589000] Calibrating delay using timer specific routine.. 2625.02 BogoMIPS (lpj=1312514)
[4294670.589000] Security Framework v1.0.0 initialized
[4294670.589000] SELinux:  Disabled at boot.
[4294670.589000] Mount-cache hash table entries: 512
[4294670.589000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294670.589000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294670.589000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294670.589000] CPU: L2 Cache: 256K (64 bytes/line)
[4294670.589000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000020 00000000 00000000 00000000
[4294670.589000] mtrr: v2.0 (20020519)
[4294670.589000] CPU: AMD Athlon(tm) Processor stepping 02
[4294670.589000] Enabling fast FPU save and restore... done.
[4294670.589000] Checking 'hlt' instruction... OK.
[4294670.593000] checking if image is initramfs... it is
[4294671.469000] Freeing initrd memory: 6834k freed
[4294671.492000] ACPI: Looking for DSDT ... not found!
[4294671.493000] ACPI: setting ELCR to 0200 (from 0e00)
[4294671.494000] NET: Registered protocol family 16
[4294671.494000] EISA bus registered
[4294671.494000] ACPI: bus type pci registered
[4294671.495000] PCI: PCI BIOS revision 2.10 entry at 0xf10e0, last bus=1
[4294671.495000] PCI: Using configuration type 1
[4294671.496000] ACPI: Subsystem revision 20051216
[4294671.500000] ACPI: Interpreter enabled
[4294671.500000] ACPI: Using PIC for interrupt routing
[4294671.501000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294671.501000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294671.501000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294671.501000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294671.503000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.503000] PCI: Probing PCI hardware (bus 00)
[4294671.503000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.505000] PCI quirk: region e200-e27f claimed by vt82c686 HW-mon
[4294671.505000] PCI quirk: region e800-e80f claimed by vt82c686 SMB
[4294671.505000] Boot video device is 0000:01:00.0
[4294671.505000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.530000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294671.537000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.537000] pnp: PnP ACPI init
[4294671.541000] pnp: PnP ACPI: found 12 devices
[4294671.541000] PnPBIOS: Disabled by ACPI PNP
[4294671.541000] PCI: Using ACPI for IRQ routing
[4294671.541000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.551000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[4294671.551000] pnp: 00:02: ioport range 0xe800-0xe80f has been reserved
[4294671.551000] pnp: 00:02: ioport range 0xe200-0xe27f has been reserved
[4294671.551000] PCI: Bridge: 0000:00:01.0
[4294671.551000]   IO window: disabled.
[4294671.551000]   MEM window: ee000000-efdfffff
[4294671.551000]   PREFETCH window: eff00000-fbffffff
[4294671.551000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.551000] Simple Boot Flag at 0x3a set to 0x1
[4294671.552000] audit: initializing netlink socket (disabled)
[4294671.552000] audit(1154202367.551:1): initialized
[4294671.552000] VFS: Disk quotas dquot_6.5.1
[4294671.552000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.552000] Initializing Cryptographic API
[4294671.552000] io scheduler noop registered
[4294671.552000] io scheduler anticipatory registered
[4294671.552000] io scheduler deadline registered
[4294671.552000] io scheduler cfq registered
[4294671.552000] Applying VIA southbridge workaround.
[4294671.552000] PCI: Disabling Via external APIC routing
[4294671.552000] isapnp: Scanning for PnP cards...
[4294671.910000] isapnp: No Plug & Play device found
[4294671.928000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[4294671.928000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[4294671.931000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.932000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.932000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.932000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.932000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.934000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.935000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.935000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.935000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.935000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.936000] mice: PS/2 mouse device common for all mice
[4294671.936000] EISA: Probing bus 0 at eisa.0
[4294671.936000] EISA: Detected 0 cards.
[4294671.936000] NET: Registered protocol family 2
[4294671.945000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)[4294671.945000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.945000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.946000] TCP: Hash tables configured (established 32768 bind 32768)
[4294671.946000] TCP reno registered
[4294671.946000] TCP bic registered
[4294671.946000] NET: Registered protocol family 1
[4294671.946000] NET: Registered protocol family 8
[4294671.946000] NET: Registered protocol family 20
[4294671.946000] Using IPI Shortcut mode
[4294671.946000] ACPI wakeup devices:
[4294671.946000] PCI0 PCI1 UAR1 UAR2 USB0 USB1 AC97
[4294671.946000] ACPI: (supports S0 S1 S4 S5)
[4294671.947000] Freeing unused kernel memory: 288k freed
[4294671.975000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.039000] vga16fb: initializing
[4294672.039000] vga16fb: mapped to 0xc00a0000
[4294672.170000] Console: switching to colour frame buffer device 80x25
[4294672.170000] fb0: VGA16 VGA frame buffer device
[4294673.333000] Capability LSM initialized
[4294673.385000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294673.385000] ACPI: Processor [CPU0] (supports 16 throttling states)
[4294674.211000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[4294674.211000] VP_IDE: chipset revision 6
[4294674.211000] VP_IDE: not 100% native mode: will probe irqs later
[4294674.211000] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[4294674.211000]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
[4294674.211000]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:DMA
[4294674.211000] Probing IDE interface ide0...
[4294674.597000] hda: SAMSUNG SP0802N, ATA DISK drive
[4294674.852000] hdb: Conner Technology CT210, ATA DISK drive
[4294674.903000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.927000] Probing IDE interface ide1...
[4294675.721000] hdc: Compaq DVD-ROM DVD-114 0114, ATAPI CD/DVD-ROM drive
[4294676.435000] hdd: YAMAHA CRW8824E, ATAPI CD/DVD-ROM drive
[4294676.487000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.503000] hda: max request size: 1024KiB
[4294676.530000] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294676.530000] hda: cache flushes supported
[4294676.531000]  hda: hda1 hda2 hda3 < hda5 > hda4
[4294676.556000] hdb: max request size: 128KiB
[4294676.556000] hdb: 20040450 sectors (10260 MB) w/512KiB Cache, CHS=19881/16/63, UDMA(66)
[4294676.556000] hdb: cache flushes not supported
[4294676.556000]  hdb:<6>hdc: ATAPI DVD-ROM drive, 512kB Cache, UDMA(33)
[4294676.556000] Uniform CD-ROM driver Revision: 3.20
[4294676.561000]  hdb1
[4294676.561000] hdd: ATAPI 16X CD-ROM CD-R/RW drive, 4096kB Cache, DMA
[4294678.646000] usbcore: registered new driver usbfs
[4294678.647000] usbcore: registered new driver hub
[4294678.650000] USB Universal Host Controller Interface driver v2.3
[4294678.650000] **** SET: Misaligned resource pointer: dfb79e02 Type 07 Len 0
[4294678.651000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294678.651000] PCI: setting IRQ 9 as level-triggered
[4294678.651000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294678.651000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[4294678.651000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294678.651000] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000d400
[4294678.652000] hub 1-0:1.0: USB hub found
[4294678.652000] hub 1-0:1.0: 2 ports detected
[4294678.753000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294678.753000] uhci_hcd 0000:00:07.3: UHCI Host Controller
[4294678.753000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[4294678.753000] uhci_hcd 0000:00:07.3: irq 9, io base 0x0000d000
[4294678.753000] hub 2-0:1.0: USB hub found
[4294678.753000] hub 2-0:1.0: 2 ports detected
[4294678.959000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294679.029000] Attempting manual resume
[4294679.059000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.072000] kjournald starting.  Commit interval 5 seconds
[4294679.081000] hub 1-1:1.0: USB hub found
[4294679.083000] hub 1-1:1.0: 4 ports detected
[4294679.680000] usb 1-1.3: new low speed USB device using uhci_hcd and address 3
[4294691.268000] parport_pc: VIA 686A/8231 detected
[4294691.268000] parport_pc: probing current configuration
[4294691.268000] parport_pc: Current parallel port base: 0x378
[4294691.268000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294691.323000] parport0: Printer, EPSON Stylus COLOR 880
[4294691.323000] parport_pc: VIA parallel port: io=0x378, irq=7
[4294691.437000] Linux agpgart interface v0.101 (c) Dave Jones
[4294691.450000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[4294691.453000] agpgart: AGP aperture is 32M @ 0xfc000000
[4294691.461000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.465000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.684000] **** SET: Misaligned resource pointer: df918722 Type 07 Len 0
[4294691.685000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[4294691.685000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[4294691.685000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[4294692.011000] Real Time Clock Driver v1.12
[4294692.476000] nvidia: module license 'NVIDIA' taints kernel.
[4294692.509000] **** SET: Misaligned resource pointer: da22b9a2 Type 07 Len 0
[4294692.510000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294692.510000] PCI: setting IRQ 11 as level-triggered
[4294692.510000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294692.511000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294692.540000] Linux Tulip driver version 1.1.13 (December 15, 2004)
[4294692.540000] **** SET: Misaligned resource pointer: da831ee2 Type 07 Len 0
[4294692.541000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294692.541000] PCI: setting IRQ 10 as level-triggered
[4294692.541000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294692.557000] tulip0:  MII transceiver #1 config 3100 status 7829 advertising 01e1.
[4294692.561000] eth0: Davicom DM9102/DM9102A rev 64 at 0001a400, 00:60:6E:75:75:69, IRQ 10.
[4294692.572000] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[4294693.561000] Floppy drive(s): fd0 is 1.44M
[4294693.572000] input: PC Speaker as /class/input/input1
[4294693.629000] usbcore: registered new driver hiddev
[4294693.658000] input: Microsoft Microsoft IntelliMouseï¿½ Optical as /class/input/input2
[4294693.658000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouseï¿½ Optical] on usb-0000:00:07.2-1.3
[4294693.658000] usbcore: registered new driver usbhid
[4294693.658000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294693.710000] FDC 0 is a post-1991 82077
[4294693.715000] ts: Compaq touchscreen protocol output
[4294694.261000] lp0: using parport0 (interrupt-driven).
[4294694.352000] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1 across:1510068k
[4294694.497000] EXT3 FS on hda4, internal journal
[4294694.719000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.719000] md: bitmap version 4.39
[4294695.286000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294695.683000] cdrom: open failed.
[4294696.194000] cdrom: open failed.
[4294696.199000] cdrom: open failed.
[4294705.980000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294706.049000] NTFS volume version 3.1.
[4294706.077000] kjournald starting.  Commit interval 5 seconds
[4294706.077000] EXT3 FS on hda2, internal journal
[4294706.077000] EXT3-fs: mounted filesystem with ordered data mode.
[4294707.979000] NET: Registered protocol family 17
[4294713.283000] ACPI: Power Button (FF) [PWRF]
[4294713.283000] ACPI: Power Button (CM) [PWRB]
[4294713.451000] ibm_acpi: ec object not found
[4294713.486000] pcc_acpi: loading...
[4294714.155000] powernow: No powernow capabilities detected
[4294719.215000] ppdev: user-space parallel port driver
[4294719.542000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294719.542000] apm: overridden by ACPI.
[4294725.854000] Bluetooth: Core ver 2.8
[4294725.854000] NET: Registered protocol family 31
[4294725.854000] Bluetooth: HCI device and connection manager initialized
[4294725.854000] Bluetooth: HCI socket layer initialized
[4294725.905000] Bluetooth: L2CAP ver 2.8
[4294725.905000] Bluetooth: L2CAP socket layer initialized
[4294725.942000] Bluetooth: RFCOMM socket layer initialized
[4294725.942000] Bluetooth: RFCOMM TTY layer initialized
[4294725.942000] Bluetooth: RFCOMM ver 1.7
[4294734.656000] NET: Registered protocol family 10
[4294734.656000] lo: Disabled Privacy Extensions
[4294734.656000] IPv6 over IPv4 tunneling driver
[4294745.600000] eth0: no IPv6 routers present


Anybody any ideas, it was all working fine in Breezy

Gerry

---

### Post by nstenz on 2006-08-30
If you haven't fixed this yet, I'm almost positive the problem is Ubuntu loading the wrong driver for your network card. Search the forums for tulip driver blacklist ... I think the offending driver is called dmfe or something similar.

---

