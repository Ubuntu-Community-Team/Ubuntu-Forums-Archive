---
title: "getting my wireless back (xsupplicant screwed it up)"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by hcdaume3 on 2006-10-01
It used to be that when I went into network-admin, I had one wireless device (eth1) and one wired device (eth0).  Everything worked fine.  I then installed xsupplicant so I could connect to my university wireless network.  This didn't work, which is not a huge problem.  The bigger problem is that now when I go into network-admin, both eth0 and eth1 show up as wired devices, so I get go to properties on eth1 to get a list of wireless networks and connect!

How can I fix this?

---

### Post by dmizer on 2006-10-02
post the output of dmesg (in code tags to make the post more user friendly).
also post the output of lspci and the contents of your /etc/network/interfaces

---

### Post by hcdaume3 on 2006-10-02
dmesg gives:

<code>

[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f6e0000 (usable)
[17179569.184000]  BIOS-e820: 000000003f6e0000 - 000000003f6ec000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003f6ec000 - 000000003f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 118MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 259808
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30432 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 SONY                                  ) @ 0x000f68a0
[17179569.184000] ACPI: RSDT (v001   SONY       G7 0x20050609 PTL  0x00000000) @ 0x3f6e7808
[17179569.184000] ACPI: FADT (v002   SONY       G7 0x20050609 PTL  0x00000050) @ 0x3f6ebec2
[17179569.184000] ACPI: BOOT (v001   SONY       G7 0x20050609 PTL  0x00000001) @ 0x3f6ebfd8
[17179569.184000] ACPI: SSDT (v001   SONY       G7 0x20050609 PTL  0x00000000) @ 0x3f6e7838
[17179569.184000] ACPI: DSDT (v001   SONY       G7 0x20050609 PTL  0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec10000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (017f1000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 595.595 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.988000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.988000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.052000] Memory: 1019548k/1039232k available (1976k kernel code, 18844k reserved, 606k data, 288k init, 121728k highmem)
[17179571.052000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.132000] Calibrating delay using timer specific routine.. 1192.29 BogoMIPS (lpj=2384580)
[17179571.132000] Security Framework v1.0.0 initialized
[17179571.132000] SELinux:  Disabled at boot.
[17179571.132000] Mount-cache hash table entries: 512
[17179571.132000] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000
[17179571.132000] CPU: After vendor identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000
[17179571.132000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179571.132000] CPU: L2 cache: 2048K
[17179571.132000] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00000040 00000180 00000000 00000000
[17179571.132000] mtrr: v2.0 (20020519)
[17179571.132000] CPU: Intel(R) Pentium(R) M processor 1.20GHz stepping 08
[17179571.132000] Enabling fast FPU save and restore... done.
[17179571.132000] Enabling unmasked SIMD FPU exception support... done.
[17179571.132000] Checking 'hlt' instruction... OK.
[17179571.148000] checking if image is initramfs... it is
[17179572.868000] Freeing initrd memory: 6595k freed
[17179572.876000] ACPI: Looking for DSDT ... not found!
[17179572.884000] NET: Registered protocol family 16
[17179572.884000] EISA bus registered
[17179572.884000] ACPI: bus type pci registered
[17179572.884000] PCI: PCI BIOS revision 2.10 entry at 0xfd9b2, last bus=2
[17179572.884000] PCI: Using configuration type 1
[17179572.884000] ACPI: Subsystem revision 20051216
[17179572.892000] ACPI: Interpreter enabled
[17179572.892000] ACPI: Using PIC for interrupt routing
[17179572.892000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.892000] PCI: Probing PCI hardware (bus 00)
[17179572.900000] Boot video device is 0000:00:02.0
[17179572.900000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179572.900000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179572.900000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.900000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.900000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.916000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179572.916000] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[17179572.916000] ACPI: PCI Interrupt Link [LNKB] (IRQs 9) *0, disabled.
[17179572.920000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9) *0, disabled.
[17179572.920000] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
[17179572.920000] ACPI: PCI Interrupt Link [LNKE] (IRQs *9)
[17179572.920000] ACPI: PCI Interrupt Link [LNKF] (IRQs 5) *0, disabled.
[17179572.920000] ACPI: PCI Interrupt Link [LNKG] (IRQs 9) *0, disabled.
[17179572.920000] ACPI: PCI Interrupt Link [LNKH] (IRQs 9) *0, disabled.
[17179572.920000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179572.924000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.924000] pnp: PnP ACPI init
[17179572.928000] pnp: PnP ACPI: found 9 devices
[17179572.928000] PnPBIOS: Disabled by ACPI PNP
[17179572.928000] PCI: Using ACPI for IRQ routing
[17179572.928000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.936000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179572.936000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179572.936000]   IO window: 00003400-000034ff
[17179572.936000]   IO window: 00003800-000038ff
[17179572.936000]   PREFETCH window: 50000000-51ffffff
[17179572.936000]   MEM window: 54000000-55ffffff
[17179572.936000] PCI: Bridge: 0000:00:1e.0
[17179572.936000]   IO window: 3000-3fff
[17179572.936000]   MEM window: e0200000-e02fffff
[17179572.936000]   PREFETCH window: 50000000-51ffffff
[17179572.936000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.936000] **** SET: Misaligned resource pointer: dfe656c2 Type 07 Len 0
[17179572.936000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[17179572.936000] PCI: setting IRQ 9 as level-triggered
[17179572.936000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179572.936000] Simple Boot Flag at 0x36 set to 0x1
[17179572.936000] audit: initializing netlink socket (disabled)
[17179572.936000] audit(1159814073.936:1): initialized
[17179572.936000] highmem bounce pool size: 64 pages
[17179572.936000] VFS: Disk quotas dquot_6.5.1
[17179572.936000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.936000] Initializing Cryptographic API
[17179572.936000] io scheduler noop registered
[17179572.936000] io scheduler anticipatory registered
[17179572.936000] io scheduler deadline registered
[17179572.936000] io scheduler cfq registered
[17179572.940000] isapnp: Scanning for PnP cards...
[17179573.292000] isapnp: No Plug & Play device found
[17179573.324000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.332000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.332000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.332000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.336000] **** SET: Misaligned resource pointer: df8791c2 Type 07 Len 0
[17179573.336000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[17179573.336000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179573.336000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179573.340000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.340000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.340000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.340000] mice: PS/2 mouse device common for all mice
[17179573.340000] EISA: Probing bus 0 at eisa.0
[17179573.340000] Cannot allocate resource for EISA slot 1
[17179573.340000] Cannot allocate resource for EISA slot 2
[17179573.340000] Cannot allocate resource for EISA slot 3
[17179573.340000] EISA: Detected 0 cards.
[17179573.340000] NET: Registered protocol family 2
[17179573.376000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.380000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.380000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.380000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.380000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.380000] TCP reno registered
[17179573.380000] TCP bic registered
[17179573.380000] NET: Registered protocol family 1
[17179573.380000] NET: Registered protocol family 8
[17179573.380000] NET: Registered protocol family 20
[17179573.380000] Using IPI Shortcut mode
[17179573.380000] ACPI wakeup devices: 
[17179573.380000] PWRB PCIB LANC  EC0 USB0 USB1 USB2 USB7 
[17179573.380000] ACPI: (supports S0 S3 S4 S5)
[17179573.380000] Freeing unused kernel memory: 288k freed
[17179573.484000] vga16fb: initializing
[17179573.484000] vga16fb: mapped to 0xc00a0000
[17179573.608000] Console: switching to colour frame buffer device 80x30
[17179573.608000] fb0: VGA16 VGA frame buffer device
[17179573.628000] Capability LSM initialized
[17179573.704000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179573.704000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.708000] ACPI: Thermal Zone [ATF0] (30 C)
[17179574.548000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179574.548000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179574.548000] ACPI: PCI Interrupt 0000:00:1f.1[A]: no GSI
[17179574.548000] ICH4: chipset revision 3
[17179574.548000] ICH4: not 100% native mode: will probe irqs later
[17179574.548000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:pio, hdb:pio
[17179574.548000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:pio, hdd:pio
[17179574.548000] Probing IDE interface ide0...
[17179574.836000] hda: TOSHIBA MK6006GAH, ATA DISK drive
[17179575.508000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.532000] Probing IDE interface ide1...
[17179576.268000] hdc: UJDA765aDVD/CDRW, ATAPI CD/DVD-ROM drive
[17179576.604000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.616000] hda: max request size: 1024KiB
[17179576.632000] hda: 117210240 sectors (60011 MB), CHS=16383/255/63, UDMA(100)
[17179576.632000] hda: cache flushes supported
[17179576.632000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[17179576.704000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.704000] Uniform CD-ROM driver Revision: 3.20
[17179577.088000] usbcore: registered new driver usbfs
[17179577.088000] usbcore: registered new driver hub
[17179577.092000] USB Universal Host Controller Interface driver v2.3
[17179577.092000] **** SET: Misaligned resource pointer: dfd0a702 Type 07 Len 0
[17179577.092000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[17179577.092000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179577.092000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.092000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.092000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.092000] uhci_hcd 0000:00:1d.0: irq 9, io base 0x00001820
[17179577.092000] hub 1-0:1.0: USB hub found
[17179577.092000] hub 1-0:1.0: 2 ports detected
[17179577.196000] **** SET: Misaligned resource pointer: dfd0a402 Type 07 Len 0
[17179577.196000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[17179577.196000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[17179577.196000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.196000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.196000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.196000] uhci_hcd 0000:00:1d.1: irq 9, io base 0x00001840
[17179577.200000] hub 2-0:1.0: USB hub found
[17179577.200000] hub 2-0:1.0: 2 ports detected
[17179577.268000] ieee1394: Initialized config rom entry `ip1394'
[17179577.304000] **** SET: Misaligned resource pointer: dfd2edc2 Type 07 Len 0
[17179577.304000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[17179577.304000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179577.304000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.304000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.304000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.304000] uhci_hcd 0000:00:1d.2: irq 9, io base 0x00001860
[17179577.304000] hub 3-0:1.0: USB hub found
[17179577.304000] hub 3-0:1.0: 2 ports detected
[17179577.408000] **** SET: Misaligned resource pointer: dfd2eac2 Type 07 Len 0
[17179577.408000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[17179577.408000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[17179577.408000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.408000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.408000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.408000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179577.412000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179577.412000] ehci_hcd 0000:00:1d.7: irq 9, io mem 0xe0100000
[17179577.416000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.416000] hub 4-0:1.0: USB hub found
[17179577.416000] hub 4-0:1.0: 6 ports detected
[17179577.520000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179577.520000] **** SET: Misaligned resource pointer: dfd2e7c2 Type 07 Len 0
[17179577.520000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 9
[17179577.520000] ACPI: PCI Interrupt 0000:02:04.2[C] -> Link [LNKG] -> GSI 9 (level, low) -> IRQ 9
[17179577.572000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[e0207000-e02077ff]  Max Packet=[2048]
[17179577.692000] Attempting manual resume
[17179577.740000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.768000] kjournald starting.  Commit interval 5 seconds
[17179578.152000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17179578.844000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301d72562]
[17179598.540000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.552000] agpgart: Detected an Intel 855 Chipset.
[17179598.552000] agpgart: Detected 8060K stolen memory.
[17179598.592000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179599.936000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179600.044000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179600.500000] hw_random hardware driver 1.0.0 loaded
[17179600.588000] Bluetooth: Core ver 2.8
[17179600.588000] NET: Registered protocol family 31
[17179600.588000] Bluetooth: HCI device and connection manager initialized
[17179600.588000] Bluetooth: HCI socket layer initialized
[17179600.724000] Bluetooth: HCI USB driver ver 2.9
[17179600.800000] usbcore: registered new driver hci_usb
[17179601.040000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179601.040000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179601.212000] Real Time Clock Driver v1.12
[17179601.836000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179601.836000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179601.860000] intel8x0_measure_ac97_clock: measured 55367 usecs
[17179601.860000] intel8x0: clocking to 48000
[17179601.860000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179601.860000] Yenta: CardBus bridge found at 0000:02:04.0 [104d:818f]
[17179601.860000] Yenta: Enabling burst memory read transactions
[17179601.860000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179601.860000] Yenta: Routing CardBus interrupts to PCI
[17179601.860000] Yenta TI: socket 0000:02:04.0, mfunc 0x01001b22, devctl 0x64
[17179601.896000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179601.912000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17179601.912000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179601.960000] ieee80211_crypt: registered algorithm 'NULL'
[17179601.960000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179601.960000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179602.076000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179602.076000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179602.076000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179602.092000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 9
[17179602.092000] Socket status: 30000006
[17179602.092000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179602.092000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179602.092000] cs: IO port probe 0x3000-0x3fff: clean.
[17179602.092000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179602.092000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179602.168000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179602.192000] e100: eth0: e100_probe: addr 0xe0205000, irq 9, MAC addr 00:01:4A:24:E2:13
[17179602.196000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[17179602.196000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179602.456000] input: PS/2 Mouse as /class/input/input1
[17179602.472000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
[17179602.580000] ts: Compaq touchscreen protocol output
[17179602.888000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179603.244000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179603.836000] lp: driver loaded but no devices found
[17179604.028000] SCSI subsystem initialized
[17179604.048000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179604.048000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179604.048000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179604.172000] Adding 1622524k swap on /dev/hda5.  Priority:-1 extents:1 across:1622524k
[17179604.228000] EXT3 FS on hda3, internal journal
[17179604.356000] NET: Registered protocol family 17
[17179604.540000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179604.708000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179604.708000] md: bitmap version 4.39
[17179606.872000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179606.988000] NTFS volume version 3.1.
[17179608.864000] NET: Registered protocol family 10
[17179608.864000] lo: Disabled Privacy Extensions
[17179608.864000] IPv6 over IPv4 tunneling driver
[17179610.444000] ACPI: AC Adapter [ACAD] (off-line)
[17179610.448000] ACPI: Battery Slot [BAT1] (battery present)
[17179610.632000] ACPI: Lid Switch [LID0]
[17179610.632000] ACPI: Power Button (CM) [PWRB]
[17179610.848000] ibm_acpi: ec object not found
[17179610.900000] pcc_acpi: loading...
[17179610.952000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[17179611.100000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179617.224000] ppdev: user-space parallel port driver
[17179619.212000] [drm] Initialized drm 1.0.1 20051102
[17179619.260000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179619.260000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179619.260000] [drm] Initialized i915 1.4.0 20060119 on minor 1
[17179619.780000] eth0: no IPv6 routers present
[17179620.524000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179620.524000] apm: overridden by ACPI.
</code>

lspci gives:

<code>
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:02:04.3 Mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
0000:02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
</code>

and /etc/network/interfaces is:

<code>
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp





auto eth1
</code>

---

### Post by jwbirdsong on 2006-10-02
I know it sounds simplistic but I had same problem (assuming caused by xsupplicant also)
It SEEMS to change my (your?) /etc/network/interfaces file..if I do a** sudo gedit /etc/network/interfaces file** and cut paste the  auto eth1 "header" above the eth1 line so you have 
```
auto eth1
iface eth1 inet dhcp
``` 
And reboot, I connect on boot every time

But once that "header" moves to bottom of the file I can't connect at all
Maybe it will work for you too

---

### Post by hcdaume3 on 2006-10-03
Unfortunately, just moving the auto eth1 didn't fix it :(.

---

### Post by jwbirdsong on 2006-10-03
I didn't really have a LOT of hope for it...but as it works for me thought it was worth a shot.....I would also make sure BOTH lines have the "header"  as upon reading again it looks like you are trying to connect with eth0 not eth1, correct??  I missed the fact that **both** lines have misplaced/missing headers....
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

---

### Post by dmizer on 2006-10-03
well, your wireless is being detected and the module is loading, but it's not getting atached to an interface (eth0, eth1 etc).  since the only interface that's loading in dmesg is your wired adapter, was there any special configuration you had to do initially to make that card work (pre xsupplicant)

btw: code tags are enclosed in these type brackets: []

---

### Post by hcdaume3 on 2006-10-04
grrr, no i didn't have to do any special configuration at all...it worked straight out of the box.

it is eth1 that i'm trying to use (eth0 is the wired and works fine).  i tried moving the "auto eth0" above and that didn't help either.

---

### Post by hcdaume3 on 2006-10-04
grrr, no i didn't have to do any special configuration at all...it worked straight out of the box.

it is eth1 that i'm trying to use (eth0 is the wired and works fine).  i tried moving the "auto eth0" above and that didn't help either.

---

### Post by dmizer on 2006-10-04
> **hcdaume3 said:**
> grrr, no i didn't have to do any special configuration at all...it worked straight out of the box.

it is eth1 that i'm trying to use (eth0 is the wired and works fine).  i tried moving the "auto eth0" above and that didn't help either.

well, according to your dmesg, you have no eth1.  you can't use eth1 if it's not even there.

if you go to system > administration > network > and then click on hardware, do you see anything other than your wired adapter?

---

### Post by hcdaume3 on 2006-10-07
Not sure what you mean...under network-admin (system/admin/network settings) I have both eth1 and eth0 listed under connections, but both are listed as wired connections.

In System/Admin/Device manager, I have (among other things), a 82801DB PRO/100 BE (MOB) Ethernet Controller (with a subitem "Networking interface" and a PRO/Wireless 2200BG with a WLAN Interface under it.

---

