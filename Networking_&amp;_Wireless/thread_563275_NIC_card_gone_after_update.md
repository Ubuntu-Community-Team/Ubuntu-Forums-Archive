---
title: "NIC card gone after update"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by mdoyle on 2007-09-29
This is not my first install of Gutsy. I had it previously installed on this machine and after a hard drive crash, i'm reinstalling it. I installed Gutys, then went to download the nvidia drivers. After they were installed and the computer was restart my NIC card is gone. It's not in Network Tools or anywhere else that I can see.

It is an Intel onboard NIC card. It worked fine prior to the update. Any ideas on where I should start?

---

### Post by mdoyle on 2007-09-30
bump

---

### Post by mdoyle on 2007-09-30
After a bit of research i found the lshw -C network command. It tells me that both my connections (wired and wireless) are unclaimed. They were both there and working prior to the kernel upgrade.

---

### Post by mdoyle on 2007-09-30
bump

---

### Post by noob12 on 2007-09-30
Can you get the output of the **dmesg** command and post that?  It may provide clues about why those devices remain unclaimed.  (You may need a USB drive to get text off the box.)

---

### Post by mdoyle on 2007-10-02
```
[   69.089776] assign_interrupt_mode Found MSI capability
[   69.089799] Allocate Port Service[0000:00:1c.0:pcie00]
[   69.089816] Allocate Port Service[0000:00:1c.0:pcie02]
[   69.089867] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   69.089895] assign_interrupt_mode Found MSI capability
[   69.089918] Allocate Port Service[0000:00:1c.1:pcie00]
[   69.089936] Allocate Port Service[0000:00:1c.1:pcie02]
[   69.089985] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   69.090014] assign_interrupt_mode Found MSI capability
[   69.090037] Allocate Port Service[0000:00:1c.2:pcie00]
[   69.090053] Allocate Port Service[0000:00:1c.2:pcie02]
[   69.090102] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   69.090131] assign_interrupt_mode Found MSI capability
[   69.090154] Allocate Port Service[0000:00:1c.3:pcie00]
[   69.090170] Allocate Port Service[0000:00:1c.3:pcie02]
[   69.090220] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   69.090249] assign_interrupt_mode Found MSI capability
[   69.090271] Allocate Port Service[0000:00:1c.4:pcie00]
[   69.090288] Allocate Port Service[0000:00:1c.4:pcie02]
[   69.090389] isapnp: Scanning for PnP cards...
[   69.138497] Switched to high resolution mode on CPU 0
[   69.442912] isapnp: No Plug & Play device found
[   69.453944] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   69.454027] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   69.454420] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   69.454750] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   69.454852] input: Macintosh mouse button emulation as /class/input/input0
[   69.454892] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   69.454893] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   69.457908] serio: i8042 KBD port at 0x60,0x64 irq 1
[   69.457910] serio: i8042 AUX port at 0x60,0x64 irq 12
[   69.457986] mice: PS/2 mouse device common for all mice
[   69.458038] EISA: Probing bus 0 at eisa.0
[   69.458043] Cannot allocate resource for EISA slot 1
[   69.458044] Cannot allocate resource for EISA slot 2
[   69.458045] Cannot allocate resource for EISA slot 3
[   69.458047] Cannot allocate resource for EISA slot 4
[   69.458057] EISA: Detected 0 cards.
[   69.458107] TCP cubic registered
[   69.458115] NET: Registered protocol family 1
[   69.458128] Using IPI Shortcut mode
[   69.458230]   Magic number: 11:924:431
[   69.458375] Freeing unused kernel memory: 352k freed
[   69.511148] input: AT Translated Set 2 keyboard as /class/input/input1
[   70.611629] Capability LSM initialized
[   70.654250] Monitor-Mwait will be used to enter C-1 state
[   70.654253] ACPI: Processor [CPU0] (supports 8 throttling states)
[   71.053545] usbcore: registered new interface driver usbfs
[   71.053558] usbcore: registered new interface driver hub
[   71.053569] usbcore: registered new device driver usb
[   71.053986] USB Universal Host Controller Interface driver v3.0
[   71.054024] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 18 (level, low) -> IRQ 19
[   71.054031] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   71.054034] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   71.054126] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   71.054147] uhci_hcd 0000:00:1a.0: irq 19, io base 0x000040e0
[   71.054209] usb usb1: configuration #1 chosen from 1 choice
[   71.054224] hub 1-0:1.0: USB hub found
[   71.054227] hub 1-0:1.0: 2 ports detected
[   71.135273] SCSI subsystem initialized
[   71.138361] libata version 2.21 loaded.
[   71.155151] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   71.155159] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   71.155161] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   71.155175] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   71.155196] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000040c0
[   71.155252] usb usb2: configuration #1 chosen from 1 choice
[   71.155267] hub 2-0:1.0: USB hub found
[   71.155270] hub 2-0:1.0: 2 ports detected
[   71.247882] Floppy drive(s): fd0 is 1.44M
[   71.258975] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 17 (level, low) -> IRQ 17
[   71.258981] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   71.258984] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   71.258997] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   71.259017] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000040a0
[   71.259071] usb usb3: configuration #1 chosen from 1 choice
[   71.259086] hub 3-0:1.0: USB hub found
[   71.259089] hub 3-0:1.0: 2 ports detected
[   71.270221] FDC 0 is a post-1991 82077
[   71.362836] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 22
[   71.362844] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   71.362847] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   71.362865] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   71.362887] uhci_hcd 0000:00:1d.0: irq 22, io base 0x00004080
[   71.362963] usb usb4: configuration #1 chosen from 1 choice
[   71.362984] hub 4-0:1.0: USB hub found
[   71.362989] hub 4-0:1.0: 2 ports detected
[   71.394718] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   71.466663] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   71.466669] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   71.466672] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   71.466689] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   71.466710] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00004060
[   71.466789] usb usb5: configuration #1 chosen from 1 choice
[   71.466810] hub 5-0:1.0: USB hub found
[   71.466815] hub 5-0:1.0: 2 ports detected
[   71.570502] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   71.570509] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   71.570512] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   71.570529] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   71.570549] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00004040
[   71.570624] usb usb6: configuration #1 chosen from 1 choice
[   71.570646] hub 6-0:1.0: USB hub found
[   71.570651] hub 6-0:1.0: 2 ports detected
[   71.645323] usb 1-1: configuration #1 chosen from 1 choice
[   71.675325] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 17 (level, low) -> IRQ 17
[   71.675331] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   71.675334] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   71.675348] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   71.675369] ehci_hcd 0000:00:1a.7: debug port 1
[   71.675373] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   71.675376] ehci_hcd 0000:00:1a.7: irq 17, io mem 0x92225c00
[   71.679261] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   71.679310] usb usb7: configuration #1 chosen from 1 choice
[   71.679325] hub 7-0:1.0: USB hub found
[   71.679329] hub 7-0:1.0: 6 ports detected
[   71.782185] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 22
[   71.782196] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   71.782199] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   71.782218] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   71.782243] ehci_hcd 0000:00:1d.7: debug port 1
[   71.782248] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   71.782253] ehci_hcd 0000:00:1d.7: irq 22, io mem 0x92225800
[   71.786126] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   71.786170] usb usb8: configuration #1 chosen from 1 choice
[   71.786185] hub 8-0:1.0: USB hub found
[   71.786189] hub 8-0:1.0: 6 ports detected
[   71.890064] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   71.890088] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   71.890131] scsi0 : pata_marvell
[   71.890158] scsi1 : pata_marvell
[   71.890181] ata1: PATA max UDMA/100 cmd 0x00012018 ctl 0x00012026 bmdma 0x00012000 irq 17
[   71.890184] ata2: DUMMY
[   71.890209] BAR5:00:00 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:01 0D:00 0E:00 0F:00 
[   72.229860] ata1.01: ATAPI: HL-DT-STDVDRRW GCA-4166B, 1.08, max UDMA/44
[   72.401590] ata1.01: configured for UDMA/44
[   72.403057] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRRW GCA-4166B 1.08 PQ: 0 ANSI: 5
[   72.404846] ahci 0000:00:1f.2: version 2.2
[   72.404858] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 21 (level, low) -> IRQ 21
[   72.656784] usb 1-1: USB disconnect, address 2
[   72.896386] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   73.148029] usb 1-1: configuration #1 chosen from 1 choice
[   73.391617] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   73.403619] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   73.403622] ahci 0000:00:1f.2: flags: 64bit ncq led clo pmp pio slum part 
[   73.403626] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   73.403862] scsi2 : ahci
[   73.403887] scsi3 : ahci
[   73.403903] scsi4 : ahci
[   73.403920] scsi5 : ahci
[   73.403937] scsi6 : ahci
[   73.403952] scsi7 : ahci
[   73.404008] ata3: SATA max UDMA/133 cmd 0xf8896100 ctl 0x00000000 bmdma 0x00000000 irq 217
[   73.404010] ata4: SATA max UDMA/133 cmd 0xf8896180 ctl 0x00000000 bmdma 0x00000000 irq 217
[   73.404013] ata5: SATA max UDMA/133 cmd 0xf8896200 ctl 0x00000000 bmdma 0x00000000 irq 217
[   73.404015] ata6: SATA max UDMA/133 cmd 0xf8896280 ctl 0x00000000 bmdma 0x00000000 irq 217
[   73.404017] ata7: SATA max UDMA/133 cmd 0xf8896300 ctl 0x00000000 bmdma 0x00000000 irq 217
[   73.404020] ata8: SATA max UDMA/133 cmd 0xf8896380 ctl 0x00000000 bmdma 0x00000000 irq 217
[   73.576553] usb 3-1: configuration #1 chosen from 1 choice
[   73.579514] hub 3-1:1.0: USB hub found
[   73.582484] hub 3-1:1.0: 3 ports detected
[   73.886850] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   73.930787] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   74.104310] ata3.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[   74.104313] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   74.120720] usb 3-2: configuration #1 chosen from 1 choice
[   74.162527] ata3.00: configured for UDMA/133
[   74.327347] usb 3-1.2: new full speed USB device using uhci_hcd and address 4
[   74.480166] usb 3-1.2: configuration #1 chosen from 1 choice
[   74.645672] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   74.649246] ata4.00: ATA-7: Maxtor 6B250R0, BAH41B70, max UDMA/133
[   74.649249] ata4.00: 490234752 sectors, multi 0: LBA48 
[   74.649251] ata4.00: applying bridge limits
[   74.654313] ata4.00: configured for UDMA/100
[   74.686796] usb 3-1.3: new full speed USB device using uhci_hcd and address 5
[   74.839621] usb 3-1.3: configuration #1 chosen from 1 choice
[   74.846558] usbcore: registered new interface driver hiddev
[   74.851579] input: Logitech Logitech BT Mini-Receiver as /class/input/input2
[   74.851585] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.2-1.2
[   74.860597] input: Logitech Logitech BT Mini-Receiver as /class/input/input3
[   74.860638] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.2-1.3
[   74.860646] usbcore: registered new interface driver usbhid
[   74.860648] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   74.965176] ata5: SATA link down (SStatus 0 SControl 300)
[   75.276691] ata6: SATA link down (SStatus 0 SControl 300)
[   75.759942] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   75.760424] ata7.00: ATA-7: WDC WD1600JS-60MHB1, 10.02E02, max UDMA/100
[   75.760427] ata7.00: 312581808 sectors, multi 0: LBA48 
[   75.760981] ata7.00: configured for UDMA/100
[   76.071458] ata8: SATA link down (SStatus 0 SControl 300)
[   76.071541] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[   76.071794] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6B250R0   BAH4 PQ: 0 ANSI: 5
[   76.071983] scsi 6:0:0:0: Direct-Access     ATA      WDC WD1600JS-60M 10.0 PQ: 0 ANSI: 5
[   76.072768] ACPI: PCI Interrupt 0000:07:03.0[A] -> GSI 19 (level, low) -> IRQ 20
[   76.123221] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[92006000-920067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   76.133082] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   76.133090] sd 2:0:0:0: [sda] Write Protect is off
[   76.133091] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   76.133098] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.133123] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   76.133128] sd 2:0:0:0: [sda] Write Protect is off
[   76.133129] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   76.133136] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.133139]  sda:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   76.141512] Uniform CD-ROM driver Revision: 3.20
[   76.141632] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   76.148336]  sda1 sda2 sda3
[   76.148672] sd 2:0:0:0: [sda] Attached SCSI disk
[   76.148754] sd 3:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   76.148759] sd 3:0:0:0: [sdb] Write Protect is off
[   76.148761] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   76.148768] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.148788] sd 3:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   76.148793] sd 3:0:0:0: [sdb] Write Protect is off
[   76.148795] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   76.148802] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.148803]  sdb: sdb1 sdb2 sdb3
[   76.193645] sd 3:0:0:0: [sdb] Attached SCSI disk
[   76.193729] sd 6:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   76.193735] sd 6:0:0:0: [sdc] Write Protect is off
[   76.193736] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   76.193743] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.193765] sd 6:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   76.193770] sd 6:0:0:0: [sdc] Write Protect is off
[   76.193771] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   76.193778] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.193780]  sdc: sdc1
[   76.220558] sd 6:0:0:0: [sdc] Attached SCSI disk
[   76.222909] sr 0:0:1:0: Attached scsi generic sg0 type 5
[   76.222988] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   76.223073] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   76.223154] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   76.464673] Attempting manual resume
[   76.464675] swsusp: Resume From Partition 8:19
[   76.464676] PM: Checking swsusp image.
[   76.464794] PM: Resume from disk failed.
[   76.472776] EXT3-fs: INFO: recovery required on readonly filesystem.
[   76.472779] EXT3-fs: write access will be enabled during recovery.
[   77.389496] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001e0444f]
[   77.993478] kjournald starting.  Commit interval 5 seconds
[   77.993486] EXT3-fs: sdb2: orphan cleanup on readonly fs
[   77.993491] ext3_orphan_cleanup: deleting unreferenced inode 4210887
[   77.993511] EXT3-fs: sdb2: 1 orphan inode deleted
[   77.993513] EXT3-fs: recovery complete.
[   77.995162] EXT3-fs: mounted filesystem with ordered data mode.
[   87.295316] Linux agpgart interface v0.102 (c) Dave Jones
[   87.334594] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   87.335740] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   87.747246] nvidia: module license 'NVIDIA' taints kernel.
[   88.018546] Bluetooth: Core ver 2.11
[   88.018574] NET: Registered protocol family 31
[   88.018576] Bluetooth: HCI device and connection manager initialized
[   88.018577] Bluetooth: HCI socket layer initialized
[   88.041799] Bluetooth: HCI USB driver ver 2.9
[   88.043323] usbcore: registered new interface driver hci_usb
[   88.046816] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   88.046822] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   88.046886] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   88.229780] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1017
[   88.229791] usbcore: registered new interface driver usblp
[   88.229794] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   88.663021] input: PC Speaker as /class/input/input4
[   88.766365] Real Time Clock Driver v1.12ac
[   89.452764] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   90.418977] fuse init (API version 7.8)
[   90.465768] lp: driver loaded but no devices found
[   90.521119] Adding 1156672k swap on /dev/sdb3.  Priority:-1 extents:1 across:1156672k
[   91.086217] EXT3 FS on sdb2, internal journal
[   92.220417] input: Power Button (FF) as /class/input/input5
[   92.222346] ACPI: Power Button (FF) [PWRF]
[   92.241408] input: Sleep Button (CM) as /class/input/input6
[   92.243285] ACPI: Sleep Button (CM) [SLPB]
[   92.252471] No dock devices found.
[   93.334135] ppdev: user-space parallel port driver
[   94.343727] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   94.343729] apm: overridden by ACPI.
[   94.492462] Capability LSM initialized
[   94.668344] Bluetooth: L2CAP ver 2.8
[   94.668347] Bluetooth: L2CAP socket layer initialized
[   94.741420] Bluetooth: RFCOMM socket layer initialized
[   94.741485] Bluetooth: RFCOMM TTY layer initialized
[   94.741486] Bluetooth: RFCOMM ver 1.8
[   94.838472] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.838483]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.838498]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.838504]  [<c0166ce9>] __slab_alloc+0x239/0x3d0
[   94.838513]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.838521]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.838530]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.838534]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.838538]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.838544]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.838549]  [<c0169030>] do_filp_open+0x50/0x60
[   94.838557]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.838563]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.838567]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.838573]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.838578]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.838584]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.838590]  =======================
[   94.838592] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.838596]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.838608]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.838613]  [<c0166ce9>] __slab_alloc+0x239/0x3d0
[   94.838620]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.838637]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.838643]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.838645]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.838648]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.838652]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.838655]  [<c0169030>] do_filp_open+0x50/0x60
[   94.838660]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.838664]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.838667]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.838670]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.838674]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.838678]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.838681]  =======================
[   94.838683] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.838685]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.838693]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.838696]  [<c0166ce9>] __slab_alloc+0x239/0x3d0
[   94.838701]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.838706]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.838712]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.838714]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.838717]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.838720]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.838723]  [<c0169030>] do_filp_open+0x50/0x60
[   94.838729]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.838733]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.838736]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.838739]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.838742]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.838746]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.838750]  =======================
[   94.844056] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.844062]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.844071]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.844078]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.844081]  [<c012db20>] autoremove_wake_function+0x0/0x50
[   94.844085]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.844091]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.844093]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.844096]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.844099]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.844103]  [<c0169030>] do_filp_open+0x50/0x60
[   94.844108]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.844112]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.844115]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.844118]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.844122]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.844126]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.844129]  =======================
[   94.844131] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.844133]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.844141]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.844147]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.844151]  [<c012db20>] autoremove_wake_function+0x0/0x50
[   94.844154]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.844160]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.844162]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.844165]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.844169]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.844172]  [<c0169030>] do_filp_open+0x50/0x60
[   94.844177]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.844181]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.844184]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.844187]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.844190]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.844194]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.844198]  =======================
[   94.847731] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.847736]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.847745]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.847751]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.847754]  [<c012db20>] autoremove_wake_function+0x0/0x50
[   94.847758]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.847764]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.847766]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.847769]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.847772]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.847775]  [<c0169030>] do_filp_open+0x50/0x60
[   94.847781]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.847785]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.847788]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.847791]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.847795]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.847799]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.847802]  =======================
[   94.847804] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.847806]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.847814]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.847820]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.847824]  [<c012db20>] autoremove_wake_function+0x0/0x50
[   94.847827]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.847833]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.847835]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.847838]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.847842]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.847844]  [<c0169030>] do_filp_open+0x50/0x60
[   94.847850]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.847854]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.847857]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.847860]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.847863]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.847867]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.847871]  =======================
[   94.847872] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   94.847874]  [<f88f3628>] hid_output_report+0x2a8/0x320 [hid]
[   94.847883]  [<f88fb488>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   94.847889]  [<f88fb797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
[   94.847892]  [<c012db20>] autoremove_wake_function+0x0/0x50
[   94.847896]  [<f88fde46>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   94.847901]  [<c0118441>] kunmap_atomic+0x51/0x90
[   94.847904]  [<c011844d>] kunmap_atomic+0x5d/0x90
[   94.847907]  [<c0157aa6>] __handle_mm_fault+0x216/0xa00
[   94.847910]  [<c0168fd5>] nameidata_to_filp+0x35/0x40
[   94.847913]  [<c0169030>] do_filp_open+0x50/0x60
[   94.847918]  [<f88fda00>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   94.847922]  [<c0175fd9>] do_ioctl+0x69/0x70
[   94.847925]  [<c017603c>] vfs_ioctl+0x5c/0x260
[   94.847928]  [<c01762b2>] sys_ioctl+0x72/0x90
[   94.847932]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9
[   94.847936]  [<c02d0000>] __find_acq_core+0x90/0x3a0
[   94.847939]  =======================
[   95.391144] usb 3-1.1: new full speed USB device using uhci_hcd and address 6
[   95.525011] usb 3-1.1: configuration #1 chosen from 1 choice
[  149.829192] NET: Registered protocol family 10
[  149.829381] lo: Disabled Privacy Extensions
[  158.299833] usb 5-2: new low speed USB device using uhci_hcd and address 2
[  158.523592] usb 5-2: configuration #1 chosen from 1 choice
[  158.539610] input: USB Optical Mouse as /class/input/input7
[  158.539635] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2


```

---

### Post by noob12 on 2007-10-02
Unfortunately this excerpt from dmesg leaves off the initial part of the boot

Try a fresh cold boot.   Right after booting, run these commands and post the output:
```

dmesg

lspci -nn

sudo lshw -C network

```

---

### Post by mdoyle on 2007-10-03
dmesg still gives the same amount even after reboot.

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:03.0 Communication controller [0780]: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller [8086:29c4] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82801I (ICH9 Family) Gigabit Ethernet Controller [8086:294c] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller [8086:2912] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller [8086:2922] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7950 GT] [10de:0295] (rev a1)
03:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface [11ab:6101] (rev b1)
07:00.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
07:01.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
07:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
```

sudo lshw -C network
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82801I (ICH9 Family) Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Network controller
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:07:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32

```

---

### Post by noob12 on 2007-10-03
OK.  You have one of the new Intel chips.

Follow this HOWTO to get the driver on your wired interface:  [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

After that ordeal, you can attack the wireless.

---

### Post by Sand Lee on 2007-10-03
Have you updated your NIC's firmware in windows? I had a similar problem that didn't get fixed until i rolled-back the changes from windows update.

---

### Post by mdoyle on 2007-10-03
noob, i'm running kernel 2.6.22-12, those files won't install. What do I do?

Nothing was ever changed in Vista.

---

### Post by noob12 on 2007-10-03
OK.  Somehow missed that.  Also I missed that you were using the net before your nvidia driver update.  Stupid of me.

Does ```
dmesg | grep e1000
``` show anything?  If so can you post that?   Prior posts of your dmesg output were missing everything from the beginning so I couldn't see anything related to this driver loading' maybe you weren't getting what scrolled off-screen.

Try to reload the driver manually:
```

sudo modprobe -r e1000
sudo modprobe e1000

# then see what the kernel said
tail -25 /var/log/kern.log

```

If it reports a problem, post what it says.

If it seems to have worked without reporting a problem, see if you have an ethernet interface now using **ifconfig -a** and restart networking **sudo /etc/init.d/networking restart** if you do.


Your earlier dmesg does indicate one of your human interface devices (kb, mouse, other) is causing some problem; I don't know if this is impacting things later in the boot.  You might want to post those WARNING sections in a bug on launchpad.

---

### Post by mdoyle on 2007-10-03
dmesg | grep e1000 didn't return any output, neither did the two commands to reload the driver. The kern.log file is posted below. Restarting the networking returned 5 lines "Ignoring unknown interface ethX=ethX" substitute X for 0, 1, 2, 0 the last line was about my wireless card.

```

Oct  3 15:56:45 mike-desktop kernel: [   65.009398]  [<f88a4628>] hid_output_report+0x2a8/0x320 [hid]
Oct  3 15:56:45 mike-desktop kernel: [   65.009406]  [<f8906488>] hid_submit_ctrl+0x58/0x200 [usbhid]
Oct  3 15:56:45 mike-desktop kernel: [   65.009412]  [<f8906797>] usbhid_submit_report+0x167/0x1b0 [usbhid]
Oct  3 15:56:45 mike-desktop kernel: [   65.009415]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Oct  3 15:56:45 mike-desktop kernel: [   65.009418]  [<f8908e46>] hiddev_ioctl+0x446/0xb50 [usbhid]
Oct  3 15:56:45 mike-desktop kernel: [   65.009424]  [kunmap_atomic+81/144] kunmap_atomic+0x51/0x90
Oct  3 15:56:45 mike-desktop kernel: [   65.009426]  [kunmap_atomic+93/144] kunmap_atomic+0x5d/0x90
Oct  3 15:56:45 mike-desktop kernel: [   65.009429]  [__handle_mm_fault+534/2560] __handle_mm_fault+0x216/0xa00
Oct  3 15:56:45 mike-desktop kernel: [   65.009432]  [nameidata_to_filp+53/64] nameidata_to_filp+0x35/0x40
Oct  3 15:56:45 mike-desktop kernel: [   65.009435]  [do_filp_open+80/96] do_filp_open+0x50/0x60
Oct  3 15:56:45 mike-desktop kernel: [   65.009440]  [<f8908a00>] hiddev_ioctl+0x0/0xb50 [usbhid]
Oct  3 15:56:45 mike-desktop kernel: [   65.009444]  [do_ioctl+105/112] do_ioctl+0x69/0x70
Oct  3 15:56:45 mike-desktop kernel: [   65.009447]  [vfs_ioctl+92/608] vfs_ioctl+0x5c/0x260
Oct  3 15:56:45 mike-desktop kernel: [   65.009450]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Oct  3 15:56:45 mike-desktop kernel: [   65.009453]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Oct  3 15:56:45 mike-desktop kernel: [   65.009457]  [__find_acq_core+144/928] __find_acq_core+0x90/0x3a0
Oct  3 15:56:45 mike-desktop kernel: [   65.009461]  =======================
Oct  3 15:56:45 mike-desktop kernel: [   65.518451] usb 3-1.1: new full speed USB device using uhci_hcd and address 7
Oct  3 15:56:46 mike-desktop kernel: [   65.654320] usb 3-1.1: configuration #1 chosen from 1 choice
Oct  3 15:56:46 mike-desktop kernel: [   65.712088] Bluetooth: HCI USB driver ver 2.9
Oct  3 15:56:46 mike-desktop kernel: [   65.714564] usbcore: registered new interface driver hci_usb
Oct  3 15:57:00 mike-desktop kernel: [   79.823881] NET: Registered protocol family 10
Oct  3 15:57:00 mike-desktop kernel: [   79.823995] lo: Disabled Privacy Extensions
Oct  3 15:59:22 mike-desktop kernel: [  221.440470] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
Oct  3 15:59:22 mike-desktop kernel: [  221.440473] Copyright (c) 1999-2006 Intel Corporation.

```

---

### Post by noob12 on 2007-10-03
After running the modprobe you got no errors, but you also did not get an eth0 listed in your **ifconfig -a** output?

Does 
```

modinfo e1000 | grep -i 294c

```
give you any output?

---

### Post by mdoyle on 2007-10-03
Correct. Local Loopback is all that shows up after the ifconfig command.

That last command doesn't give me any output.

---

### Post by noob12 on 2007-10-03
OK.  Having trouble creating a consistent picture here.  

Based on this bug on launchpad, it indicates that Gutsy should have support for your device in the e1000 driver [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/140498](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/140498)  but it may not yet have hit the Tribe builds.

If your device was in fact covered, that last modinfo command should have produced an alias line with your device id in it.  This suggests that it isn't covered

On the other hand you said your network was working with this kernel before you updated the nvidia drivers.  I can't really explain that.  (Any possibility you had booted a different kernel version on your box?) 

On the off chance the device is mapped but to another driver, check:
```

grep -i 294c /lib/modules/`uname -r`/modules.pcimap

```

If that also turns up empty, I don't see how you could have had the network running earlier on the same kernel, and in that case I would suggest you try the lengthy build procedure in the HOWTO I pointed to earlier to build e1000 7.6.5 from the Intel sources.  It is true that the pre-built modules won't work for you but the build procedure should work if you replace 2.6.20-15 where it appears with your actual kernel version 2.6.22-12 uniformly.  

I can try to help walk you through that if you have questions.

---

### Post by mdoyle on 2007-10-03
So I went back and installed the version of Gutsy I had on another machine just to see what in the heck happened. It seems that during the install of the Nvidia drivers the kernal was upgrading as well, so that explains why my drivers went away.

I guess i'll have to build them, since a fresh install will set me back a few hours, and even then i'll want the Nvidia drivers which will once again upgrade the kernel.

I read your article, and the only part I don't understand really is where to download the correct sources. I know I need to change the name in the address, but its pretty jumbled with % and the likes. Any (more) help would be appreciated.

---

### Post by noob12 on 2007-10-03
[COLOR="Red"]UPDATE:  In Gutsy, this and other ICH9 chipsets are supposed to be covered in a driver module called e1000-ich9 which is in the linux-ubuntu-modules package in Gutsy.  I'm not sure that is installed by default or not, but you should not need to build yourself.  You may also need to add a line e1000-ich9 to your /etc/modules file.[/COLOR]


OK.

The driver source is the same link as is on that page.  It goes to the Intel site.

The headers sources depend on your architecture and kernel version.  The general way to get the right ones is to go to the [http://packages.ubuntu.com](http://packages.ubuntu.com) site and navigate to the right page based on your kernel version.

Almost all chips of this type are on Intel-based mobos so you are probably in the i386 architecture class.  Based on that and provided you are running the generic kernel, your header set and link would be

linux-headers-generic_2.6.22.12.17_i386.deb: 
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-meta%2Flinux-headers-generic_2.6.22.12.17_i386.deb&md5sum=d9c3de69b0a19a89ac860fc5ed195358&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-meta%2Flinux-headers-generic_2.6.22.12.17_i386.deb&md5sum=d9c3de69b0a19a89ac860fc5ed195358&arch=i386&type=main)

---

### Post by mdoyle on 2007-10-05
I'll add that line, if the linux-ubuntu-modules package isn't installed by default, how do I do that?

So i'm following your How To on building the driver. I get to the part in the build where I type the "make" command and it returns with "*** Linux kernel source not found. Stop".

---

### Post by noob12 on 2007-10-05
To see if you already have the e1000-ich9 Gutsy driver installed, see if **modinfo e1000-ich9** says something other than it can't find the module.

If it is not found, then you can download it from packages.ubuntu.com (using another host) and transfer the .deb file to your host and install the deb file.  It may also be on the CD-ROM.  Sorry I don't know as much about Gutsy, as I haven't spent much time on it yet.  If you've got the generic kernel then navigate here and find the download link: [http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-12-generic](http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-12-generic)
Otherwise, navigate down to the right package for your kernel.

The error you got when building means either that you didn't get the right headers for your kernel version or you are building in a directory with spaces in the full path.  I've had the latter happen with that makefile.  If you build under /tmp as directed in the instructions, that shouldn't happen though.

---

### Post by mdoyle on 2007-10-05
Yeah, I was doing it from the /tmp directory. Now with the correct headers I get "*** No targets. Stop."

Another thing to note is that there is no e1000.ko file in those packages I downloaded for Gutsy. There is a e1000.h file, so i've been substituting for that file, I hope its the correct file, heh.

---

### Post by noob12 on 2007-10-05
One of us is lost.  The .h file is C header file.   The .ko is a compile kernel module.
Not sure where you have gotten to at this point.

You might want to try installing the linux-ubuntu-modules package and using the e1000-ich9 driver from that instead of trying to build from scratch.

---

### Post by mdoyle on 2007-10-06
It's obvious who that someone is, lol.

I thought I had something going, but that's obviously not the case.

I've unpacked the linux-ubuntu-modules package, go into the unpacked folder, then the ubuntu folder and see the Makefile file. I run make in the terminal, it returns

```
Makefile:5: /.config: No such file or directory
make: *** No rule to make target '/.config'. Stop.

```

I'm obviously very new to linux, and obviousy i'm not installing this package correctly.

---

### Post by noob12 on 2007-10-06
It sounds like you are downloading the source version of the linux-ubuntu-modules package (tar.gz).  What you want is the built binary debian (.deb) package, which will directly install the kernel modules for you into the right place.  No make.

I looked  back and found that I actually don't know the specific kernel version you are running for sure.  If you post the output of ```
uname -a
``` then I can provide the links and step by step instructions for you and walk through them if you need.

---

### Post by mdoyle on 2007-10-06
I'm running

2.6.22-12-386

---

### Post by noob12 on 2007-10-06
OK.

1.  Go to this page: [http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-12-generic](http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-12-generic)

2.  Scroll down till you see a table that looks roughly like this (but all nice HTML of course)
```

Architecture	Files	Package Size	Installed Size
amd64 	[list of files] 	2896.4 	10772
i386 	[list of files] 	2942.5 	9448

```

3. Click on the **i386** which is a link.  You may be led to a download page where you need to select a mirror close to you before the download starts.  Save the file.  You should get a file with a name like:  **linux-ubuntu-modules-2.6.22-12-generic_2.6.22-12.32_i386.deb**  ; if you're doing it right now it should be the same down to the revision numbers.  Make sure it ends in .deb.

4. Transfer that file to your Ubuntu host using, say a USB drive.

5. On the Ubuntu host open a Terminal and go to the directory where you have that .deb file.

6. Type
```

sudo dpkg --install linux-ubuntu-modules-2.6.22-12-generic_2.6.22-12.32_i386.deb

```

7. This should install the driver module.  Try loading the e1000-ich9 module by hand
```

sudo modprobe e1000-ich9

```

8.  See if you have an eth0.  You should.
```

ifconfig -a

```
If you don't, things aren't going as expected.  We'll need to figure out why; in this case stop here.

9.  If things look good try to bring up eth0 by hand 
```

sudo ifup eth0

```
See if you have connectivity.  If not, we will troubleshoot that separately.  Proceed in any case.

10.  If you did not do this already, add a line saying just **e1000-ich9** to the file /etc/modules.  This may not be needed but it is safe.  I think you said you had done this before.  Let me know if you need instructions for that.

11.  Reboot.  After a reboot you should still have an eth0 (in **ifconfig -a** output) and you should have connectivity.  If you don't, we'll troubleshoot further.

---

### Post by mdoyle on 2007-10-06
The .deb file seemed to install correctly. Ran the modprobe command and it returned

```
FATAL: Module e1000-ich9 not found
```

---

### Post by noob12 on 2007-10-06
I didn't expect that.

What do these say?
```

ls /lib/modules/

ls /lib/modules/2.6.22-12-generic/ubuntu/net/e1000-ich9/

```

---

### Post by mdoyle on 2007-10-07
```
2.6.22-12-386 2.6.22-12-generic 2.6.22-12-generic 2.6.22-9-generic 
```

```
e1000-ich9.ko
```

---

### Post by noob12 on 2007-10-07
OK.  This time I was lost.  Sorry.  You said you are booting the -i386 version and I pointed you to the generic one by mistake.

You should follow the same instructions as posting #26 earlier on this thread, with these modifications

In step 1 go to this page: [http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-12-386](http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-12-386)

In step 3 the package you download will be called 
**linux-ubuntu-modules-2.6.22-12-386_2.6.22-12.32_i386.deb**

In step 6 you will actually do 
```

sudo dpkg --install linux-ubuntu-modules-2.6.22-12-386_2.6.22-12.32_i386.deb

```

---

### Post by mdoyle on 2007-10-07
That worked! Thanks a ton. Posting this from my Ubuntu computer.

Now here is a question. Should I be weary of any kernel updates? Will I need to follow these steps every time until the driver is loaded into the kernels?

---

### Post by noob12 on 2007-10-08
Good to hear (at last)!

Yes you might need to exercise some care when you get kernel upgrades.  I still don't know whether this package is supposed to be installed by default in Gutsy and if so why you didn't get it with your installation.  This might be a pre-release issue.

You should be ok if you make sure that you have pulled the updated linux-ubuntu-modules package for a new kernel version before you boot into the new kernel.

As long as you have the network, you should just be able to use aptitude or apt-get to pull the package and install it along with kernel updates that you get.  You should also be able to boot into the prior kernel to pull this if you forget.

In the worst case this method can be used to recover if you lose the driver.

---

### Post by mdoyle on 2007-10-08
Cool. Thanks again for the help.

---

