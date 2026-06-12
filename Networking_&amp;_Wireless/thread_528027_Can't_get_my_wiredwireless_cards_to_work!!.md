---
title: "Can't get my wired/wireless cards to work!!"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by Salatino on 2007-08-17
Hi. I'm _NEW_ to the linux world and just installed Ubuntu 7.04 on my Toshiba laptop along with Windows XP. I have the following cards in my machine:
- Marvell 88E8053 PCI-E Gigabit Ethernet Controller
- Intel PRO/Wireless 2200BG Network Connection

My machine is connected to a linksys DSL router but doesn't seem to get an IP address (i assume cuz i can't browse the internet). The network Settings shows "Wired connection" and "Modem connection" but no wirless connections!

When I tried the "lshw -C network" command, it listed my Marvell card and its logical name as eth0 and my Intel wirless card was also listed but with no logical name and "network UNCLAIMED" in its header!!

Any help is highly appreciated and remember that i'm completely new to Linux.

Thanx

---

### Post by noob12 on 2007-08-17
OK. UNCLAIMED means that no driver has claimed the device.  The ipw2200 driver shipped in 7.04 should be trying to claim it, so we need to understand why it didn't.

Please post these.
```

lspci -nn

sudo lshw -C network

```

Then do this.  It tells the driver to reload, and also to spit out some debugging info to
the kernel log.
```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw2200
sudo modprobe ipw2200 debug=15
sudo /etc/init.d/networking start

```

*Following that*, post the full output of

```

dmesg

```

We hope this will give us a better idea of why the driver failed to load at the initial boot as well as what happened on that last reload attempt.

---

### Post by Salatino on 2007-08-17
Now this is really funny!

I'm writing from my desktop machine and Ubuntu is installed in my laptop (which has no internet connection yet!) and I did all what you asked me to do and saved all the results in a text file but cannot copy this file to my desktop machine through my USB hard drive cuz it says "you do not have permissions to write to this folder"!!

How can I post the results??!!

---

### Post by thevictor390 on 2007-08-17
right-click on folder -> permissions tab -> make sure you have read and write permissions.

I had the same problem with mu USB drive.  The other way is to go through command-line and use "sudo," but that's unnecessarily difficult.

---

### Post by Salatino on 2007-08-24
Oh it's because my USB drive formatted as NTFS!

I'll convert it to FAT32 and continue with the instructions.

---

### Post by noob12 on 2007-08-31
I'm no longer watching this thread.  PM me if you want attention.

---

### Post by tankertux on 2008-02-16
I have the same problem noted above.  I've posted the output that you needed.

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 01)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 01)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 01)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
01:0a.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
01:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)
```

sudo lshw -C network
```
  *-network:0             
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:9c:4a:33
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.136 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:cffff000-cfffffff ioport:cf40-cf7f irq:11
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: a
       bus info: pci@01:0a.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
       resources: iomemory:ceffe000-ceffefff irq:11

```

and the output of dmesg after running your posted commands:
```
jordan@Grant-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 000000000000ee00 end: 00000000000eee00 type: 2
[    0.000000] copy_e820_map() start: 00000000000eee00 size: 0000000000000200 end: 00000000000ef000 type: 4
[    0.000000] copy_e820_map() start: 00000000000ef000 size: 0000000000011000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001ee40000 end: 000000001ef40000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ef40000 size: 0000000000010000 end: 000000001ef50000 type: 3
[    0.000000] copy_e820_map() start: 000000001ef50000 size: 00000000000b0000 end: 000000001f000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec10000 size: 0000000000010000 end: 00000000fec20000 type: 2
[    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000020000 end: 00000000fedc0000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ef40000 (usable)
[    0.000000]  BIOS-e820: 000000001ef40000 - 000000001ef50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ef50000 - 000000001f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 126784) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126784
[    0.000000]   HighMem    126784 ->   126784
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126784
[    0.000000] On node 0 totalpages: 126784
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 958 pages used for memmap
[    0.000000]   Normal zone: 121730 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f0180
[    0.000000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ef40000
[    0.000000] ACPI: FADT (v002 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ef40058
[    0.000000] ACPI: DBGP (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ef400dc
[    0.000000] ACPI: BOOT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ef40030
[    0.000000] ACPI: DSDT (v001 TOSHIB AFCF7    0x20030326 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f000000:dfc10000)
[    0.000000] Detected 1995.111 MHz processor.
[  748.885112] Built 1 zonelists.  Total pages: 125794
[  748.885118] Kernel command line: root=UUID=77d103fd-6d1b-4716-8d54-43c9d1d51387 ro quiet splash
[  748.885326] Local APIC disabled by BIOS -- you can enable it with "lapic"
[  748.885336] mapped APIC to ffffd000 (013eb000)
[  748.885340] Enabling fast FPU save and restore... done.
[  748.885344] Enabling unmasked SIMD FPU exception support... done.
[  748.885355] Initializing CPU#0
[  748.885442] PID hash table entries: 2048 (order: 11, 8192 bytes)
[  748.887370] Console: colour VGA+ 80x25
[  748.887721] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  748.888082] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  748.906106] Memory: 491456k/507136k available (1992k kernel code, 15076k reserved, 893k data, 328k init, 0k highmem)
[  748.906120] virtual kernel memory layout:
[  748.906121]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[  748.906123]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  748.906124]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[  748.906126]     lowmem  : 0xc0000000 - 0xdef40000   ( 495 MB)
[  748.906127]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[  748.906128]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[  748.906130]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[  748.906134] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  748.985398] Calibrating delay using timer specific routine.. 3993.71 BogoMIPS (lpj=7987435)
[  748.985458] Security Framework v1.0.0 initialized
[  748.985467] SELinux:  Disabled at boot.
[  748.985490] Mount-cache hash table entries: 512
[  748.985694] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[  748.985711] CPU: Trace cache: 12K uops, L1 D cache: 8K
[  748.985715] CPU: L2 cache: 256K
[  748.985718] CPU: Hyper-Threading is disabled
[  748.985721] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00003080 00004400 00000000 00000000
[  748.985738] Compat vDSO mapped to ffffe000.
[  748.985743] Remapping vsyscall page to ffffe000
[  748.985761] Checking 'hlt' instruction... OK.
[  749.001524] SMP alternatives: switching to UP code
[  749.001844] Freeing SMP alternatives: 11k freed
[  749.002144] Early unpacking initramfs... done
[  749.404280] ACPI: Core revision 20060707
[  749.404462] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[  749.406707] ACPI: setting ELCR to 0200 (from 0e00)
[  749.406870] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.00GHz stepping 07
[  749.406879] SMP motherboard not detected.
[  749.406882] Local APIC not detected. Using dummy APIC emulation.
[  749.406937] Brought up 1 CPUs
[  749.407293] Booting paravirtualized kernel on bare hardware
[  749.407404] Time: 15:21:34  Date: 01/16/108
[  749.407448] NET: Registered protocol family 16
[  749.407605] EISA bus registered
[  749.407615] ACPI: bus type pci registered
[  749.407737] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
[  749.407740] PCI: Using configuration type 1
[  749.407742] Setting up standard PCI resources
[  749.412297] ACPI: Interpreter enabled
[  749.412304] ACPI: Using PIC for interrupt routing
[  749.413261] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[  749.413710] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[  749.414230] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[  749.414664] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[  749.415183] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[  749.415630] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[  749.416148] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[  749.416581] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[  749.416844] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  749.416852] PCI: Probing PCI hardware (bus 00)
[  749.417637] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[  749.417923] Boot video device is 0000:00:02.0
[  749.418302] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[  749.418307] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[  749.418585] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[  749.418752] PCI: Transparent bridge - 0000:00:1e.0
[  749.418869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  749.421003] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[  749.426314] ACPI: Power Resource [PFAN] (off)
[  749.426483] Linux Plug and Play Support v0.97 (c) Adam Belay
[  749.426501] pnp: PnP ACPI init
[  749.430650] pnp: PnP ACPI: found 10 devices
[  749.430659] PnPBIOS: Disabled by ACPI PNP
[  749.430745] PCI: Using ACPI for IRQ routing
[  749.430751] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  749.430776] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[  749.435972] NET: Registered protocol family 8
[  749.435976] NET: Registered protocol family 20
[  749.437578] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[  749.437626] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
[  749.437629]   IO window: 0000c000-0000c0ff
[  749.437634]   IO window: 0000c400-0000c4ff
[  749.437640]   PREFETCH window: 28000000-2bffffff
[  749.437646]   MEM window: 30000000-33ffffff
[  749.437652] PCI: Bridge: 0000:00:1e.0
[  749.437655]   IO window: c000-cfff
[  749.437662]   MEM window: cef00000-cfffffff
[  749.437668]   PREFETCH window: 28000000-2bffffff
[  749.437685] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  749.437705] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
[  749.438040] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[  749.438045] PCI: setting IRQ 11 as level-triggered
[  749.438049] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[  749.438097] NET: Registered protocol family 2
[  749.477260] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  749.477380] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[  749.477480] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[  749.477538] TCP: Hash tables configured (established 16384 bind 8192)
[  749.477541] TCP reno registered
[  749.489358] checking if image is initramfs... it is
[  750.272822] Freeing initrd memory: 7011k freed
[  750.273139] Simple Boot Flag at 0x7c set to 0x1
[  750.273437] audit: initializing netlink socket (disabled)
[  750.273457] audit(1203175294.572:1): initialized
[  750.273672] VFS: Disk quotas dquot_6.5.1
[  750.273701] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  750.273768] io scheduler noop registered
[  750.273772] io scheduler anticipatory registered
[  750.273776] io scheduler deadline registered
[  750.273788] io scheduler cfq registered (default)
[  750.274197] isapnp: Scanning for PnP cards...
[  750.627156] isapnp: No Plug & Play device found
[  750.710484] Real Time Clock Driver v1.12ac
[  750.710567] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  750.712316] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[  750.712688] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[  750.712694] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[  750.712705] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[  750.712880] mice: PS/2 mouse device common for all mice
[  750.713833] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  750.714245] input: Macintosh mouse button emulation as /class/input/input0
[  750.714313] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  750.714320] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  750.714601] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[  750.732644] serio: i8042 KBD port at 0x60,0x64 irq 1
[  750.732654] serio: i8042 AUX port at 0x60,0x64 irq 12
[  750.733035] EISA: Probing bus 0 at eisa.0
[  750.733044] Cannot allocate resource for EISA slot 1
[  750.733064] EISA: Detected 0 cards.
[  750.763191] TCP cubic registered
[  750.763202] NET: Registered protocol family 1
[  750.763235] Using IPI No-Shortcut mode
[  750.763363] ACPI: (supports S0 S3 S4 S5)
[  750.763426]   Magic number: 12:589:386
[  750.764055] Freeing unused kernel memory: 328k freed
[  750.764522] Time: tsc clocksource has been installed.
[  750.781858] input: AT Translated Set 2 keyboard as /class/input/input1
[  752.123064] Capability LSM initialized
[  752.184920] ACPI: Transitioning device [FAN] to D3
[  752.184927] ACPI: Transitioning device [FAN] to D3
[  752.184932] ACPI: Fan [FAN] (off)
[  752.191212] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[  752.192773] ACPI: Thermal Zone [THRM] (60 C)
[  753.090535] SCSI subsystem initialized
[  753.097906] libata version 2.20 loaded.
[  753.131588] ata_piix 0000:00:1f.1: version 2.10ac1
[  753.131954] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[  753.131959] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  753.131983] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  753.132080] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[  753.132123] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[  753.132160] scsi0 : ata_piix
[  753.152578] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[  753.152584] e100: Copyright(c) 1999-2006 Intel Corporation
[  753.180095] usbcore: registered new interface driver usbfs
[  753.180136] usbcore: registered new interface driver hub
[  753.180178] usbcore: registered new device driver usb
[  753.202797] USB Universal Host Controller Interface driver v3.0
[  753.295812] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[  753.295820] ata1.00: ATA-6: CSD CAT040H, , max UDMA/100
[  753.295823] ata1.00: 78140160 sectors, multi 16: LBA 
[  753.303767] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[  753.303775] ata1.00: configured for UDMA/100
[  753.303794] scsi1 : ata_piix
[    4.516000] Time: acpi_pm clocksource has been installed.
[    4.804000] ata2.00: ATAPI, max UDMA/33
[    4.984000] ata2.00: configured for UDMA/33
[    4.984000] scsi 0:0:0:0: Direct-Access     ATA      CSD CAT040H      n/a  PQ: 0 ANSI: 5
[    4.988000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1333 PQ: 0 ANSI: 5
[    4.996000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    4.996000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[    5.016000] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:9C:4A:33
[    5.020000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    5.020000] PCI: setting IRQ 10 as level-triggered
[    5.020000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    5.020000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    5.020000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.020000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.020000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
[    5.020000] usb usb1: configuration #1 chosen from 1 choice
[    5.020000] hub 1-0:1.0: USB hub found
[    5.020000] hub 1-0:1.0: 2 ports detected
[    5.048000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[    5.052000] sda: Write Protect is off
[    5.052000] sda: Mode Sense: 00 3a 00 00
[    5.052000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.052000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[    5.052000] sda: Write Protect is off
[    5.052000] sda: Mode Sense: 00 3a 00 00
[    5.052000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.052000]  sda:PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[    5.124000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    5.124000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    5.124000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.124000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.124000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.124000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.124000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    5.124000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x2c080000
[    5.128000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.128000] usb usb2: configuration #1 chosen from 1 choice
[    5.128000] hub 2-0:1.0: USB hub found
[    5.128000] hub 2-0:1.0: 6 ports detected
[    5.128000]  sda1 sda2 < sda5 >
[    5.160000] sd 0:0:0:0: Attached scsi disk sda
[    5.168000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.168000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.224000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.224000] Uniform CD-ROM driver Revision: 3.20
[    5.224000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.412000] Attempting manual resume
[    5.412000] swsusp: Resume From Partition 8:5
[    5.412000] PM: Checking swsusp image.
[    5.412000] PM: Resume from disk failed.
[    5.464000] kjournald starting.  Commit interval 5 seconds
[    5.464000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.312000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   17.736000] NET: Registered protocol family 17
[   18.724000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.732000] agpgart: Detected an Intel 855 Chipset.
[   18.732000] agpgart: Detected 16252K stolen memory.
[   18.744000] agpgart: AGP aperture is 128M @ 0xd8000000
[   18.960000] intel_rng: FWH not detected
[   18.976000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.980000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.032000] input: PC Speaker as /class/input/input2
[   19.060000] iTCO_vendor_support: vendor-support=0
[   19.060000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   19.332000] pnp: Device 00:09 activated.
[   19.332000] parport: PnPBIOS parport detected.
[   19.332000] pnp: Device 00:09 disabled.
[   19.480000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
[   19.564000] input: PS/2 Mouse as /class/input/input3
[   19.608000] ieee80211_crypt: registered algorithm 'NULL'
[   19.616000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   19.624000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x5860)
[   19.624000] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
[   19.624000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.632000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.632000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.652000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   19.652000] Socket status: 30000007
[   19.652000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   19.652000] cs: IO port probe 0xc000-0xcfff: clean.
[   19.652000] pcmcia: parent PCI bridge Memory window: 0xcef00000 - 0xcfffffff
[   19.652000] pcmcia: parent PCI bridge Memory window: 0x28000000 - 0x2bffffff
[   19.700000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   19.700000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.700000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   19.700000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   20.064000] ipw2200: Unable to load ucode: -22
[   20.064000] ipw2200: Unable to load firmware: -22
[   20.064000] ipw2200: failed to register network device
[   20.064000] ACPI: PCI interrupt for device 0000:01:0a.0 disabled
[   20.064000] ipw2200: probe of 0000:01:0a.0 failed with error -5
[   20.100000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[   20.104000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.104000] cs: IO port probe 0x820-0x8ff: clean.
[   20.104000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.104000] cs: IO port probe 0xa00-0xaff: clean.
[   20.152000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
[   20.152000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   20.152000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   20.972000] intel8x0_measure_ac97_clock: measured 55221 usecs
[   20.972000] intel8x0: clocking to 48000
[   21.184000] fuse init (API version 7.8)
[   21.228000] lp: driver loaded but no devices found
[   21.276000] Adding 1461872k swap on /dev/disk/by-uuid/0ef8b3ec-7cea-4648-a194-2363907b4d14.  Priority:-1 extents:1 across:1461872k
[   21.432000] EXT3 FS on sda1, internal journal
[   21.660000] NET: Registered protocol family 10
[   21.660000] lo: Disabled Privacy Extensions
[   27.524000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   27.524000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   27.528000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   27.528000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   27.552000] ACPI: Battery Slot [BAT1] (battery present)
[   27.572000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   27.600000] ACPI: AC Adapter [ADP1] (on-line)
[   27.632000] ibm_acpi: ec object not found
[   27.740000] Using specific hotkey driver
[   27.820000] input: Power Button (FF) as /class/input/input5
[   27.828000] ACPI: Power Button (FF) [PWRF]
[   27.876000] input: Lid Switch as /class/input/input6
[   27.880000] ACPI: Lid Switch [LID]
[   27.928000] input: Power Button (CM) as /class/input/input7
[   27.932000] ACPI: Power Button (CM) [PWRB]
[   27.956000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   28.000000] No dock devices found.
[   28.016000] pcc_acpi: loading...
[   33.600000] [drm] Initialized drm 1.1.0 20060810
[   33.608000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   33.612000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   33.612000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[   33.616000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   34.416000] ppdev: user-space parallel port driver
[   35.328000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   35.328000] apm: overridden by ACPI.
[   35.568000] Bluetooth: Core ver 2.11
[   35.572000] NET: Registered protocol family 31
[   35.572000] Bluetooth: HCI device and connection manager initialized
[   35.572000] Bluetooth: HCI socket layer initialized
[   35.620000] Bluetooth: L2CAP ver 2.8
[   35.620000] Bluetooth: L2CAP socket layer initialized
[   35.644000] Bluetooth: RFCOMM socket layer initialized
[   35.644000] Bluetooth: RFCOMM TTY layer initialized
[   35.644000] Bluetooth: RFCOMM ver 1.8
[   49.088000] eth0: no IPv6 routers present
[  208.312000] e100: eth0: e100_watchdog: link down
[  218.312000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  218.312000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  235.668000] eth0: no IPv6 routers present
[  764.312000] e100: eth0: e100_watchdog: link down
[  770.312000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  770.312000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  788.568000] eth0: no IPv6 routers present
[ 1254.024000] ieee80211_crypt: unregistered algorithm 'NULL'
[ 1254.060000] ieee80211_crypt: registered algorithm 'NULL'
[ 1254.064000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 1254.064000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 1254.068000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[ 1254.068000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 1254.068000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 1254.068000] ipw2200: U ipw_pci_probe pci_resource_len = 0x00001000
[ 1254.068000] ipw2200: U ipw_pci_probe pci_resource_base = dfcb0000
[ 1254.072000] ipw2200: U ipw_sw_reset Hardware crypto [off]
[ 1254.072000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 1254.100000] ipw2200: U ipw_get_fw Read firmware 'ipw2200-bss.fw' image v3.0 (191126 bytes)
[ 1254.112000] ipw2200: U ipw_load initial device response after 0ms
[ 1254.112000] ipw2200: U ipw_stop_master stop master 0ms
[ 1254.132000] ipw2200: U ipw_load_ucode Microcode is not alive
[ 1254.132000] ipw2200: Unable to load ucode: -22
[ 1254.132000] ipw2200: Unable to load firmware: -22
[ 1254.136000] ipw2200: failed to register network device
[ 1254.136000] ACPI: PCI interrupt for device 0000:01:0a.0 disabled
[ 1254.136000] ipw2200: probe of 0000:01:0a.0 failed with error -5
[ 1268.100000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1268.104000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1268.104000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1286.568000] eth0: no IPv6 routers present

```

Any suggestions for getting my IPW2200BG working?

---

### Post by Count Doofus on 2008-02-16
Here is the link for the linux driver for the intel 2200bg wireless chipset


[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=1637&DwnldID=11780&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=1637&DwnldID=11780&strOSs=39&OSFullName=Linux*&lang=eng)

Good Luck

---

### Post by tankertux on 2008-02-16
I guess UNCLAIMED means that no driver has "claimed" the device.  Any tips on installation of the driver and associating it to the device?

(I'm a linux/ubuntu noob)

---

### Post by Hightide on 2008-02-16
Hi TankerTux

---

### Post by Hightide on 2008-02-16
Hi TankerTux

yes its mean's there is a driver problem

I notice you device is PRO/Wireless 2200BG Network Connection (ipw2200)

This [thread]("http://ubuntuforums.org/showthread.php?t=683043&highlight=PRO%2FWireless+2200BG") may help.

regards
:)

---

