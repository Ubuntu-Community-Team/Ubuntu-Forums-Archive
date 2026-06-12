---
title: "GoPro Sd card wont mount???"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by KTM2Good on 2011-06-13
When i go into the disk utility to try and mount the sd card manually it gives me this error:


Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed


i'd like to figure out where this is claiming to be mounted as i searched the file system like crazy trying to find out where this thing is mounted. any help is much appreciated as i dont want to have to switch back to windows just to use this awesome little camera.

Also i am using maverick meerkat (10.10)

---

### Post by coffeecat on 2011-06-13
Welcome to the forum.

I think you accidentally clicked in the wrong place in Disk Utility:

> **KTM2Good said:**
> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

That's telling you that /dev/sda1 (that's the first partition in your hard drive) is your root Ubuntu partition. You can't remount it for obvious reasons. Your SD card wil be /dev/sdb1 or /dev/sdc1 depending on how many internal hard disks you have.

> **KTM2Good said:**
> i'd like to figure out where this is claiming to be mounted as i searched the file system like crazy trying to find out where this thing is mounted. any help is much appreciated as i dont want to have to switch back to windows just to use this awesome little camera.

Also i am using maverick meerkat (10.10)

If the card has been automounted then you will be able to find it in the folder it has mounted to in /media. But you shouldn't need to. An automounted SD card should cause a window to popup asking what you want to open the card with, or a file browser window will open depending on what your settings are.

A few questions: Are you plugging the camera in directly to a USB port and, if so, what make/model camera. If you are trying to mount the SD card with a SD card reader, is the card a standard SD or one of the higher-capacity SDHC cards? There is a problem with some (but only some) card readers with SDHC cards in Linux.

Last question: have you ever installed an application from the repository to "help" with usb automounting? They are not necessary; they all seem to cause problems; the commonest and worst offender, at least on GUI systems, seems to be usbmount which is not meant to be used with a GUI. If you have installed any of these 3rd party apps, I suggest you uninstall them.

---

### Post by KTM2Good on 2011-06-13
i have not used any of the mounting softwares as i did not see a point to it. and i know that this is forsure the output of the sd card and not another partition on the hard drive. 
as for the camera i do not use it to try and mount as it does not show up either. but it is a GoPro Hd Hero 960. 
and the sd card is a PNY Premium 16 GB/ 4hr hd video card, class 4

---

### Post by coffeecat on 2011-06-13
A 16GB card would be SDHC, so you might be tripping over the issue that I mentioned where some  card readers won't read SDHC cards in Linux.

Plug the card in, open a terminal (Applications > Accessories) and post the output of these two commands:

```
dmesg | tail 
sudo fdisk -lu
```

You will be prompted for your password with the second command. It won't be echoed to the screen - nothing will appear to be happening as you type - but don't worry, the password is going in. You can copy and paste the output by highlight-dragging the output text with the mouse, right-click > Copy, which will copy it to the clipboard, and then use the usual keyboard shortcut, ctrl-V, to paste it to the message field for your post.

---

### Post by KTM2Good on 2011-06-14
[    0.402320] libata version 3.00 loaded.
[    0.402536] usbcore: registered new interface driver usbfs
[    0.402587] usbcore: registered new interface driver hub
[    0.402688] usbcore: registered new device driver usb
[    0.404502] ACPI: WMI: Mapper loaded
[    0.404511] PCI: Using ACPI for IRQ routing
[    0.404520] PCI: pci_cache_line_size set to 64 bytes
[    0.404760] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.404770] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.404778] reserve RAM buffer: 000000003f576000 - 000000003fffffff 
[    0.404789] reserve RAM buffer: 000000003f66d000 - 000000003fffffff 
[    0.404798] reserve RAM buffer: 000000003f6ee000 - 000000003fffffff 
[    0.404807] reserve RAM buffer: 000000003f700000 - 000000003fffffff 
[    0.405121] NetLabel: Initializing
[    0.405129] NetLabel:  domain hash size = 128
[    0.405135] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.405181] NetLabel:  unlabeled traffic allowed by default
[    0.405314] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.405329] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.405345] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.412092] Switching to clocksource tsc
[    0.441115] AppArmor: AppArmor Filesystem Enabled
[    0.441153] pnp: PnP ACPI init
[    0.441201] ACPI: bus type pnp registered
[    0.505069] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
[    0.508068] pnp: PnP ACPI: found 9 devices
[    0.508077] ACPI: ACPI bus type pnp unregistered
[    0.508086] PnPBIOS: Disabled by ACPI PNP
[    0.508127] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.508138] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.508147] system 00:01: [io  0x0610] has been reserved
[    0.508157] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.508166] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.508176] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.508186] system 00:01: [io  0xff2c-0xff2f] has been reserved
[    0.508200] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.508211] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.508222] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.508232] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.508243] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.508254] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.508264] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.548857] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.548872] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.548886] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
[    0.548899] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.548915] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.548925] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.548939] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
[    0.548952] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.548969] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.548979] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
[    0.548993] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
[    0.549006] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.549023] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.549034] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.549049] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
[    0.549062] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
[    0.549079] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.549086] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.549099] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.549109] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.549153]   alloc irq_desc for 16 on node -1
[    0.549162]   alloc kstat_irqs on node -1
[    0.549180] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.549194] pci 0000:00:1c.0: setting latency timer to 64
[    0.549214] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.549231]   alloc irq_desc for 17 on node -1
[    0.549237]   alloc kstat_irqs on node -1
[    0.549250] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.549264] pci 0000:00:1c.1: setting latency timer to 64
[    0.549285]   alloc irq_desc for 18 on node -1
[    0.549291]   alloc kstat_irqs on node -1
[    0.549303] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.549315] pci 0000:00:1c.2: setting latency timer to 64
[    0.549334] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.549345]   alloc irq_desc for 19 on node -1
[    0.549351]   alloc kstat_irqs on node -1
[    0.549363] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.549377] pci 0000:00:1c.3: setting latency timer to 64
[    0.549394] pci 0000:00:1e.0: setting latency timer to 64
[    0.549406] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.549415] pci_bus 0000:00: resource 5 [io  0x0d00-0xefff]
[    0.549424] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.549432] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.549442] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.549450] pci_bus 0000:01: resource 1 [mem 0x57100000-0x581fffff]
[    0.549459] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.549469] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.549477] pci_bus 0000:02: resource 1 [mem 0x56100000-0x570fffff]
[    0.549486] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.549496] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
[    0.549504] pci_bus 0000:03: resource 1 [mem 0x55000000-0x560fffff]
[    0.549513] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
[    0.549523] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.549531] pci_bus 0000:04: resource 1 [mem 0x54000000-0x54ffffff]
[    0.549540] pci_bus 0000:04: resource 2 [mem 0x53000000-0x53ffffff 64bit pref]
[    0.549550] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.549558] pci_bus 0000:05: resource 5 [io  0x0d00-0xefff]
[    0.549567] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.549575] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
[    0.549685] NET: Registered protocol family 2
[    0.549875] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.550752] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.551903] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.552545] TCP: Hash tables configured (established 131072 bind 65536)
[    0.552557] TCP reno registered
[    0.552572] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.552596] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.552871] NET: Registered protocol family 1
[    0.552922] pci 0000:00:02.0: Boot video device
[    0.553278] PCI: CLS 0 bytes, default 64
[    0.553365] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.553374] Simple Boot Flag at 0x44 set to 0x1
[    0.553980] cpufreq-nforce2: No nForce2 chipset.
[    0.554106] Scanning for low memory corruption every 60 seconds
[    0.554582] audit: initializing netlink socket (disabled)
[    0.554611] type=2000 audit(1308074185.548:1): initialized
[    0.578853] highmem bounce pool size: 64 pages
[    0.578873] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.584383] VFS: Disk quotas dquot_6.5.2
[    0.584601] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.586840] fuse init (API version 7.14)
[    0.587168] msgmni has been set to 1709
[    0.758893] Freeing initrd memory: 10524k freed
[    0.774806] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.774815] io scheduler noop registered
[    0.774820] io scheduler deadline registered
[    0.774862] io scheduler cfq registered (default)
[    0.775108] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.775170]   alloc irq_desc for 40 on node -1
[    0.775176]   alloc kstat_irqs on node -1
[    0.775195] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.775381] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.775436]   alloc irq_desc for 41 on node -1
[    0.775441]   alloc kstat_irqs on node -1
[    0.775455] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.775635] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.775697]   alloc irq_desc for 42 on node -1
[    0.775702]   alloc kstat_irqs on node -1
[    0.775716] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.775916] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.775972]   alloc irq_desc for 43 on node -1
[    0.775976]   alloc kstat_irqs on node -1
[    0.775991] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.776233] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.776464] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.776480] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.776759] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.776774] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.777041] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.777055] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.777320] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.777335] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.777644] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.777658] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.777924] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.777939] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.778203] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.778217] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.778481] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.778495] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.778601] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.778824] intel_idle: MWAIT substates: 0x20220
[    0.778830] intel_idle: v0.4 model 0x1C
[    0.778834] intel_idle: lapic_timer_reliable_states 0x2
[    0.778847] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.778959] Switching to clocksource hpet
[    0.840197] ACPI: AC Adapter [AC] (on-line)
[    0.840408] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.840422] ACPI: Power Button [PWRB]
[    0.840529] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.840628] ACPI: Lid Switch [LID0]
[    0.840736] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.840746] ACPI: Sleep Button [SLPB]
[    0.840881] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.840891] ACPI: Power Button [PWRF]
[    0.841235] ACPI: Fan [FAN] (on)
[    0.841819] ACPI: acpi_idle yielding to intel_idle
[    0.908388] thermal LNXTHERM:01: registered as thermal_zone0
[    0.908408] ACPI: Thermal Zone [THRM] (27 C)
[    0.908612] ERST: Table is not found!
[    0.908782] isapnp: Scanning for PnP cards...
[    0.909467] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.913981] brd: module loaded
[    0.915811] loop: module loaded
[    0.917680] Fixed MDIO Bus: probed
[    0.917809] PPP generic driver version 2.4.2
[    0.917942] tun: Universal TUN/TAP device driver, 1.6
[    0.917949] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.918218] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.918274] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.918314] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.918324] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.918429] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.918492] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.918512] ehci_hcd 0000:00:1d.7: debug port 1
[    0.922399] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.922443] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    0.936034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.936395] hub 1-0:1.0: USB hub found
[    0.936411] hub 1-0:1.0: 8 ports detected
[    0.936621] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI)

---

### Post by KTM2Good on 2011-06-14
workaround
[    0.918512] ehci_hcd 0000:00:1d.7: debug port 1
[    0.922399] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.922443] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    0.936034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.936395] hub 1-0:1.0: USB hub found
[    0.936411] hub 1-0:1.0: 8 ports detected
[    0.936621] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.936670] uhci_hcd: USB Universal Host Controller Interface driver
[    0.936750] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.936768] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.936777] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.936886] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.936935] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
[    0.937308] hub 2-0:1.0: USB hub found
[    0.937322] hub 2-0:1.0: 2 ports detected
[    0.937481] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.937499] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.937508] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.937611] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.937679] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
[    0.938043] hub 3-0:1.0: USB hub found
[    0.938061] hub 3-0:1.0: 2 ports detected
[    0.938223] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.938240] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.938248] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.938361] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.938424] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
[    0.938778] hub 4-0:1.0: USB hub found
[    0.938792] hub 4-0:1.0: 2 ports detected
[    0.938941] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.938959] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.938967] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.939075] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.939139] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
[    0.939501] hub 5-0:1.0: USB hub found
[    0.939514] hub 5-0:1.0: 2 ports detected
[    0.939821] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    0.960395] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.960415] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.960647] mice: PS/2 mouse device common for all mice
[    0.961113] rtc_cmos 00:03: RTC can wake from S4
[    0.961229] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.961281] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.961637] device-mapper: uevent: version 1.0.3
[    0.961992] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.962203] device-mapper: multipath: version 1.1.1 loaded
[    0.962211] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.962588] EISA: Probing bus 0 at eisa.0
[    0.962597] EISA: Cannot allocate resource for mainboard
[    0.962606] Cannot allocate resource for EISA slot 1
[    0.962614] Cannot allocate resource for EISA slot 2
[    0.962622] Cannot allocate resource for EISA slot 3
[    0.962629] Cannot allocate resource for EISA slot 4
[    0.962637] Cannot allocate resource for EISA slot 5
[    0.962645] Cannot allocate resource for EISA slot 6
[    0.962653] Cannot allocate resource for EISA slot 7
[    0.962660] Cannot allocate resource for EISA slot 8
[    0.962666] EISA: Detected 0 cards.
[    0.963122] cpuidle: using governor ladder
[    0.963523] cpuidle: using governor menu
[    0.964396] TCP cubic registered
[    0.964843] NET: Registered protocol family 10
[    0.965870] lo: Disabled Privacy Extensions
[    0.966507] NET: Registered protocol family 17
[    0.968841] Using IPI No-Shortcut mode
[    0.969141] PM: Resume from disk failed.
[    0.969171] registered taskstats version 1
[    0.969769]   Magic number: 15:744:946
[    0.969825] tty tty3: hash matches
[    0.969936] rtc_cmos 00:03: setting system clock to 2011-06-14 17:56:26 UTC (1308074186)
[    0.969945] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.969951] EDD information not available.
[    0.988987] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.252047] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.263912] isapnp: No Plug & Play device found
[    1.263985] Freeing unused kernel memory: 688k freed
[    1.264665] Write protecting the kernel text: 4944k
[    1.264741] Write protecting the kernel read-only data: 1976k
[    1.305582] udev[76]: starting version 163
[    1.524107] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.568928] ACPI: Battery Slot [BAT0] (battery present)
[    1.690404] Initializing USB Mass Storage driver...
[    1.690767] scsi0 : usb-storage 1-8:1.0
[    1.691176] usbcore: registered new interface driver usb-storage
[    1.691185] USB Mass Storage support registered.
[    2.117081] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.117108] atl1c 0000:03:00.0: setting latency timer to 64
[    2.203807] ahci 0000:00:1f.2: version 3.0
[    2.203848] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.203935]   alloc irq_desc for 44 on node -1
[    2.203944]   alloc kstat_irqs on node -1
[    2.203969] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    2.204101] ahci: SSS flag set, parallel bus scan disabled
[    2.204167] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    2.204179] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    2.204194] ahci 0000:00:1f.2: setting latency timer to 64
[    2.204930] scsi1 : ahci
[    2.205253] scsi2 : ahci
[    2.205534] scsi3 : ahci
[    2.205798] scsi4 : ahci
[    2.206612] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 44
[    2.206623] ata2: DUMMY
[    2.206633] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 44
[    2.206641] ata4: DUMMY
[    2.217832] atl1c 0000:03:00.0: version 1.0.0.2-NAPI
[    2.524157] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.526443] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.526893] ata1.00: ATA-8: Hitachi HTS543216L9SA00, FB2OC40C, max UDMA/133
[    2.526909] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.528793] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.529318] ata1.00: configured for UDMA/133
[    2.544557] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    2.545136] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.545437] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.545622] sd 1:0:0:0: [sda] Write Protect is off
[    2.545630] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.545701] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.546360]  sda: sda1 sda2 < sda5 >
[    2.593965] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.690736] scsi 0:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.692297] sd 0:0:0:0: Attached scsi generic sg1 type 0
[    2.864105] ata3: SATA link down (SStatus 0 SControl 300)
[    3.611536] sd 0:0:0:0: [sdb] 32372736 512-byte logical blocks: (16.5 GB/15.4 GiB)
[    3.612322] sd 0:0:0:0: [sdb] Write Protect is off
[    3.612337] sd 0:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.612357] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[    3.615516] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[    3.615535]  sdb: sdb1
[    3.619301] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[    3.619316] sd 0:0:0:0: [sdb] Attached SCSI removable disk
[    4.007039] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.267399] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.377304] udev[368]: starting version 163
[   10.820352] lp: driver loaded but no devices found
[   11.012317] Linux video capture interface: v2.00
[   11.254048] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)
[   11.271053] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input5
[   11.271543] usbcore: registered new interface driver uvcvideo
[   11.271552] USB Video Class driver (v0.1.0)
[   11.746798] type=1400 audit(1308099397.272:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=556 comm="apparmor_parser"
[   11.746914] type=1400 audit(1308099397.272:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=532 comm="apparmor_parser"
[   11.747714] type=1400 audit(1308099397.272:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=556 comm="apparmor_parser"
[   11.747826] type=1400 audit(1308099397.272:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=532 comm="apparmor_parser"
[   11.748244] type=1400 audit(1308099397.276:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=556 comm="apparmor_parser"
[   11.748405] type=1400 audit(1308099397.276:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=532 comm="apparmor_parser"
[   11.783246] intel_rng: FWH not detected
[   11.783797] Linux agpgart interface v0.103
[   11.931250] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   11.932625] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   11.936201] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   12.005437] lib80211: common routines for IEEE802.11 drivers
[   12.005450] lib80211_crypt: registered algorithm 'NULL'
[   12.239111] leds_ss4200: no LED devices found
[   12.345397] acpi device:27: registered as cooling_device3
[   12.345937] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   12.346106] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[   12.880807] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.880820] Disabling lock debugging due to kernel taint
[   12.905734] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.905758] wl 0000:01:00.0: setting latency timer to 64
[   13.175515] lib80211_crypt: registered algorithm 'TKIP'
[   13.175927] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   13.209671] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000/0xa0000
[   13.289990] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.291964]   alloc irq_desc for 45 on node -1
[   13.291976]   alloc kstat_irqs on node -1
[   13.292055] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.292313] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.295612] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   13.512208] [drm] Initialized drm 1.1.0 20060810
[   13.899837] hda_codec: ALC272X: BIOS auto-probing.
[   13.913097] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.913113] i915 0000:00:02.0: setting latency timer to 64
[   13.997035] [drm] set up 7M of stolen space
[   14.107672] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.108100] [drm] initialized overlay support
[   14.421091] Skipping EDID probe due to cached edid
[   14.838600] Console: switching to colour frame buffer device 128x37
[   14.845696] fb0: inteldrmfb frame buffer device
[   14.845702] drm: registered panic notifier
[   14.845711] Slow work thread pool: Starting up
[   14.845865] Slow work thread pool: Ready
[   14.845889] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.932144] Skipping EDID probe due to cached edid
[   17.201960] type=1400 audit(1308099402.728:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=969 comm="apparmor_parser"
[   17.202856] type=1400 audit(1308099402.728:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=969 comm="apparmor_parser"
[   17.203377] type=1400 audit(1308099402.728:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=969 comm="apparmor_parser"
[   17.248460] type=1400 audit(1308099402.776:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=967 comm="apparmor_parser"
[   18.145102] type=1400 audit(1308099403.672:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=985 comm="apparmor_parser"
[   18.146334] type=1400 audit(1308099403.672:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=985 comm="apparmor_parser"
[   18.147966] type=1400 audit(1308099403.672:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=933 comm="apparmor_parser"
[   18.149245] type=1400 audit(1308099403.676:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=933 comm="apparmor_parser"
[   18.588072] type=1400 audit(1308099404.116:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=987 comm="apparmor_parser"
[   18.613808] type=1400 audit(1308099404.140:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=997 comm="apparmor_parser"
[   18.672423] ppdev: user-space parallel port driver
[   20.404378]   alloc irq_desc for 46 on node -1
[   20.404386]   alloc kstat_irqs on node -1
[   20.404414] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[   20.405192] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.265923] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.265935] vboxdrv: Successfully done.
[   22.265942] vboxdrv: Found 2 processor cores.
[   22.266578] vboxdrv: fAsync=0 offMin=0x180 offMax=0x93c
[   22.270643] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.270657] vboxdrv: Successfully loaded version 3.2.8_OSE (interface 0x00140001).
[   22.781392] Skipping EDID probe due to cached edid
[   22.912367] Skipping EDID probe due to cached edid
[   26.423964] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   27.716199] Skipping EDID probe due to cached edid
[   27.756194] Skipping EDID probe due to cached edid
[   27.804201] Skipping EDID probe due to cached edid
[   27.836198] Skipping EDID probe due to cached edid
[   30.480048] eth1: no IPv6 routers present
[   31.138711] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   40.648333] Skipping EDID probe due to cached edid
[   40.701234] Skipping EDID probe due to cached edid
[   40.736204] Skipping EDID probe due to cached edid
[   45.924174] Skipping EDID probe due to cached edid
[   47.569170] Skipping EDID probe due to cached edid
[  109.607797] lo: Disabled Privacy Extensions
[  209.173790] usb 1-2: USB disconnect, address 2
[  209.432180] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  209.598906] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)
[  209.618155] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8
[ 2678.483062] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
james@james-Aspire-one:~$ tail
sudo fdisk -1u





sorry about the way i had to post this back. it was saying i had images in it...

---

### Post by ClientAlive on 2011-06-14
Wherever that smiley face shows up started out as the number eight or colon eight. I've had it happen to me and I had to edit the post and actually type out "eight."

8)

Edit: It's eight followed by right parenthesis.

---

### Post by tgalati4 on 2011-06-14
I've only used 4GB sandisk cards in my GoPro and I've never had problems reading them.  It could be your reader is not happy reading 16GB cards.  Try plugging in the camera with USB and see if you can see the files.  Try another reader in another computer.

---

### Post by coffeecat on 2011-06-15
@KTM2Good, I asked you to post the output of:
```
dmesg | tail 
sudo fdisk -lu
```But you posted the output of:

```
dmseg
```And you didn't post the output of 'sudo fdisk -lu'

I suspect you may have used another character for '|'. The '|' (pipe) symbol is usually on the key next to the left shift key, the backslash key shifted.

I can see some what is needed from your posted output but we need to be sure you had the card plugged in first. Plug the card in and then a few seconds later:

```
dmesg | tail 
sudo fdisk -lu
```It's important to get these outputs to see whether your system is even seeing the card let alone mount it. I suspect that the problem is that it will be a SDHC card, but let's see that output.

---

### Post by KTM2Good on 2011-06-15
oh crap see i didnt know if that was a just to make me type a new message or what. and the sudo fdisk -1u didnt go through but i suspect that is because i typed the first command wrong.

---

### Post by KTM2Good on 2011-06-15
> **coffeecat said:**
> @KTM2Good, I asked you to post the output of:
```
dmesg | tail 
sudo fdisk -lu
```But you posted the output of:

```
dmseg
```And you didn't post the output of 'sudo fdisk -lu'

I suspect you may have used another character for '|'. The '|' (pipe) symbol is usually on the key next to the left shift key, the backslash key shifted.

I can see some what is needed from your posted output but we need to be sure you had the card plugged in first. Plug the card in and then a few seconds later:

```
dmesg | tail 
sudo fdisk -lu
```It's important to get these outputs to see whether your system is even seeing the card let alone mount it. I suspect that the problem is that it will be a SDHC card, but let's see that output.


james@james-Aspire-one:~$ dmesg | tail
[37818.492406] video LNXVIDEO:00: Restoring backlight state
[37818.605057] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[37818.660120] Skipping EDID probe due to cached edid
[37818.815901] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[37818.822162] ADDRCONF(NETDEV_UP): eth0: link is not ready
[37819.388367] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[37819.391973] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[37819.392069]  sdb: sdb1
[37820.680935] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[37829.160068] eth1: no IPv6 routers present
james@james-Aspire-one:~$ sudo fdisk -1u
[sudo] password for james: 
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

is that better. i am sorry i have been using ubuntu for a while but i only have used terminal to fetch updates and some programs. i do believe that i did the fdisk -lu wrong as i mistook the l for a 1. here are the real results of that. 


james@james-Aspire-one:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007c9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306440191   153219072   83  Linux
/dev/sda2       306442238   312580095     3068929    5  Extended
/dev/sda5       306442240   312580095     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 16.6 GB, 16574840832 bytes
28 heads, 60 sectors/track, 19269 cylinders, total 32372736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192    32372735    16182272    b  W95 FAT32

---

### Post by coffeecat on 2011-06-15
The system is seeing the card as sdb and the single FAT partition on it as sdb1. Is it not appearing anywhere when you plug it in - not in the Places menu?

If it isn't, try this from a terminal with the card in:

```
udisks --umount /dev/sdb1
```

---

### Post by KTM2Good on 2011-06-15
ok these are the results of the umount command and then i tried a few others as you can see. 



james@james-Aspire-one:~$ udisks --umount /dev/sdb1
Usage:
  udisks [OPTION...] udisks commandline tool

Help Options:
  -h, --help                   Show help options

Application Options:
  --enumerate                  Enumerate objects paths for devices
  --enumerate-device-files     Enumerate device files for devices
  --dump                       Dump all information about all devices
  --monitor                    Monitor activity from the disk daemon
  --monitor-detail             Monitor with detail
  --show-info                  Show information about a device file
  --inhibit-polling            Inhibit polling
  --inhibit-all-polling        Inhibit all polling
  --poll-for-media             Poll for media
  --set-spindown               Set spindown timeout for drive
  --set-spindown-all           Set spindown timeout for all drives
  --spindown-timeout           Spindown timeout in seconds
  --inhibit                    Inhibit the daemon
  --mount                      Mount the given device
  --mount-fstype               Specify file system type
  --mount-options              Mount options separated by comma
  --unmount                    Unmount the given device
  --unmount-options            Unmount options separated by comma
  --detach                     Detach the given device
  --detach-options             Detach options separated by comma
  --ata-smart-refresh          Refresh ATA SMART data
  --ata-smart-wakeup           Wake up the disk if it is not awake
  --ata-smart-simulate         Inject libatasmart BLOB for testing

See the udisks man page for details.
james@james-Aspire-one:~$ udisks --unmount /dev/sdb1
Unmount failed: Device is not mounted
james@james-Aspire-one:~$ udisks --mount /dev/sdb1
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed



and to answer your question it does not show up in places nor when i check the media folder that it says it is mounted to. is there maybe something i have to download for it to allow the format of the stuff on the card?

---

### Post by KTM2Good on 2011-06-15
i also forgot to mention that the built in reader on my laptop worked just fine and read the 16 gb card before i put it in the go pro camera. afterwards i try and put it in the reader and it dont work right. and gives me the problem mentioned

---

### Post by tgalati4 on 2011-06-15
I seem to recall that GoPro had a list of "certified" SD cards to be used in their cameras.  Others might work, but the "certified" ones were the ones to use for critical shots.  SanDisk, Kingston and a few others.  I'm not sure if PNY made the cut.  So it's possible that the files are recoverable:

Open a terminal:  (cut and paste each command, one at a time, highlight with the mouse then use the middle click button on the mouse)

sudo apt-get install testdisk
man testdisk
man photorec

Read those manual pages thoroughly (spacebar to move forward, q to quit man pages) to understand what each tool does before mangling your SD card further.  If you don't care about the shots, then try reformatting the card within the camera and shoot a few test videos.

Can you see the files when you plug the camera in with a USB cable then plug that cable into your computer?

---

### Post by coffeecat on 2011-06-16
@KTM2Good, my apologies, I made a silly typing error with that udisks command. The option should have been --mount, not --umount. Try:

```
udisks --mount /dev/sdb1
```> **KTM2Good said:**
> i also forgot to mention that the built in reader on my laptop worked just fine and read the 16 gb card before i put it in the go pro camera. afterwards i try and put it in the reader and it dont work right. and gives me the problem mentioned

The 16GB card worked just fine at first but after you used it in the camera, it fails to work. Interesting. Did you reformat the card in the camera? There's one unusual thing about your fdisk output:

> **KTM2Good said:**
> ```
Disk /dev/sdb: 16.6 GB, 16574840832 bytes
28 heads, 60 sectors/track, 19269 cylinders, total 32372736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192    32372735    16182272    b  W95 FAT32
```

A start sector of 8192 is not impossible, but I don't see the purpose of it. I wonder if the camera is formatting the card in an unusual way.

If you did reformat the card in the camera, try this experiment. Check the udisks command first. Now backup any photos you may have on the card - I guess you'll have to use Windows for this bit. Now, in Ubuntu, use Disk Utility to reformat it to FAT. If it doesn't automount once Disk Utility has finished, unplug it and plug it back in again to get it to automount (hopefully). Can you copy files to it? Post the output of 'sudo fdisk -lu' again to see what the start sector is now. If the card works OK when formatted with Disk Utility, put it in the camera and use the camera to reformat it. What happens now when you plug it into Ubuntu?

---

### Post by KTM2Good on 2011-06-16
coffeecat i have done that before with it. that is the only way that the card actually mounts. and if you look i tried mounting cuz i thought that you might have made a typo. i also tried to unmount it.

the card worked just fine in my dads gopro as he used it until he bought a 32gb. 

so next i should run the commands trying to use the camera as a card reader?

---

