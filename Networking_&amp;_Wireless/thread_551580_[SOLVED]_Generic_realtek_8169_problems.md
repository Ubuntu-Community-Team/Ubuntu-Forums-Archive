---
title: "[SOLVED] Generic realtek 8169 problems"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by deebo32 on 2007-09-15
dmesg:
[   48.250428] r8169 Gigabit Ethernet driver 2.2LK loaded 
[   48.250569] eth1: RTL8169sb/8110sb at 0xe0852000, 00:e0:4c:69:7b:33, IRQ 18

trying to bring it up:
root@sb32:~# ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

Been searching the forums but no applicable solutions found. rmmod+modprobe does nothing, it works but it wont work at the same time :)

any help appreciated

---

### Post by noob12 on 2007-09-16
Can you please post the output of the following after a boot.
```

sudo lshw -C network

ifconfig -a

cat /etc/iftab

```

You gave us a **dmesg** snippet, but can you post the whole thing?

---

### Post by deebo32 on 2007-09-17
lshw -C network:

  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@00:0c.0
       logical name: eth0
       version: 10
       serial: 00:06:4f:0a:2a:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.10 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:bc00-bcff iomemory:df001000-df0010ff irq:16
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@00:0d.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:c000-c0ff iomemory:df002000-df0020ff irq:17

ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:06:4F:0A:2A:43
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe0a:2a43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27587356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22561982 errors:0 dropped:0 overruns:11 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:583195474 (556.1 MiB)  TX bytes:2173950583 (2.0 GiB)
          Interrupt:16 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:664 (664.0 b)  TX bytes:664 (664.0 b)

/etc/iftab

eth0 mac 00:06:4f:0a:2a:43 arp 1
eth1 mac 00:06:4f:0a:2a:42 arp 1


and to clarify, eth0 is a "spare" im using to actually get the machine networked, eth1 is the card that wont work

---

### Post by noob12 on 2007-09-17
The big UNCLAIMED here means that the driver hasn't claimed the device.  It probably had some error while trying to claim it.   

```

*-network:1 UNCLAIMED
description: Ethernet controller
product: RTL-8169 Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: d
bus info: pci@00:0d.0
version: 10
width: 32 bits
clock: 66MHz
capabilities: cap_list
configuration: latency=32 maxlatency=64 mingnt=32
resources: ioport:c000-c0ff iomemory:df002000-df0020ff irq:17

```

Posting the full output of ```
dmesg
``` may help suggest the cause.

---

### Post by deebo32 on 2007-09-18
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f66c0
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f80c0
[    0.000000] ACPI: RSDT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[    0.000000] ACPI: MADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff5880
[    0.000000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:6 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Detected 1527.235 MHz processor.
[   43.762557] Built 1 zonelists.  Total pages: 130033
[   43.762562] Kernel command line: root=UUID=cac9ef11-89ab-4c78-bd79-bc3deb628085 ro quiet splash
[   43.762783] mapped APIC to ffffd000 (fee00000)
[   43.762787] mapped IOAPIC to ffffc000 (fec00000)
[   43.762791] Enabling fast FPU save and restore... done.
[   43.762795] Enabling unmasked SIMD FPU exception support... done.
[   43.762813] Initializing CPU#0
[   43.762923] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   43.764149] Console: colour VGA+ 80x25
[   43.764838] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   43.765301] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   43.787112] Memory: 508600k/524224k available (1993k kernel code, 15088k reserved, 900k data, 328k init, 0k highmem)
[   43.787127] virtual kernel memory layout:
[   43.787128]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   43.787130]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   43.787131]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   43.787133]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   43.787135]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   43.787136]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   43.787138]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   43.787142] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   43.866858] Calibrating delay using timer specific routine.. 3057.74 BogoMIPS (lpj=6115489)
[   43.866924] Security Framework v1.0.0 initialized
[   43.866935] SELinux:  Disabled at boot.
[   43.866959] Mount-cache hash table entries: 512
[   43.867183] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   43.867196] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   43.867199] CPU: L2 Cache: 256K (64 bytes/line)
[   43.867204] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   43.867222] Compat vDSO mapped to ffffe000.
[   43.867230] Remapping vsyscall page to ffffe000
[   43.867244] Checking 'hlt' instruction... OK.
[   43.883035] SMP alternatives: switching to UP code
[   43.883438] Freeing SMP alternatives: 11k freed
[   43.883826] Early unpacking initramfs... done
[   44.271795] ACPI: Core revision 20060707
[   44.278713] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   44.281513] CPU0: AMD Athlon(tm) XP 1800+ stepping 02
[   44.281545] Total of 1 processors activated (3057.74 BogoMIPS).
[   44.282311] ENABLING IO-APIC IRQs
[   44.282662] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   44.426562] Brought up 1 CPUs
[   44.426986] Booting paravirtualized kernel on bare hardware
[   44.427104] Time: 20:15:55  Date: 08/15/107
[   44.427160] NET: Registered protocol family 16
[   44.427325] EISA bus registered
[   44.427332] ACPI: bus type pci registered
[   44.459763] PCI: PCI BIOS revision 2.10 entry at 0xfb590, last bus=1
[   44.459766] PCI: Using configuration type 1
[   44.459769] Setting up standard PCI resources
[   44.473664] ACPI: Interpreter enabled
[   44.473671] ACPI: Using IOAPIC for interrupt routing
[   44.474432] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   44.474453] PCI: Probing PCI hardware (bus 00)
[   44.474566] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   44.474992] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   44.474997] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   44.475246] Boot video device is 0000:01:00.0
[   44.475287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   44.490607] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   44.490976] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[   44.491333] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   44.491704] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   44.494119] Linux Plug and Play Support v0.97 (c) Adam Belay
[   44.494141] pnp: PnP ACPI init
[   44.497205] pnp: PnP ACPI: found 11 devices
[   44.497213] PnPBIOS: Disabled by ACPI PNP
[   44.497314] PCI: Using ACPI for IRQ routing
[   44.497319] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   44.520082] NET: Registered protocol family 8
[   44.520085] NET: Registered protocol family 20
[   44.520900] PCI: Bridge: 0000:00:01.0
[   44.520903]   IO window: disabled.
[   44.520909]   MEM window: dc000000-ddffffff
[   44.520914]   PREFETCH window: d0000000-d7ffffff
[   44.520933] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   44.520977] NET: Registered protocol family 2
[   44.550549] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   44.550704] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   44.551067] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   44.551257] TCP: Hash tables configured (established 16384 bind 8192)
[   44.551261] TCP reno registered
[   44.562584] checking if image is initramfs... it is
[   45.292482] Freeing initrd memory: 6888k freed
[   45.293289] audit: initializing netlink socket (disabled)
[   45.293316] audit(1189887356.608:1): initialized
[   45.293493] VFS: Disk quotas dquot_6.5.1
[   45.293529] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   45.293613] io scheduler noop registered
[   45.293617] io scheduler anticipatory registered
[   45.293620] io scheduler deadline registered
[   45.293630] io scheduler cfq registered (default)
[   45.293651] Applying VIA southbridge workaround.
[   45.293656] PCI: Enabling Via external APIC routing
[   45.294039] isapnp: Scanning for PnP cards...
[   45.648212] isapnp: No Plug & Play device found
[   45.683101] Real Time Clock Driver v1.12ac
[   45.683177] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.683365] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.683660] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.684477] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.684938] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.685272] mice: PS/2 mouse device common for all mice
[   45.686178] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.686566] input: Macintosh mouse button emulation as /class/input/input0
[   45.686627] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   45.686633] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   45.686997] PNP: No PS/2 controller found. Probing ports directly.
[   45.687580] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.687588] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.687784] EISA: Probing bus 0 at eisa.0
[   45.687812] Cannot allocate resource for EISA slot 4
[   45.687815] Cannot allocate resource for EISA slot 5
[   45.687818] Cannot allocate resource for EISA slot 6
[   45.687831] EISA: Detected 0 cards.
[   45.718115] TCP cubic registered
[   45.718126] NET: Registered protocol family 1
[   45.718164] Using IPI No-Shortcut mode
[   45.718303] ACPI: (supports S0 S1 S4 S5)
[   45.718366]   Magic number: 7:985:295
[   45.718414]   hash matches device ttyz9
[   45.718437]   hash matches device ttywc
[   45.718609]   hash matches device tty28
[   45.719291] Freeing unused kernel memory: 328k freed
[   45.721582] Time: tsc clocksource has been installed.
[   45.945863] Capability LSM initialized
[   46.082612] md: raid0 personality registered for level 0
[   46.741262] SCSI subsystem initialized
[   46.748228] libata version 2.20 loaded.
[   46.752030] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   46.752059] VP_IDE: chipset revision 6
[   46.752063] VP_IDE: not 100% native mode: will probe irqs later
[   46.752076] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[   46.752087]     ide0: BM-DMA at 0x9000-0x9007, BIOS settings: hda:DMA, hdb:pio
[   46.752106]     ide1: BM-DMA at 0x9008-0x900f, BIOS settings: hdc:pio, hdd:pio
[   46.752115] Probing IDE interface ide0...
[   46.777896] usbcore: registered new interface driver usbfs
[   46.777938] usbcore: registered new interface driver hub
[   46.777979] usbcore: registered new device driver usb
[   46.779376] USB Universal Host Controller Interface driver v3.0
[   46.840295] 8139too Fast Ethernet driver 0.9.28
[   47.042983] FDC 0 is a post-1991 82077
[   47.228697] hda: ST3120026A, ATA DISK drive
[   47.904595] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   47.904990] Probing IDE interface ide1...
[   48.474216] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   48.474236] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   48.474245] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 5 to 11
[   48.474277] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   48.474792] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   48.474837] uhci_hcd 0000:00:07.2: irq 11, io base 0x00009400
[   48.475766] usb usb1: configuration #1 chosen from 1 choice
[   48.476108] hub 1-0:1.0: USB hub found
[   48.476132] hub 1-0:1.0: 2 ports detected
[   48.486687] hda: max request size: 512KiB
[   48.489093] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   48.489254] hda: cache flushes supported
[   48.489333]  hda: hda1 hda2 < hda5 >
[   48.583790] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   48.583801] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 5 to 11
[   48.583831] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   48.583864] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   48.583893] uhci_hcd 0000:00:07.3: irq 11, io base 0x00009800
[   48.584044] usb usb2: configuration #1 chosen from 1 choice
[   48.584084] hub 2-0:1.0: USB hub found
[   48.584100] hub 2-0:1.0: 2 ports detected
[   48.690289] Attempting manual resume
[   48.690296] swsusp: Resume From Partition 3:5
[   48.690298] PM: Checking swsusp image.
[   48.690588] PM: Resume from disk failed.
[   48.691877] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   48.692170] eth0: RealTek RTL8139 at 0xe0864000, 00:06:4f:0a:2a:43, IRQ 16
[   48.692174] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   48.696638] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   48.696822] r8169 Gigabit Ethernet driver 2.2LK loaded
[   48.696861] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 17
[   48.697055] eth1: RTL8169sb/8110sb at 0xe0852000, 00:e0:4c:69:7b:33, IRQ 17
[   48.698257] sata_sil 0000:00:0a.0: version 2.2
[   48.698284] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 19 (level, low) -> IRQ 18
[   48.698434] ata1: SATA max UDMA/100 cmd 0xe0854080 ctl 0xe085408a bmdma 0xe0854000 irq 18
[   48.698487] ata2: SATA max UDMA/100 cmd 0xe08540c0 ctl 0xe08540ca bmdma 0xe0854008 irq 18
[   48.698511] scsi0 : sata_sil
[   48.787416] kjournald starting.  Commit interval 5 seconds
[   48.787439] EXT3-fs: mounted filesystem with ordered data mode.
[   49.167142] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   49.199449] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   49.199463] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[   49.199467] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   49.211393] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   49.211400] ata1.00: configured for UDMA/100
[   49.211422] scsi1 : sata_sil
[   49.682791] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   49.715085] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   49.715098] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[   49.715102] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   49.727034] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   49.727042] ata2.00: configured for UDMA/100
[   49.727237] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   49.727541] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   53.741104] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   55.415450] parport_pc: VIA 686A/8231 detected
[   55.415457] parport_pc: probing current configuration
[   55.415477] parport_pc: Current parallel port base: 0x378
[   55.415530] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   55.510662] parport_pc: VIA parallel port: io=0x378, irq=7
[   55.773151] Linux agpgart interface v0.102 (c) Dave Jones
[   55.788810] NET: Registered protocol family 17
[   56.034402] input: PC Speaker as /class/input/input1
[   56.053230] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.055921] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.067568] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   56.072647] agpgart: AGP aperture is 64M @ 0xd8000000
[   56.199079] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   56.199107] sda: Write Protect is off
[   56.199110] sda: Mode Sense: 00 3a 00 00
[   56.199134] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.199245] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   56.199258] sda: Write Protect is off
[   56.199262] sda: Mode Sense: 00 3a 00 00
[   56.199281] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.199286]  sda: sda1
[   56.340450] sd 0:0:0:0: Attached scsi disk sda
[   56.345043] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[   56.345071] sdb: Write Protect is off
[   56.345074] sdb: Mode Sense: 00 3a 00 00
[   56.345097] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.345216] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[   56.345230] sdb: Write Protect is off
[   56.345233] sdb: Mode Sense: 00 3a 00 00
[   56.345254] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.345258]  sdb: sdb1
[   56.405273] sd 1:0:0:0: Attached scsi disk sdb
[   56.448677] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   56.448732] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   56.878101] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   56.878118] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   56.878127] PCI: VIA VLink IRQ fixup for 0000:00:07.5, from 11 to 10
[   56.878290] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   57.175420] md: md0 stopped.
[   57.205772] md: bind<sdb1>
[   57.206005] md: bind<sda1>
[   57.282653] md0: setting max_sectors to 128, segment boundary to 32767

---

### Post by deebo32 on 2007-09-18
theres ~nothing there, eth1 just doesnt come up, no errors

---

### Post by noob12 on 2007-09-18
Can you edit your /etc/iftab and make the eth1 line read
```

eth1 mac 00:e0:4c:69:7b:33 arp 1

```
and see if that helps at all?

ADDED:  You need to reboot after that.

---

### Post by noob12 on 2007-09-18
Also, please make sure you have the eth1 card plugged into an active connection at boot time.
There's a known issue with that, and that is a second issue you might face if you are moving the cable around.

---

### Post by deebo32 on 2007-09-18
the mac fix worked, didnt even notice they were the same

but this is really weird, since to begin with the 1Gbit card was the only one in the computer

nevertheless, thanks for the help :)

---

### Post by noob12 on 2007-09-18
OK.  The odd thing was the mac in the old iftab was not the same as the other card but one higher (hex).   In any case, you can mark the thread solved.  Cheers.

---

