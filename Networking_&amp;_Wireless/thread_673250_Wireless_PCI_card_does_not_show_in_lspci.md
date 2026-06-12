---
title: "Wireless PCI card does not show in lspci"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by t99 on 2008-01-20
Hi all!
Im having a problem with my Broadcom 43xx wireless pci card.Unfortunately Iv forgotten what version it is as it has been working for months now.

Im running Edgy on my HP Compaq Presario F500 and around a week ago lost all wireless.

If the card showed up at all i would know how to fix it, but after extensive googling im lost as to why it would disappear?Any help would be appreciated!

Heres the output of some commands.

tarlach@trex-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


tarlach@trex-laptop:~$ lspci -n
00:00.0 0500: 10de:02f3 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:05.0 0300: 10de:0247 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0260 (rev a3)
00:0a.1 0c05: 10de:0264 (rev a3)
00:0a.3 0b40: 10de:0271 (rev a3)
00:0b.0 0c03: 10de:026d (rev a3)
00:0b.1 0c03: 10de:026e (rev a3)
00:0d.0 0101: 10de:0265 (rev f1)
00:0e.0 0101: 10de:0266 (rev f1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:14.0 0680: 10de:0269 (rev a3)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103


And these are the boot parameters i use: ----



title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/sda1 ro quiet splash noapic nolapic acpi off 
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot

:confused:

---

### Post by Hightide on 2008-01-20
> **t99 said:**
> Hi all!
Im having a problem with my Broadcom 43xx wireless pci card.:confused:

Hi t99

have you tried DarkNoob's how to? It may help

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

:)

---

### Post by t99 on 2008-01-20
Unfortunatley the offfline installer doesnt support my kernel.Il try the online installer tommorow but i doubt it will work because the installer couldnt find the card either. Im familiar with installling it through ndiswrapper so if i can get it to see the card,il be alright!

Thanks anyway!
Any other suggestions?


FYI

My dmesg output is mad ----

[17179577.424000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[17179577.424000] Uniform CD-ROM driver Revision: 3.20
[17179578.068000] usbcore: registered new driver hub
[17179578.068000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.072000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.076000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.080000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.084000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.088000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.088000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.096000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.096000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[17179578.096000] PCI: setting IRQ 11 as level-triggered
[17179578.096000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[17179578.096000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179578.096000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[17179578.096000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[17179578.100000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.300000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179578.300000] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[17179578.320000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179578.356000] usb usb1: configuration #1 chosen from 1 choice
[17179578.356000] hub 1-0:1.0: USB hub found
[17179578.356000] hub 1-0:1.0: 8 ports detected
[17179578.460000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[17179578.460000] PCI: setting IRQ 7 as level-triggered
[17179578.460000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[17179578.460000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[17179578.460000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[17179578.460000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[17179578.460000] ehci_hcd 0000:00:0b.1: debug port 1
[17179578.460000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[17179578.460000] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[17179578.460000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.460000] usb usb2: configuration #1 chosen from 1 choice
[17179578.460000] hub 2-0:1.0: USB hub found
[17179578.460000] hub 2-0:1.0: 8 ports detected
[17179578.568000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[17179578.568000] PCI: setting IRQ 10 as level-triggered
[17179578.568000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[17179578.568000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[17179578.568000] forcedeth: using HIGHDMA
[17179579.088000] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[17179579.120000] Attempting manual resume
[17179579.200000] kjournald starting.  Commit interval 5 seconds
[17179579.200000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.540000] input: PC Speaker as /class/input/input1
[17179592.552000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.584000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[17179592.584000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[17179592.584000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[17179592.608000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.844000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.892000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179593.032000] lp: driver loaded but no devices found
[17179593.068000] Adding 2835432k swap on /dev/disk/by-uuid/4dcd2b43-9e0c-4dfc-b4a7-5d1fe5d20f39.  Priority:-1 extents:1 across:2835432k
[17179593.144000] EXT3 FS on sda1, internal journal
[17179593.508000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[17179593.568000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179593.600000] ts: Compaq touchscreen protocol output
[17179594.664000] NET: Registered protocol family 17
[17179595.040000] ndiswrapper version 1.46 loaded (smp=yes)
[17179595.104000] usbcore: registered new driver ndiswrapper
[17179597.216000] ACPI: AC Adapter [ACAD] (on-line)
[17179597.264000] ACPI: Battery Slot [BAT0] (battery present)
[17179597.276000] ACPI: Power Button (FF) [PWRF]
[17179597.276000] ACPI: Power Button (CM) [PWRB]
[17179597.276000] ACPI: Sleep Button (CM) [SLPB]
[17179597.276000] ACPI: Lid Switch [LID]
[17179597.848000] ibm_acpi: ec object not found
[17179598.080000] pcc_acpi: loading...
[17179598.124000] wmi_add device=dff91000
[17179598.124000] calling WQBA
[17179598.400000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[17179598.400000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179598.612000] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179598.612000] powernow-k8: MP systems not supported by PSB BIOS structure
[17179598.612000] powernow-k8: MP systems not supported by PSB BIOS structure
[17179602.508000] apm: BIOS not found.
[17179607.140000] eth0: no link during initialization.
[17179607.820000] Bluetooth: Core ver 2.8
[17179607.820000] NET: Registered protocol family 31
[17179607.820000] Bluetooth: HCI device and connection manager initialized
[17179607.820000] Bluetooth: HCI socket layer initialized
[17179607.824000] Bluetooth: L2CAP ver 2.8
[17179607.824000] Bluetooth: L2CAP socket layer initialized
[17179607.828000] Bluetooth: RFCOMM socket layer initialized
[17179607.828000] Bluetooth: RFCOMM TTY layer initialized
[17179607.828000] Bluetooth: RFCOMM ver 1.7
[17179621.776000] NET: Registered protocol family 10
[17179621.776000] lo: Disabled Privacy Extensions
[17179621.776000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179621.776000] IPv6 over IPv4 tunneling driver
[17179829.908000] irq 7: nobody cared (try booting with the "irqpoll" option)
[17179829.908000]  <c0149924> __report_bad_irq+0x24/0x80  <c0149a1d> note_interrupt+0x9d/0x270
[17179829.908000]  <f8907854> usb_hcd_irq+0x24/0x60 [usbcore]  <c01492a3> handle_IRQ_event+0x33/0x60
[17179829.908000]  <c01493c8> __do_IRQ+0xf8/0x110  <c0105c89> do_IRQ+0x19/0x30
[17179829.908000]  <c010408a> common_interrupt+0x1a/0x20  <c0102080> default_idle+0x0/0x60
[17179829.908000]  <c01020aa> default_idle+0x2a/0x60  <c0102122> cpu_idle+0x42/0xb0
[17179829.908000] handlers:
[17179829.908000] [<f8907830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[17179829.908000] Disabling IRQ #7
[17180280.908000] ohci_hcd 0000:00:0b.0: wakeup
[17180281.316000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17180281.540000] usb 1-1: configuration #1 chosen from 1 choice
[17180281.736000] usbcore: registered new driver libusual
[17180281.744000] Initializing USB Mass Storage driver...
[17180281.744000] scsi2 : SCSI emulation for USB Mass Storage devices
[17180281.744000] usbcore: registered new driver usb-storage
[17180281.744000] USB Mass Storage support registered.
[17180281.744000] usb-storage: device found at 2
[17180281.744000] usb-storage: waiting for device to settle before scanning
[17180286.768000] usb-storage: device scan complete
[17180287.476000]   Vendor: OEI-USB   Model: xD CARD           Rev: 2.09
[17180287.476000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180287.976000] SCSI device sdb: 2047815 512-byte hdwr sectors (1048 MB)
[17180288.064000] sdb: Write Protect is off
[17180288.064000] sdb: Mode Sense: 0b 00 00 08
[17180288.064000] sdb: assuming drive cache: write through
[17180288.116000] SCSI device sdb: 2047815 512-byte hdwr sectors (1048 MB)
[17180288.204000] sdb: Write Protect is off
[17180288.204000] sdb: Mode Sense: 0b 00 00 08
[17180288.204000] sdb: assuming drive cache: write through
[17180288.204000]  sdb: sdb1
[17180289.556000] sd 2:0:0:0: Attached scsi removable disk sdb
[17180289.556000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17180292.356000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!




That spurious ACK is repeated at least a hundred times with the numbers ascending,I didnt think they were useful ,so deleted them before copying and pasting?

Is the IRQ 7 disabling message relevant,Iv had it before when the wireless was working but I ignored it.......


(*,)

---

### Post by t99 on 2008-01-21
Just as an update, Im still getting nowhere with this problem. I fired up a live cd of a different distro and the lspci did not see any wireless card. Would this indicate that this is a hardware problem?

---

### Post by t99 on 2008-01-22
Anyone??





:-?

---

### Post by t99 on 2008-01-23
Right I, getting to the point where Il have to reinstall Edgy. However I dont want to have this problem again if its a hardware problem. 


As a last resort, can someone recommmend a disro (with a live cd) that has good hardware detection just to doublecheck?

---

### Post by Hightide on 2008-01-23
HI t99

have you considered installing Gutsy?

:guitar:

---

### Post by rustybronco on 2008-01-23
> **t99 said:**
> Just as an update, Im still getting nowhere with this problem. I fired up a live cd of a different distro and the lspci did not see any wireless card. Would this indicate that this is a hardware problem?Going out on a limb, yes it does.
can you move it to a different slot and try it?
give this a whack on a 7.10 live cd... [http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)

---

