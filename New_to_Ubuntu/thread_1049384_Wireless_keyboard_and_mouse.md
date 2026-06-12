---
title: "Wireless keyboard and mouse"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by ChrisYK on 2009-01-24
I am new to Linux. Installed Ubuntu 8.10 with no problem, but when I switch from a wired keyboard and mouse to either a Logitech RX650 wireless keyboard and mouse or a Microsoft Wireless Multimedia keyboard and Microsoft Standard Wireless Optical mouse the rate at which keyboard button presses are recognised on the screen is rather slow and the curser for the mouse jumps from one point on the screen to another, making the mouse unusable. Changing the sensitivity of the mouse makes no difference (and the wire components work fine).

How can this be resolved?

---

### Post by Cypher on 2009-01-24
I presume the wireless keyboard/mouse have a USB component that you plug into your PC? Open up a terminal (Applications->Accessories->Terminal) and type "dmesg" to see if there are any interesting messages related to USB that might shed some light on this.

---

### Post by 5BallJuggler on 2009-01-24
Are you booting the system with the wireless mouse and keybourd connected, or the wired devices.
Try just connecting using wireless, the system should autodetect.

Have you changed the batteries in the devices recently?

---

### Post by ChrisYK on 2009-01-24
Here is an extract of dmesg, but I do not know if it is "interesting"!..

NB. The wireless set up does use a USB plug-in receiver. I have tried starting the system a number of times without the wired keyboard and mouse, and with both Logitech and Microsoft keyboards and mouse, but I can only effectively type on the forum with the wired keyboard plugged in. 

[    1.720173] ehci_hcd 0000:00:1d.7: debug port 1
[    1.720177] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.720185] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    1.725392] USB Universal Host Controller Interface driver v3.0
[    1.726589] No dock devices found.
[    1.736007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    1.736087] usb usb1: configuration #1 chosen from 1 choice
[    1.736106] hub 1-0:1.0: USB hub found
[    1.736110] hub 1-0:1.0: 8 ports detected
[    1.741292] SCSI subsystem initialized
[    1.758793] libata version 3.00 loaded.
[    1.944227] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.944236] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.944239] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.944259] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.944281] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fe00
[    1.944344] usb usb2: configuration #1 chosen from 1 choice
[    1.944363] hub 2-0:1.0: USB hub found
[    1.944367] hub 2-0:1.0: 2 ports detected
[    2.044152] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.044163] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.044166] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.044182] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.044206] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fd00
[    2.044261] usb usb3: configuration #1 chosen from 1 choice
[    2.044278] hub 3-0:1.0: USB hub found
[    2.044281] hub 3-0:1.0: 2 ports detected
[    2.108012] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    2.148131] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.148136] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.148140] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.148161] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.148189] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    2.148252] usb usb4: configuration #1 chosen from 1 choice
[    2.148273] hub 4-0:1.0: USB hub found
[    2.148278] hub 4-0:1.0: 2 ports detected
[    2.240952] usb 1-7: configuration #1 chosen from 1 choice
[    2.356169] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.356175] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.356177] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.356195] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.356221] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    2.356284] usb usb5: configuration #1 chosen from 1 choice
[    2.356305] hub 5-0:1.0: USB hub found
[    2.356309] hub 5-0:1.0: 2 ports detected
[    2.468518] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    2.518543] irq 18: nobody cared (try booting with the "irqpoll" option)
[    2.518548] Pid: 0, comm: swapper Not tainted 2.6.27-9-generic #1
[    2.518551]  [<c037c4b6>] ? printk+0x1d/0x1f
[    2.518558]  [<c01781bc>] __report_bad_irq+0x2c/0xa0
[    2.518563]  [<c0178344>] note_interrupt+0x114/0x140
[    2.518567]  [<c01770b1>] ? handle_IRQ_event+0x41/0x80
[    2.518571]  [<c0178993>] handle_fasteoi_irq+0xb3/0xe0
[    2.518574]  [<c0106c15>] do_IRQ+0x45/0x80
[    2.518578]  [<c013791c>] ? irq_exit+0x8c/0x90
[    2.518582]  [<c0113f8d>] ? smp_apic_timer_interrupt+0x5d/0x90
[    2.518587]  [<c0105003>] common_interrupt+0x23/0x30
[    2.518591]  [<c010acca>] ? mwait_idle+0x4a/0x50
[    2.518594]  [<c010288d>] cpu_idle+0x7d/0x140
[    2.518597]  [<c036ee83>] rest_init+0x53/0x60
[    2.518602]  =======================
[    2.518603] handlers:
[    2.518605] [<f88d89a0>] (usb_hcd_irq+0x0/0x90 [usbcore])
[    2.518620] Disabling IRQ #18
[    2.564164] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.564181] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    2.564190] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    2.564208] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.564219] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    2.564225] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    2.564243] ohci1394 0000:03:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.613935] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fd8ff000-fd8ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.622622] ata_piix 0000:00:1f.1: version 2.12
[    2.622629] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.622656] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.623058] scsi0 : ata_piix
[    2.623135] scsi1 : ata_piix
[    2.623695] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    2.623699] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.674321] usb 4-2: configuration #1 chosen from 1 choice
[    2.690057] usbcore: registered new interface driver hiddev
[    2.703489] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input2
[    2.703658] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2
[    2.732238] Fixing up Logitech keyboard report descriptor
[    2.732818] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input3
[    2.733038] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2
[    2.733051] usbcore: registered new interface driver usbhid
[    2.733055] usbhid: v2.6:USB HID core driver
[    2.780113] ata2: port disabled. ignoring.
[    2.780133] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.780138] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.780170] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.780209] scsi2 : ata_piix
[    2.780274] scsi3 : ata_piix
[    2.780918] ata3: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[    2.780922] ata4: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[    2.952257] ata3.00: ATAPI: Optiarc DVD RW AD-7201S, 1.06, max UDMA/100
[    2.952393] ata3.01: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[    2.952396] ata3.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.968252] ata3.00: configured for UDMA/100
[    2.976380] ata3.01: configured for UDMA/133
[    3.104357] irq 18: nobody cared (try booting with the "irqpoll" option)
[    3.104362] Pid: 0, comm: swapper Not tainted 2.6.27-9-generic #1
[    3.104364]  [<c037c4b6>] ? printk+0x1d/0x1f
[    3.104371]  [<c01781bc>] __report_bad_irq+0x2c/0xa0
[    3.104376]  [<c0178344>] note_interrupt+0x114/0x140
[    3.104379]  [<c01770b1>] ? handle_IRQ_event+0x41/0x80
[    3.104383]  [<c0178993>] handle_fasteoi_irq+0xb3/0xe0
[    3.104387]  [<c0106c15>] do_IRQ+0x45/0x80
[    3.104390]  [<c0153a53>] ? tick_nohz_stop_sched_tick+0xd3/0x360
[    3.104395]  [<c0105003>] common_interrupt+0x23/0x30
[    3.104399]  [<c010acca>] ? mwait_idle+0x4a/0x50
[    3.104402]  [<c010288d>] cpu_idle+0x7d/0x140
[    3.104405]  [<c037a711>] start_secondary+0x9d/0xcc
[    3.104409]  =======================

---

### Post by ChrisYK on 2009-01-25
Bump - is there anyone who can help please.

---

