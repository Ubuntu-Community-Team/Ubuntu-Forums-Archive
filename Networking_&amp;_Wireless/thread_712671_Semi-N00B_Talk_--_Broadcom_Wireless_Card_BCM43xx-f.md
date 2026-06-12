---
title: "Semi-N00B Talk -- Broadcom Wireless Card BCM43xx-fwcutter says it's working; no net."
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Aryeh113 on 2008-03-01
Hey, I have a compaq presario v6500z CTO, with a broadcom wireless card, I think a BCMWL6, and my internet was not working, so I installed BCM43xx-fwcutter. It says that the device is active, and my network light is on, but I cannot connect to anything, even if I set the connection up manually. Please help, I've been trying to fix my internet for, like, three months.

---

### Post by Iandefor on 2008-03-01
Can you post the output of
```
lspci
```And ```
dmesg | grep bcm
```Please?

---

### Post by Aryeh113 on 2008-03-03
lspci:

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2) 
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2) 
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2) 
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2) 
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2) 
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) 
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) 
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) 
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) 
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1) 
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1) 
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2) 
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2) 
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2) 
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) 
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) 
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)


dmesg grep bcm: (get ready for a big one)

[   23.686527] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
[   23.686533] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   23.686543] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126] 
[   23.686553] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126] 
[   23.686561] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126] 
[   23.687573] ACPI Exception (thermal-0311): AE_BAD_DATA, No critical threshold [20070126] 
[   24.267875] usbcore: registered new interface driver usbfs 
[   24.267898] usbcore: registered new interface driver hub 
[   24.267916] usbcore: registered new device driver usb 
[   24.268607] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[   24.268984] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18 
[   24.268994] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 18 (level, low) -> IRQ 16 
[   24.269005] PCI: Setting latency timer of device 0000:00:02.0 to 64 
[   24.269008] ohci_hcd 0000:00:02.0: OHCI Host Controller 
[   24.269152] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1 
[   24.269169] ohci_hcd 0000:00:02.0: irq 16, io mem 0xf6486000 
[   24.328459] usb usb1: configuration #1 chosen from 1 choice 
[   24.328487] hub 1-0:1.0: USB hub found 
[   24.328496] hub 1-0:1.0: 7 ports detected 
[   24.358868] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   24.358874] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   24.377239] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60. 
[   24.428795] ACPI: PCI Interrupt Link [Z015] enabled at IRQ 18 
[   24.428800] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z015] -> GSI 18 (level, low) -> IRQ 16 
[   24.428813] PCI: Setting latency timer of device 0000:00:04.0 to 64 
[   24.428816] ohci_hcd 0000:00:04.0: OHCI Host Controller 
[   24.428837] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2 
[   24.428849] ohci_hcd 0000:00:04.0: irq 16, io mem 0xf6487000 
[   24.463572] SCSI subsystem initialized 
[   24.467886] libata version 2.21 loaded. 
[   24.486402] usb usb2: configuration #1 chosen from 1 choice 
[   24.486431] hub 2-0:1.0: USB hub found 
[   24.486440] hub 2-0:1.0: 2 ports detected 
[   24.588770] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22 
[   24.588782] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 17 
[   24.588794] PCI: Setting latency timer of device 0000:00:02.1 to 64 
[   24.588797] ehci_hcd 0000:00:02.1: EHCI Host Controller 
[   24.588831] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3 
[   24.588857] ehci_hcd 0000:00:02.1: debug port 1 
[   24.588861] PCI: cache line size of 64 is not supported by device 0000:00:02.1 
[   24.588872] ehci_hcd 0000:00:02.1: irq 17, io mem 0xf6489000 
[   24.588880] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   24.588946] usb usb3: configuration #1 chosen from 1 choice 
[   24.588970] hub 3-0:1.0: USB hub found 
[   24.588977] hub 3-0:1.0: 7 ports detected 
[   24.692293] ACPI: PCI Interrupt Link [Z016] enabled at IRQ 22 
[   24.692298] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z016] -> GSI 22 (level, low) -> IRQ 17 
[   24.692311] PCI: Setting latency timer of device 0000:00:04.1 to 64 
[   24.692314] ehci_hcd 0000:00:04.1: EHCI Host Controller 
[   24.692336] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4 
[   24.692361] ehci_hcd 0000:00:04.1: debug port 1 
[   24.692365] PCI: cache line size of 64 is not supported by device 0000:00:04.1 
[   24.692371] ehci_hcd 0000:00:04.1: irq 17, io mem 0xf6489400 
[   24.692379] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   24.692440] usb usb4: configuration #1 chosen from 1 choice 
[   24.692461] hub 4-0:1.0: USB hub found 
[   24.692467] hub 4-0:1.0: 2 ports detected 
[    3.864000] Marking TSC unstable due to: possible TSC halt in C2. 
[    3.888000] Time: hpet clocksource has been installed. 
[    3.956000] NFORCE-MCP67: IDE controller at PCI slot 0000:00:06.0 
[    3.956000] NFORCE-MCP67: chipset revision 161 
[    3.956000] NFORCE-MCP67: not 100% native mode: will probe irqs later 
[    3.956000] NFORCE-MCP67: BIOS didn't set cable bits correctly. Enabling workaround. 
[    3.956000] NFORCE-MCP67: 0000:00:06.0 (rev a1) UDMA133 controller 
[    3.956000]     ide0: BM-DMA at 0x30c0-0x30c7, BIOS settings: hda:DMA, hdb:pio 
[    3.956000] Probing IDE interface ide0... 
[    4.692000] hda: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive 
[    5.028000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14 
[    5.032000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20 
[    5.032000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 18 
[    5.032000] PCI: Setting latency timer of device 0000:00:0a.0 to 64 
[    5.032000] forcedeth: using HIGHDMA 
[    5.032000] 0000:00:0a.0: Invalid Mac address detected: 1f:c4:9e:24:1b:00 
[    5.032000] Please complain to your hardware vendor. Switching to a random MAC. 
[    5.552000] eth0: forcedeth.c: subsystem: 0103c:30cf bound to 0000:00:0a.0 
[    5.556000] ahci 0000:00:09.0: version 2.2 
[    5.556000] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23 
[    5.556000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 19 
[    5.564000] hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA 
[    5.564000] Uniform CD-ROM driver Revision: 3.20 
[    6.560000] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode 
[    6.560000] ahci 0000:00:09.0: flags: 64bit led clo pmp pio slum part  
[    6.560000] PCI: Setting latency timer of device 0000:00:09.0 to 64 
[    6.560000] scsi0 : ahci 
[    6.560000] scsi1 : ahci 
[    6.560000] scsi2 : ahci 
[    6.560000] scsi3 : ahci 
[    6.560000] ata1: SATA max UDMA/133 cmd 0xf887c100 ctl 0x00000000 bmdma 0x00000000 irq 19 
[    6.560000] ata2: SATA max UDMA/133 cmd 0xf887c180 ctl 0x00000000 bmdma 0x00000000 irq 19 
[    6.560000] ata3: SATA max UDMA/133 cmd 0xf887c200 ctl 0x00000000 bmdma 0x00000000 irq 19 
[    6.560000] ata4: SATA max UDMA/133 cmd 0xf887c280 ctl 0x00000000 bmdma 0x00000000 irq 19 
[    7.044000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    7.044000] ata1.00: ATA-7: TOSHIBA MK8037GSX, DL232C, max UDMA/100 
[    7.044000] ata1.00: 156301488 sectors, multi 16: LBA48  
[    7.044000] ata1.00: configured for UDMA/100 
[    7.356000] ata2: SATA link down (SStatus 0 SControl 300) 
[    7.668000] ata3: SATA link down (SStatus 0 SControl 300) 
[    7.980000] ata4: SATA link down (SStatus 0 SControl 300) 
[    7.980000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8037GS DL23 PQ: 0 ANSI: 5 
[    7.980000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5 
[    7.980000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5 
[    8.032000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4] 
[    8.048000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    8.048000] sd 0:0:0:0: [sda] Write Protect is off 
[    8.048000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    8.048000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    8.048000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    8.048000] sd 0:0:0:0: [sda] Write Protect is off 
[    8.048000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    8.048000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    8.048000]  sda: sda1 sda2 
[    8.116000] sd 0:0:0:0: [sda] Attached SCSI disk 
[    8.120000] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    8.408000] kjournald starting.  Commit interval 5 seconds 
[    8.408000] EXT3-fs: mounted filesystem with ordered data mode. 
[    9.308000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00250f5b00] 
[   18.160000] sdhci: Secure Digital Host Controller Interface driver 
[   18.160000] sdhci: Copyright(c) Pierre Ossman 
[   18.160000] sdhci: SDHCI controller found at 0000:02:05.1 [1180:0822] (rev 22) 
[   18.160000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7 
[   18.160000] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNK2] -> GSI 7 (level, low) -> IRQ 7 
[   18.160000] mmc0: SDHCI at 0xf6100800 irq 7 DMA 
[   18.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   18.192000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   18.500000] Linux agpgart interface v0.102 (c) Dave Jones 
[   18.608000] input: PC Speaker as /class/input/input2 
[   18.744000] ieee80211_crypt: registered algorithm 'NULL' 
[   18.748000] ieee80211: 802.11 data/management/control stack, git-1.1.13 
[   18.748000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
[   18.856000] bcm43xx driver 
[   18.868000] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19 
[   18.868000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 20 
[   18.868000] PCI: Setting latency timer of device 0000:03:00.0 to 64 
[   18.872000] bcm43xx: Unsupported 80211 core revision 13 
[   18.876000] bcm43xx: Invalid PHY Revision 9 
[   19.128000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21 
[   19.128000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21 
[   19.128000] PCI: Setting latency timer of device 0000:00:07.0 to 64 
[   19.308000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000 
[   19.388000] input: SynPS/2 Synaptics TouchPad as /class/input/input3 
[   19.880000] lp: driver loaded but no devices found 
[   20.396000] EXT3 FS on sda2, internal journal 
[   22.184000] ACPI: AC Adapter [ACAD] (off-line) 
[   22.208000] ACPI: Battery Slot [BAT0] (battery present) 
[   22.224000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no) 
[   22.232000] No dock devices found. 
[   22.312000] input: Power Button (FF) as /class/input/input4 
[   22.316000] ACPI: Power Button (FF) [PWRF] 
[   22.348000] input: Sleep Button (CM) as /class/input/input5 
[   22.352000] ACPI: Sleep Button (CM) [SLPB] 
[   22.388000] input: Lid Switch as /class/input/input6 
[   22.392000] ACPI: Lid Switch [LID] 
[   22.424000] input: Power Button (CM) as /class/input/input7 
[   22.432000] ACPI: Power Button (CM) [PWRB] 
[   22.716000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3600+ processors (version 2.00.00) 
[   22.716000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10 
[   22.716000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x11 
[   22.716000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x12 
[   22.716000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18 
[   23.832000] ppdev: user-space parallel port driver 
[   24.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   24.520000] eth15: no link during initialization. 
[   24.592000] bcm43xx: MAC suspend failed 
[   24.636000] bcm43xx: MAC suspend failed 
[   24.668000] audit(1204498805.882:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4951 profile="/usr/sbin/cupsd" 
[   24.672000] bcm43xx: MAC suspend failed 
[   24.708000] bcm43xx: MAC suspend failed 
[   24.744000] bcm43xx: MAC suspend failed 
[   24.764000] apm: BIOS not found. 
[   24.780000] bcm43xx: MAC suspend failed 
[   24.816000] bcm43xx: MAC suspend failed 
[   24.852000] bcm43xx: MAC suspend failed 
[   25.068000] Failure registering capabilities with primary security module. 
[   25.280000] Bluetooth: Core ver 2.11 
[   25.280000] NET: Registered protocol family 31 
[   25.280000] Bluetooth: HCI device and connection manager initialized 
[   25.280000] Bluetooth: HCI socket layer initialized 
[   25.296000] Bluetooth: L2CAP ver 2.8 
[   25.296000] Bluetooth: L2CAP socket layer initialized 
[   25.368000] Bluetooth: RFCOMM socket layer initialized 
[   25.368000] Bluetooth: RFCOMM TTY layer initialized 
[   25.368000] Bluetooth: RFCOMM ver 1.8 
[   26.000000] Clocksource tsc unstable (delta = -163165351 ns) 
[   54.472000] bcm43xx: MAC suspend failed 
[   54.512000] bcm43xx: MAC suspend failed 
[   54.552000] bcm43xx: MAC suspend failed 
[   54.588000] bcm43xx: MAC suspend failed 
[   54.624000] bcm43xx: MAC suspend failed 
[   54.660000] bcm43xx: MAC suspend failed 
[   54.696000] bcm43xx: MAC suspend failed 
[   84.444000] printk: 6 messages suppressed. 
[   84.444000] bcm43xx: MAC suspend failed 
[   84.456000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   84.456000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   84.456000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   84.456000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   84.456000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   89.428000] printk: 237123 messages suppressed. 
[   89.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   94.428000] printk: 251740 messages suppressed. 
[   94.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[   99.428000] printk: 251914 messages suppressed. 
[   99.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  104.428000] printk: 251405 messages suppressed. 
[  104.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  109.428000] printk: 251676 messages suppressed. 
[  109.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  114.428000] printk: 251713 messages suppressed. 
[  114.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  119.428000] printk: 238552 messages suppressed. 
[  119.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  124.428000] printk: 251503 messages suppressed. 
[  124.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  129.428000] printk: 251894 messages suppressed. 
[  129.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  134.428000] printk: 251752 messages suppressed. 
[  134.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  139.428000] printk: 251732 messages suppressed. 
[  139.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  144.428000] printk: 251886 messages suppressed. 
[  144.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  149.428000] printk: 237498 messages suppressed. 
[  149.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  154.428000] printk: 252011 messages suppressed. 
[  154.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  159.428000] printk: 250508 messages suppressed. 
[  159.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  164.456000] printk: 237639 messages suppressed. 
[  164.456000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  169.428000] printk: 276255 messages suppressed. 
[  169.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  174.428000] printk: 295336 messages suppressed. 
[  174.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  179.428000] printk: 292788 messages suppressed. 
[  179.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  184.428000] printk: 293560 messages suppressed. 
[  184.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  189.428000] printk: 289183 messages suppressed. 
[  189.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  194.428000] printk: 292150 messages suppressed. 
[  194.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  199.428000] printk: 292759 messages suppressed. 
[  199.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  204.428000] printk: 291668 messages suppressed. 
[  204.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  209.428000] printk: 286899 messages suppressed. 
[  209.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  214.428000] printk: 288308 messages suppressed. 
[  214.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  219.428000] printk: 289438 messages suppressed. 
[  219.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  224.428000] printk: 285224 messages suppressed. 
[  224.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  229.428000] printk: 289422 messages suppressed. 
[  229.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  234.428000] printk: 287428 messages suppressed. 
[  234.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  239.428000] printk: 289999 messages suppressed. 
[  239.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  244.428000] printk: 292196 messages suppressed. 
[  244.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  249.428000] printk: 291163 messages suppressed. 
[  249.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  254.428000] printk: 284872 messages suppressed. 
[  254.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  259.428000] printk: 286626 messages suppressed. 
[  259.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  259.568000] usb 3-2: new high speed USB device using ehci_hcd and address 2 
[  259.704000] usb 3-2: configuration #1 chosen from 1 choice 
[  260.564000] usbcore: registered new interface driver libusual 
[  261.668000] Initializing USB Mass Storage driver... 
[  261.684000] scsi4 : SCSI emulation for USB Mass Storage devices 
[  261.716000] usb-storage: device found at 2 
[  261.716000] usb-storage: waiting for device to settle before scanning 
[  261.720000] usbcore: registered new interface driver usb-storage 
[  261.720000] USB Mass Storage support registered. 
[  264.428000] printk: 278267 messages suppressed. 
[  264.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  266.716000] usb-storage: device scan complete 
[  266.732000] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.1  PQ: 0 ANSI: 2 
[  266.768000] sd 4:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB) 
[  266.772000] sd 4:0:0:0: [sdb] Write Protect is off 
[  266.772000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00 
[  266.772000] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
[  266.784000] sd 4:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB) 
[  266.788000] sd 4:0:0:0: [sdb] Write Protect is off 
[  266.792000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00 
[  266.792000] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
[  266.792000]  sdb: sdb1 
[  266.800000] sd 4:0:0:0: [sdb] Attached SCSI removable disk 
[  266.804000] sd 4:0:0:0: Attached scsi generic sg1 type 0 
[  269.428000] printk: 285218 messages suppressed. 
[  269.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  274.428000] printk: 290292 messages suppressed. 
[  274.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  279.428000] printk: 268468 messages suppressed. 
[  279.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  284.428000] printk: 286321 messages suppressed. 
[  284.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  289.428000] printk: 290416 messages suppressed. 
[  289.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  294.428000] printk: 290956 messages suppressed. 
[  294.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  299.428000] printk: 291024 messages suppressed. 
[  299.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  304.428000] printk: 293273 messages suppressed. 
[  304.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  309.428000] printk: 292132 messages suppressed. 
[  309.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  314.428000] printk: 282613 messages suppressed. 
[  314.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  319.428000] printk: 283417 messages suppressed. 
[  319.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  324.428000] printk: 283920 messages suppressed. 
[  324.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  329.428000] printk: 286773 messages suppressed. 
[  329.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  334.428000] printk: 283636 messages suppressed. 
[  334.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  339.428000] printk: 290095 messages suppressed. 
[  339.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  344.428000] printk: 284039 messages suppressed. 
[  344.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  349.428000] printk: 286516 messages suppressed. 
[  349.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  354.428000] printk: 291364 messages suppressed. 
[  354.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  359.428000] printk: 296018 messages suppressed. 
[  359.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  364.428000] printk: 289234 messages suppressed. 
[  364.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  369.428000] printk: 287220 messages suppressed. 
[  369.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  374.428000] printk: 296140 messages suppressed. 
[  374.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  379.428000] printk: 299971 messages suppressed. 
[  379.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  384.428000] printk: 289676 messages suppressed. 
[  384.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  389.428000] printk: 287928 messages suppressed. 
[  389.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  394.428000] printk: 293874 messages suppressed. 
[  394.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  399.428000] printk: 289692 messages suppressed. 
[  399.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  404.428000] printk: 291006 messages suppressed. 
[  404.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  409.428000] printk: 283298 messages suppressed. 
[  409.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  414.428000] printk: 295702 messages suppressed. 
[  414.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  419.428000] printk: 291678 messages suppressed. 
[  419.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  424.460000] printk: 218991 messages suppressed. 
[  424.460000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  429.428000] printk: 220512 messages suppressed. 
[  429.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  434.428000] printk: 217685 messages suppressed. 
[  434.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  439.428000] printk: 292734 messages suppressed. 
[  439.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  444.428000] printk: 297253 messages suppressed. 
[  444.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  449.428000] printk: 301331 messages suppressed. 
[  449.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  454.428000] printk: 300534 messages suppressed. 
[  454.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  459.428000] printk: 284726 messages suppressed. 
[  459.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  464.428000] printk: 296004 messages suppressed. 
[  464.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  469.428000] printk: 291224 messages suppressed. 
[  469.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  474.428000] printk: 289702 messages suppressed. 
[  474.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  479.428000] printk: 293136 messages suppressed. 
[  479.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  484.428000] printk: 289610 messages suppressed. 
[  484.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  489.428000] printk: 290026 messages suppressed. 
[  489.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  494.428000] printk: 287011 messages suppressed. 
[  494.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  499.428000] printk: 294823 messages suppressed. 
[  499.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  504.576000] printk: 290186 messages suppressed. 
[  504.576000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  504.576000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away. 
[  507.592000] psmouse.c: failed to re-enable mouse on isa0060/serio1 
[  507.592000] psmouse.c: resync failed, issuing reconnect request 
[  509.428000] printk: 231321 messages suppressed. 
[  509.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  514.428000] printk: 288747 messages suppressed. 
[  514.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  519.428000] printk: 281053 messages suppressed. 
[  519.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  524.428000] printk: 289298 messages suppressed. 
[  524.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  529.428000] printk: 295755 messages suppressed. 
[  529.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  534.428000] printk: 288829 messages suppressed. 
[  534.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  539.428000] printk: 273359 messages suppressed. 
[  539.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  544.428000] printk: 293645 messages suppressed. 
[  544.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  549.428000] printk: 290330 messages suppressed. 
[  549.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  554.428000] printk: 293338 messages suppressed. 
[  554.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  559.428000] printk: 288507 messages suppressed. 
[  559.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  564.428000] printk: 273742 messages suppressed. 
[  564.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  569.428000] printk: 261641 messages suppressed. 
[  569.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  574.428000] printk: 290850 messages suppressed. 
[  574.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  579.428000] printk: 289814 messages suppressed. 
[  579.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  584.428000] printk: 288716 messages suppressed. 
[  584.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  589.428000] printk: 290481 messages suppressed. 
[  589.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  594.428000] printk: 290504 messages suppressed. 
[  594.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  599.428000] printk: 291913 messages suppressed. 
[  599.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  604.428000] printk: 284799 messages suppressed. 
[  604.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  609.428000] printk: 285836 messages suppressed. 
[  609.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  614.428000] printk: 285895 messages suppressed. 
[  614.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  619.428000] printk: 283922 messages suppressed. 
[  619.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  624.428000] printk: 295979 messages suppressed. 
[  624.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  629.428000] printk: 299624 messages suppressed. 
[  629.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  634.428000] printk: 301270 messages suppressed. 
[  634.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  639.428000] printk: 293458 messages suppressed. 
[  639.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  644.428000] printk: 292990 messages suppressed. 
[  644.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  649.428000] printk: 300831 messages suppressed. 
[  649.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  654.428000] printk: 299624 messages suppressed. 
[  654.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
[  659.428000] printk: 300106 messages suppressed. 
[  659.428000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR 
aryeh@aryeh-laptop:~$  
aryeh@aryeh-laptop:~$  
aryeh@aryeh-laptop:~$  
 


Usage: dmesg [-c] [-n level] [-s bufsize]

THanks a lot for the help!

---

### Post by sillyxone on 2008-03-04
can you try ndiswrapper instead. I had problem with bcm43xx driver too, but ndiswrapper never failed me.

look here for instruction:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

the version of ndiswrapper from Synaptic works fine. Also, it's best if you could find the Windows driver that work for your card.

---

### Post by Iandefor on 2008-03-04
Well, if you're still interested in working with the bcm43xx driver, can you post the output cat /proc/interrupts ?

---

