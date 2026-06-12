---
title: "Logitech M-RBB93 on Vaio VGN-T150 laptop"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by fastluck on 2006-11-10
I had a good, working Ubuntu installation (4.10).  I decided to upgrade and everything below quit working.  So I reinstalled Edgy from scratch with the same problems.  This post is about my mice.

I have a Sony Vaio VGN-T150.  Both the onboard mousepad and the bluetooth mouse (Logitech M-RBB93) quit working.

According to ps, HCID is already running.  
Here's the thing--I wrote a script that I use to get the mouse working. This script worked until I upgraded.  Now, when I run this script:

```
#!/bin/bash
modprobe hidp
hcid
hidd --server
hidd --connect 00:07:61:3D:AF:C7

```

...it hangs for awhile.  Then I get this error:
```
Can't get device information: Host is down

```

What is going on?  Why did it just magically quit working when I upgraded?    

DMESG Output:

```
[17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[17179569.184000]  BIOS-e820: 000000001f6e0000 - 000000001f6ec000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f6ec000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 502MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 128736
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124640 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 SONY                                  ) @ 0x000f68a0
[17179569.184000] ACPI: RSDT (v001   SONY       G7 0x20050119 PTL  0x00000000) @ 0x1f6e7808
[17179569.184000] ACPI: FADT (v002   SONY       G7 0x20050119 PTL  0x00000050) @ 0x1f6ebec2
[17179569.184000] ACPI: BOOT (v001   SONY       G7 0x20050119 PTL  0x00000001) @ 0x1f6ebfd8
[17179569.184000] ACPI: SSDT (v001   SONY       G7 0x20050119 PTL  0x00000000) @ 0x1f6e7838
[17179569.184000] ACPI: DSDT (v001   SONY       G7 0x20050119 PTL  0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=340dbe01-74d6-4279-b9c5-e80b1475a073 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (013f2000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1091.909 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.468000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.468000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.484000] Memory: 499732k/514944k available (1829k kernel code, 14640k reserved, 1038k data, 288k init, 0k highmem)
[17179569.484000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.564000] Calibrating delay using timer specific routine.. 2185.49 BogoMIPS (lpj=4370981)
[17179569.564000] Security Framework v1.0.0 initialized
[17179569.564000] SELinux:  Disabled at boot.
[17179569.564000] Mount-cache hash table entries: 512
[17179569.564000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.564000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.564000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.564000] CPU: L2 cache: 2048K
[17179569.564000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179569.564000] CPU: Intel(R) Pentium(R) M processor 1.10GHz stepping 06
[17179569.564000] Checking 'hlt' instruction... OK.
[17179569.580000] SMP alternatives: switching to UP code
[17179569.580000] Freeing SMP alternatives: 0k freed
[17179569.580000] checking if image is initramfs... it is
[17179570.548000] Freeing initrd memory: 6628k freed
[17179570.548000] ACPI: Core revision 20060707
[17179570.548000] ACPI: Looking for DSDT ... not found!
[17179570.552000] ACPI: System reset via FADT Reset Register is supported
[17179570.552000] machine_reset = acpi_machine_reset
[17179570.552000] NET: Registered protocol family 16
[17179570.552000] EISA bus registered
[17179570.552000] ACPI: bus type pci registered
[17179570.552000] PCI: PCI BIOS revision 2.10 entry at 0xfd9b2, last bus=2
[17179570.552000] PCI: Using configuration type 1
[17179570.552000] Setting up standard PCI resources
[17179570.568000] ACPI: Interpreter enabled
[17179570.568000] ACPI: Using PIC for interrupt routing
[17179570.568000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.568000] PCI: Probing PCI hardware (bus 00)
[17179570.572000] Boot video device is 0000:00:02.0
[17179570.572000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.572000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179570.572000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.572000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.572000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.572000] Please report the result to linux-kernel to fix this permanently
[17179570.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.580000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.584000] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[17179570.584000] ACPI: PCI Interrupt Link [LNKB] (IRQs 9) *0, disabled.
[17179570.584000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9) *0, disabled.
[17179570.584000] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
[17179570.584000] ACPI: PCI Interrupt Link [LNKE] (IRQs *9)
[17179570.584000] ACPI: PCI Interrupt Link [LNKF] (IRQs 5) *0, disabled.
[17179570.584000] ACPI: PCI Interrupt Link [LNKG] (IRQs 9) *0, disabled.
[17179570.584000] ACPI: PCI Interrupt Link [LNKH] (IRQs 9) *0, disabled.
[17179570.584000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179570.588000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.588000] pnp: PnP ACPI init
[17179570.588000] pnp: PnP ACPI: found 9 devices
[17179570.588000] PnPBIOS: Disabled by ACPI PNP
[17179570.588000] PCI: Using ACPI for IRQ routing
[17179570.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.596000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.596000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179570.596000]   IO window: 00003400-000034ff
[17179570.596000]   IO window: 00003800-000038ff
[17179570.596000]   PREFETCH window: 30000000-31ffffff
[17179570.596000]   MEM window: 34000000-35ffffff
[17179570.596000] PCI: Bridge: 0000:00:1e.0
[17179570.596000]   IO window: 3000-3fff
[17179570.596000]   MEM window: e0200000-e02fffff
[17179570.596000]   PREFETCH window: 30000000-31ffffff
[17179570.596000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.596000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[17179570.596000] PCI: setting IRQ 9 as level-triggered
[17179570.596000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179570.596000] NET: Registered protocol family 2
[17179570.628000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.628000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.628000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.628000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.628000] TCP reno registered
[17179570.628000] Simple Boot Flag at 0x36 set to 0x1
[17179570.628000] audit: initializing netlink socket (disabled)
[17179570.628000] audit(1163193860.628:1): initialized
[17179570.628000] VFS: Disk quotas dquot_6.5.1
[17179570.628000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.628000] Initializing Cryptographic API
[17179570.628000] io scheduler noop registered
[17179570.628000] io scheduler anticipatory registered
[17179570.628000] io scheduler deadline registered
[17179570.628000] io scheduler cfq registered (default)
[17179570.628000] isapnp: Scanning for PnP cards...
[17179570.980000] isapnp: No Plug & Play device found
[17179571.008000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.008000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[17179571.008000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179571.008000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179571.008000] mice: PS/2 mouse device common for all mice
[17179571.008000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.008000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.008000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.008000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.016000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.016000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.016000] EISA: Probing bus 0 at eisa.0
[17179571.016000] Cannot allocate resource for EISA slot 1
[17179571.016000] Cannot allocate resource for EISA slot 2
[17179571.016000] Cannot allocate resource for EISA slot 3
[17179571.016000] EISA: Detected 0 cards.
[17179571.016000] TCP bic registered
[17179571.016000] NET: Registered protocol family 1
[17179571.016000] NET: Registered protocol family 8
[17179571.016000] NET: Registered protocol family 20
[17179571.016000] Using IPI Shortcut mode
[17179571.016000] ACPI: (supports S0 S3 S4 S5)
[17179571.020000] Freeing unused kernel memory: 288k freed
[17179571.052000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.156000] Capability LSM initialized
[17179572.196000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.196000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.200000] ACPI: Thermal Zone [ATF0] (28 C)
[17179572.552000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179572.552000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.552000] ACPI: Unable to derive IRQ for device 0000:00:1f.1
[17179572.552000] ACPI: PCI Interrupt 0000:00:1f.1[A]: no GSI
[17179572.552000] ICH4: chipset revision 3
[17179572.552000] ICH4: not 100% native mode: will probe irqs later
[17179572.552000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:pio, hdb:pio
[17179572.552000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:pio, hdd:pio
[17179572.552000] Probing IDE interface ide0...
[17179572.844000] hda: TOSHIBA MK4004GAH, ATA DISK drive
[17179573.516000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.964000] Probing IDE interface ide1...
[17179574.700000] hdc: MATSHITAUJ-822Da, ATAPI CD/DVD-ROM drive
[17179575.036000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.044000] hda: max request size: 128KiB
[17179575.048000] hda: 78126048 sectors (40000 MB), CHS=65535/16/63, UDMA(100)
[17179575.052000] hda: cache flushes supported
[17179575.052000]  hda: hda1 hda2 < hda5 >
[17179575.160000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.160000] Uniform CD-ROM driver Revision: 3.20
[17179575.512000] usbcore: registered new driver usbfs
[17179575.512000] usbcore: registered new driver hub
[17179575.512000] USB Universal Host Controller Interface driver v3.0
[17179575.516000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[17179575.516000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179575.516000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.516000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.516000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.516000] uhci_hcd 0000:00:1d.0: irq 9, io base 0x00001820
[17179575.516000] usb usb1: configuration #1 chosen from 1 choice
[17179575.516000] hub 1-0:1.0: USB hub found
[17179575.516000] hub 1-0:1.0: 2 ports detected
[17179575.588000] ieee1394: Initialized config rom entry `ip1394'
[17179575.620000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[17179575.620000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[17179575.620000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.620000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.620000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.620000] uhci_hcd 0000:00:1d.1: irq 9, io base 0x00001840
[17179575.620000] usb usb2: configuration #1 chosen from 1 choice
[17179575.620000] hub 2-0:1.0: USB hub found
[17179575.620000] hub 2-0:1.0: 2 ports detected
[17179575.724000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[17179575.724000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179575.724000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.724000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.724000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.724000] uhci_hcd 0000:00:1d.2: irq 9, io base 0x00001860
[17179575.724000] usb usb3: configuration #1 chosen from 1 choice
[17179575.724000] hub 3-0:1.0: USB hub found
[17179575.724000] hub 3-0:1.0: 2 ports detected
[17179575.828000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[17179575.828000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[17179575.828000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.828000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.828000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179575.828000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.828000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.828000] ehci_hcd 0000:00:1d.7: irq 9, io mem 0xe0100000
[17179575.832000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.832000] usb usb4: configuration #1 chosen from 1 choice
[17179575.832000] hub 4-0:1.0: USB hub found
[17179575.832000] hub 4-0:1.0: 6 ports detected
[17179575.936000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 9
[17179575.936000] ACPI: PCI Interrupt 0000:02:04.2[C] -> Link [LNKG] -> GSI 9 (level, low) -> IRQ 9
[17179575.996000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[e0207000-e02077ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179576.144000] kjournald starting.  Commit interval 5 seconds
[17179576.144000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.752000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179576.928000] usb 2-1: configuration #1 chosen from 1 choice
[17179577.172000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17179577.268000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301c7afda]
[17179577.372000] usb 3-1: configuration #1 chosen from 1 choice
[17179592.628000] Real Time Clock Driver v1.12ac
[17179593.004000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.016000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.056000] hw_random: RNG not detected
[17179593.956000] Bluetooth: Core ver 2.8
[17179593.956000] NET: Registered protocol family 31
[17179593.956000] Bluetooth: HCI device and connection manager initialized
[17179593.956000] Bluetooth: HCI socket layer initialized
[17179593.976000] Bluetooth: HCI USB driver ver 2.9
[17179593.980000] usbcore: registered new driver hci_usb
[17179594.116000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.152000] agpgart: Detected an Intel 855 Chipset.
[17179594.152000] agpgart: Detected 8060K stolen memory.
[17179594.164000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179594.424000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179594.424000] Yenta: CardBus bridge found at 0000:02:04.0 [104d:818f]
[17179594.424000] Yenta: Enabling burst memory read transactions
[17179594.424000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179594.424000] Yenta: Routing CardBus interrupts to PCI
[17179594.424000] Yenta TI: socket 0000:02:04.0, mfunc 0x01001b22, devctl 0x64
[17179594.656000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 9
[17179594.656000] Socket status: 30000006
[17179594.656000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179594.656000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179594.656000] cs: IO port probe 0x3000-0x3fff: clean.
[17179594.656000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179594.656000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179594.668000] input: PS/2 Mouse as /class/input/input1
[17179594.688000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
[17179594.784000] ieee80211_crypt: registered algorithm 'NULL'
[17179594.804000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179594.804000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179594.836000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179594.836000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179594.836000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179594.836000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[17179594.836000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179594.888000] ts: Compaq touchscreen protocol output
[17179595.128000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179595.128000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179595.452000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179595.452000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179595.476000] e100: eth1: e100_probe: addr 0xe0205000, irq 9, MAC addr 00:01:4A:04:81:0C
[17179595.548000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179595.548000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179595.808000] cs: IO port probe 0x100-0x3af: clean.
[17179595.808000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179595.812000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.812000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.812000] cs: IO port probe 0xa00-0xaff: clean.
[17179595.836000] usbcore: registered new driver hiddev
[17179595.852000] input: Logitech Apple Optical USB Mouse as /class/input/input3
[17179595.852000] input: USB HID v1.10 Mouse [Logitech Apple Optical USB Mouse] on usb-0000:00:1d.1-1
[17179595.852000] usbcore: registered new driver usbhid
[17179595.852000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179596.236000] ieee80211_crypt: registered algorithm 'WEP'
[17179596.368000] intel8x0_measure_ac97_clock: measured 55491 usecs
[17179596.368000] intel8x0: clocking to 48000
[17179596.520000] lp: driver loaded but no devices found
[17179596.612000] SCSI subsystem initialized
[17179596.620000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179596.620000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179596.736000] Adding 1485972k swap on /dev/disk/by-uuid/1862a939-f15f-4376-9364-572a6a64d199.  Priority:-1 extents:1 across:1485972k
[17179596.808000] EXT3 FS on hda1, internal journal
[17179597.044000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.044000] md: bitmap version 4.39
[17179597.304000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179597.392000] NET: Registered protocol family 17
[17179603.612000] ACPI: AC Adapter [ACAD] (on-line)
[17179603.660000] ACPI: Battery Slot [BAT1] (battery present)
[17179603.680000] ACPI: Lid Switch [LID0]
[17179603.680000] ACPI: Power Button (CM) [PWRB]
[17179603.852000] ibm_acpi: ec object not found
[17179603.884000] pcc_acpi: loading...
[17179603.908000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[17179604.012000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179606.112000] NET: Registered protocol family 10
[17179606.112000] lo: Disabled Privacy Extensions
[17179606.112000] IPv6 over IPv4 tunneling driver
[17179607.348000] [drm] Initialized drm 1.0.1 20051102
[17179607.352000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179607.352000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179607.352000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179608.788000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179608.788000] apm: overridden by ACPI.
[17179615.036000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[17179615.036000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[17179615.036000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[17179615.036000] sonypi: device allocated minor is 61
[17179615.080000] input: Sony Vaio Jogdial as /class/input/input4
[17179615.108000] input: Sony Vaio Keys as /class/input/input5
[17179615.572000] Bluetooth: L2CAP ver 2.8
[17179615.572000] Bluetooth: L2CAP socket layer initialized
[17179615.656000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179615.704000] Bluetooth: RFCOMM socket layer initialized
[17179615.704000] Bluetooth: RFCOMM TTY layer initialized
[17179615.704000] Bluetooth: RFCOMM ver 1.7
[17179616.332000] eth1: no IPv6 routers present

```

---

### Post by fastluck on 2006-11-14
I see a lot of these posts, and not too many solutions.  As you can see [here,]("http://ubuntuforums.org/showthread.php?p=609310#post609310") I solved this problem for 4.10.  But the solution doesn't work for Edgy even though it's supposed to.  I'm sure it's something I just don't know.  Kind of like having to turn off proxy in order to get apt to work if you don't have a proxy server defined. 

If someone knows the simple answer, please post it here.

Thanks,

Fastluck

---

