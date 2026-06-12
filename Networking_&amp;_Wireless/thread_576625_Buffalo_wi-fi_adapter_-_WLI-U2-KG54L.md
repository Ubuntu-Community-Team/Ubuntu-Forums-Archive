---
title: "Buffalo wi-fi adapter - WLI-U2-KG54L"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by rfgermain on 2007-10-15
firstly am completely new to, threads, ubuntu, irc and all this talk about kernals.
I am a windows convert that got lured into this ubuntu, and its fantastic i must admit - and completely free!!! i don't know why i gave all that money to Mr gates.

The problem i have though is you (ubuntu users, Collectively) speak another language and well.......... i dont speak it!
All was brilliant not a problem or error message in sight, but i have a wireless hub from BT   and i started using it with the Ethernet cable connected directly to the hub - not exactly what its for but hey job done i guess!, i moved the computer upstairs and bought a buffalo adapter to talk to the hub. i plugged it in the usb port, light came on and .......... nothing worked?
i put the c.d. in that came with the device and it was all .exe files and i guess thats just windows that uses them? so i have a dire problem;

I can get advice about how to do this but i find again and again the chosen language to give advice is 'geek'?
Can anyone please give me a step by step way to get this to talk to the hub as i'm well out of my league with this?
I would consider my knowledge of computers good and would have no probs on windows but because am so new to this ubuntu i have no idea.

i have a wireless adapter in one hand, that doesn't work and a copy of vista in the other please help me because i don't want to go backwards

My email is [email]rfgermain@gmail.com[/email] if you just want to email me?
Thanks in advance
Richard

---

### Post by Lambert on 2007-10-15
Yes geek is a common language but just ask for clarification and we'll continue to work with you until it works.

As far as your device, it looks like the chipset in the device is based on zydas.

[http://ubuntuforums.org/showthread.php?t=468347&highlight=zd1211rw](http://ubuntuforums.org/showthread.php?t=468347&highlight=zd1211rw)

shows how one user got this working. You can search the forum for zd1211rw and find more information.

Basically look for the link in the 4th post, download the file ending in .deb and follow this howto on installing .deb packages in ubuntu if you're not sure how.



[http://www.cutlersoftware.com/ubuntuinstall/#installing_a_package_manually](http://www.cutlersoftware.com/ubuntuinstall/#installing_a_package_manually)

Then open the application terminal found in applications->accesories-> and type this 

```

sudo modprobe -v zd1211rw

```

Now open up network manager and try to connect. If you're having problems come back here with as much details as you can including a reboot and opening the terminal program again typing in the following 

```

dmesg

```

and posting the output here.

---

### Post by rfgermain on 2007-10-17
Hi thanks for your help i felt like a pro downloading these .deb files and am sure i nearly got it to work?

But hey you said if i didn't then post the reply up here..... and guess what i didnt so;




richard@richard-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f57f0
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
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7270 checksum 0
[    0.000000] ACPI: RSDP 000F7270, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 1FFF30C0, 3A27 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF6B00, 0068 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=429e6671-eecd-426f-a072-72e13eadc196 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2020.008 MHz processor.
[   17.201271] Console: colour VGA+ 80x25
[   17.201689] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.202063] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.216960] Memory: 508172k/524224k available (2015k kernel code, 15476k reserved, 916k data, 364k init, 0k highmem)
[   17.216974] virtual kernel memory layout:
[   17.216975]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   17.216977]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.216978]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   17.216981]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   17.216983]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   17.216984]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   17.216986]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   17.216990] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.217041] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.296922] Calibrating delay using timer specific routine.. 4044.09 BogoMIPS (lpj=8088184)
[   17.296956] Security Framework v1.0.0 initialized
[   17.296966] SELinux:  Disabled at boot.
[   17.296982] Mount-cache hash table entries: 512
[   17.297171] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[   17.297188] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   17.297191] CPU: L2 cache: 512K
[   17.297195] CPU: Hyper-Threading is disabled
[   17.297198] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00000400 00000000 00000000
[   17.297212] Compat vDSO mapped to ffffe000.
[   17.297231] Checking 'hlt' instruction... OK.
[   17.313038] SMP alternatives: switching to UP code
[   17.313295] Freeing SMP alternatives: 11k freed
[   17.313676] Early unpacking initramfs... done
[   17.766277] ACPI: Core revision 20070126
[   17.766882] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.953271] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 07
[   17.953324] Total of 1 processors activated (4044.09 BogoMIPS).
[   17.953439] ENABLING IO-APIC IRQs
[   17.953645] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.099518] Brought up 1 CPUs
[   18.099689] Booting paravirtualized kernel on bare hardware
[   18.099779] Time: 19:38:53  Date: 09/17/107
[   18.099815] NET: Registered protocol family 16
[   18.099951] EISA bus registered
[   18.099969] ACPI: bus type pci registered
[   18.114268] PCI: PCI BIOS revision 2.10 entry at 0xfaf20, last bus=1
[   18.114271] PCI: Using configuration type 1
[   18.114274] Setting up standard PCI resources
[   18.125129] ACPI: EC: Look up EC in DSDT
[   18.130541] ACPI: Interpreter enabled
[   18.130546] ACPI: (supports S0 S1 S4 S5)
[   18.130574] ACPI: Using IOAPIC for interrupt routing
[   18.138206] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.138215] PCI: Probing PCI hardware (bus 00)
[   18.138456] Enabling SiS 96x SMBus.
[   18.139372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.166570] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   18.166707] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   18.166840] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   18.166974] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[   18.167107] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[   18.167248] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   18.167401] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   18.167538] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   18.167680] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.167696] pnp: PnP ACPI init
[   18.167710] ACPI: bus type pnp registered
[   18.172149] pnp: PnP ACPI: found 13 devices
[   18.172153] ACPI: ACPI bus type pnp unregistered
[   18.172160] PnPBIOS: Disabled by ACPI PNP
[   18.172238] PCI: Using ACPI for IRQ routing
[   18.172243] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.183027] NET: Registered protocol family 8
[   18.183031] NET: Registered protocol family 20
[   18.183315] Time: tsc clocksource has been installed.
[   18.214036] PCI: Bridge: 0000:00:01.0
[   18.214039]   IO window: disabled.
[   18.214047]   MEM window: ec000000-edffffff
[   18.214053]   PREFETCH window: e0000000-e7ffffff
[   18.214087] NET: Registered protocol family 2
[   18.251260] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.251330] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   18.251499] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.251614] TCP: Hash tables configured (established 16384 bind 16384)
[   18.251618] TCP reno registered
[   18.263362] checking if image is initramfs... it is
[   18.714361] Switched to high resolution mode on CPU 0
[   19.156542] Freeing initrd memory: 7106k freed
[   19.157076] audit: initializing netlink socket (disabled)
[   19.157098] audit(1192649933.184:1): initialized
[   19.160536] VFS: Disk quotas dquot_6.5.1
[   19.160615] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.160761] io scheduler noop registered
[   19.160764] io scheduler anticipatory registered
[   19.160767] io scheduler deadline registered
[   19.160790] io scheduler cfq registered (default)
[   19.241327] Boot video device is 0000:01:00.0
[   19.241566] isapnp: Scanning for PnP cards...
[   19.595066] isapnp: No Plug & Play device found
[   19.631320] Real Time Clock Driver v1.12ac
[   19.631455] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.631569] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.631843] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.632793] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.633232] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.634336] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.634665] input: Macintosh mouse button emulation as /class/input/input0
[   19.634782] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   19.634785] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   19.635175] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.635183] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.635423] mice: PS/2 mouse device common for all mice
[   19.635590] EISA: Probing bus 0 at eisa.0
[   19.635601] Cannot allocate resource for EISA slot 1
[   19.635631] EISA: Detected 0 cards.
[   19.635904] TCP cubic registered
[   19.635926] NET: Registered protocol family 1
[   19.635958] Using IPI No-Shortcut mode
[   19.636178]   Magic number: 11:897:647
[   19.636296]   hash matches device ptydc
[   19.636992] Freeing unused kernel memory: 364k freed
[   19.672638] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.915882] AppArmor: AppArmor initialized<5>audit(1192649935.184:2):  type=1505 info="AppArmor initialized" pid=1179
[   20.928226] fuse init (API version 7.8)
[   20.936388] Failure registering capabilities with primary security module.
[   20.954832] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.736604] SCSI subsystem initialized
[   21.744084] libata version 2.21 loaded.
[   21.748894] pata_sis 0000:00:02.5: version 0.5.1
[   21.749089] scsi0 : pata_sis
[   21.749158] scsi1 : pata_sis
[   21.749299] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   21.749304] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   21.803861] usbcore: registered new interface driver usbfs
[   21.803900] usbcore: registered new interface driver hub
[   21.803932] usbcore: registered new device driver usb
[   21.805073] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.920651] ata1.00: ATA-7: Maxtor 2B020H1, WAK21R90, max UDMA/100
[   21.920657] ata1.00: 40020624 sectors, multi 16: LBA48 
[   21.920855] ata1.01: ATA-6: ST320410A, 5.33, max UDMA/100
[   21.920858] ata1.01: 39102336 sectors, multi 16: LBA 
[   21.928661] ata1.00: configured for UDMA/100
[   21.944724] ata1.01: configured for UDMA/100
[   22.595372] ata2.00: ATAPI: PIONEER DVD-RW  DVR-110D, 1.17, max UDMA/66
[   22.595381] ata2.01: ATAPI: LITE-ON CD-RW SOHR-5238S, 4S07, max UDMA/33
[   22.766928] ata2.00: configured for UDMA/66
[   22.938552] ata2.01: configured for UDMA/33
[   22.938738] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2B020H1   WAK2 PQ: 0 ANSI: 5
[   22.939350] scsi 0:0:1:0: Direct-Access     ATA      ST320410A        5.33 PQ: 0 ANSI: 5
[   22.945905] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-110D 1.17 PQ: 0 ANSI: 5
[   22.947152] scsi 1:0:1:0: CD-ROM            LITE-ON  CD-RW SOHR-5238S 4S07 PQ: 0 ANSI: 5
[   22.947741] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   22.947760] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   22.948199] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   22.948229] ohci_hcd 0000:00:03.0: irq 16, io mem 0xef001000
[   22.978302] sd 0:0:0:0: [sda] 40020624 512-byte hardware sectors (20491 MB)
[   22.978956] sd 0:0:0:0: [sda] Write Protect is off
[   22.978961] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.979003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.979102] sd 0:0:0:0: [sda] 40020624 512-byte hardware sectors (20491 MB)
[   22.979117] sd 0:0:0:0: [sda] Write Protect is off
[   22.979121] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.979146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.979152]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[   23.004393] hub 1-0:1.0: USB hub found
[   23.004407] hub 1-0:1.0: 2 ports detected
[   23.106185] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   23.106210] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   23.106244] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   23.106265] ohci_hcd 0000:00:03.1: irq 17, io mem 0xef002000
[   23.164007] usb usb2: configuration #1 chosen from 1 choice
[   23.164045] hub 2-0:1.0: USB hub found
[   23.164057] hub 2-0:1.0: 2 ports detected
[   23.265861] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   23.265885] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   23.265919] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   23.265940] ohci_hcd 0000:00:03.2: irq 18, io mem 0xef003000
[   23.323738] usb usb3: configuration #1 chosen from 1 choice
[   23.323783] hub 3-0:1.0: USB hub found
[   23.323796] hub 3-0:1.0: 2 ports detected
[   23.409433] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   23.426166] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   23.426187] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   23.426237] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   23.426285] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   23.426298] ehci_hcd 0000:00:03.3: irq 19, io mem 0xef004000
[   23.585109] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.585269] usb usb4: configuration #1 chosen from 1 choice
[   23.585308] hub 4-0:1.0: USB hub found
[   23.585320] hub 4-0:1.0: 6 ports detected
[   23.689220] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 20
[   23.689232] 3c59x: Donald Becker and others.
[   23.689240] 0000:00:0d.0: 3Com PCI 3c905C Tornado at e083a000.
[   23.992327] usb 1-1: device not accepting address 2, error -62
[   24.415528] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   24.477933]  sda1 sda2 < sda5 >
[   24.504115] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.504383] sd 0:0:1:0: [sdb] 39102336 512-byte hardware sectors (20020 MB)
[   24.504403] sd 0:0:1:0: [sdb] Write Protect is off
[   24.504407] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   24.504433] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.504508] sd 0:0:1:0: [sdb] 39102336 512-byte hardware sectors (20020 MB)
[   24.504523] sd 0:0:1:0: [sdb] Write Protect is off
[   24.504527] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   24.504551] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.504556]  sdb: sdb1
[   24.530987] sd 0:0:1:0: [sdb] Attached SCSI disk
[   24.538015] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.538207] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   24.538387] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   24.538580] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   24.548277] usb 4-1: configuration #1 chosen from 1 choice
[   24.548433] hub 4-1:1.0: USB hub found
[   24.548527] hub 4-1:1.0: 4 ports detected
[   24.587863] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   24.587871] Uniform CD-ROM driver Revision: 3.20
[   24.587965] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.593158] sr1: scsi3-mmc drive: 252x/52x writer cd/rw xa/form2 cdda tray
[   24.593242] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   24.866915] usb 4-1.1: new high speed USB device using ehci_hcd and address 3
[   24.991477] usb 4-1.1: configuration #1 chosen from 1 choice
[   25.020980] Attempting manual resume
[   25.020985] swsusp: Resume From Partition 8:5
[   25.020988] PM: Checking swsusp image.
[   25.021233] PM: Resume from disk failed.
[   25.080440] kjournald starting.  Commit interval 5 seconds
[   25.080459] EXT3-fs: mounted filesystem with ordered data mode.
[   25.210259] usb 4-1.3: new low speed USB device using ehci_hcd and address 4
[   25.324411] usb 4-1.3: configuration #1 chosen from 1 choice
[   25.537619] usb 4-1.4: new high speed USB device using ehci_hcd and address 5
[   25.646168] usb 4-1.4: configuration #1 chosen from 1 choice
[   25.646605] usbcore: registered new interface driver libusual
[   26.349752] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.349760] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.462327] Initializing USB Mass Storage driver...
[   26.462421] scsi2 : SCSI emulation for USB Mass Storage devices
[   26.462490] usb-storage: device found at 3
[   26.462492] usb-storage: waiting for device to settle before scanning
[   26.462523] usbcore: registered new interface driver usb-storage
[   26.462527] USB Mass Storage support registered.
[   31.451707] usb-storage: device scan complete
[   31.453195] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgent Go     100F PQ: 0 ANSI: 4
[   31.459652] sd 2:0:0:0: [sdc] Spinning up disk....ready
[   34.616269] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   34.620267] sd 2:0:0:0: [sdc] Write Protect is off
[   34.620284] sd 2:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   34.620288] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   34.624266] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   34.628246] sd 2:0:0:0: [sdc] Write Protect is off
[   34.628252] sd 2:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   34.628266] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   34.628277]  sdc: sdc1
[   34.682421] sd 2:0:0:0: [sdc] Attached SCSI disk
[   34.682488] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   37.363455] Linux agpgart interface v0.102 (c) Dave Jones
[   37.421605] agpgart: Detected SiS chipset - id:1606
[   37.426409] agpgart: AGP aperture is 64M @ 0xe8000000
[   37.454066] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.456493] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.611408] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
[   38.281146] nvidia: module license 'NVIDIA' taints kernel.
[   38.786006] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   38.786355] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   39.415331] input: PC Speaker as /class/input/input2
[   39.482226] Linux video capture interface: v2.00
[   39.698915] parport_pc 00:09: reported by Plug and Play ACPI
[   39.698967] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   39.907013] usbcore: registered new interface driver hiddev
[   39.910036] input: Logitech USB Receiver as /class/input/input3
[   39.910123] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:03.3-1.3
[   39.916929] input: Logitech USB Receiver as /class/input/input4
[   39.917061] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:03.3-1.3
[   39.917083] usbcore: registered new interface driver usbhid
[   39.917088] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.011173] saa7130/34: v4l2 driver version 0.2.14 loaded
[   40.011273] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 22
[   40.011285] saa7133[0]: found at 0000:00:0b.0, rev: 208, irq: 22, latency: 32, mmio: 0xef005000
[   40.011294] saa7133[0]: subsystem: 17de:7250, board: KWorld DVB-T 210 [card=114,autodetected]
[   40.011304] saa7133[0]: board init: gpio is 100
[   40.150959] saa7133[0]: i2c eeprom 00: de 17 50 72 ff ff ff ff ff ff ff ff ff ff ff ff
[   40.150975] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.150989] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.151002] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.151015] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.151029] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.151042] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.151055] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.172280] ieee80211_crypt: registered algorithm 'NULL'
[   40.305458] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   40.348274] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   40.348280] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   40.353376] tuner 1-004b: setting tuner address to 61
[   40.393312] tuner 1-004b: type set to tda8290+75a
[   40.529469] usb 4-1.4: reset high speed USB device using ehci_hcd and address 5
[   40.757177] zd1211rw 4-1.4:1.0: RF UNKNOWN_A_RF 0xa is not supported
[   40.844618] usb 4-1.4: reset high speed USB device using ehci_hcd and address 5
[   40.953286] usbcore: registered new interface driver zd1211rw
[   41.758694] tuner 1-004b: setting tuner address to 61
[   41.798618] tuner 1-004b: type set to tda8290+75a
[   43.119364] saa7133[0]: registered device video0 [v4l2]
[   43.119572] saa7133[0]: registered device vbi0
[   43.119763] saa7133[0]: registered device radio0
[   43.184077] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   43.507388] intel8x0_measure_ac97_clock: measured 52857 usecs
[   43.507393] intel8x0: clocking to 48000
[   43.546448] saa7134 ALSA driver for DMA sound loaded
[   43.546492] saa7133[0]/alsa: saa7133[0] at 0xef005000 irq 22 registered as card -2
[   43.618161] DVB: registering new adapter (saa7133[0]).
[   43.618170] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   43.687043] tda1004x: setting up plls for 48MHz sampling clock
[   44.672477] lp0: using parport0 (interrupt-driven).
[   44.747724] Adding 875500k swap on /dev/sda5.  Priority:-1 extents:1 across:875500k
[   45.150559] EXT3 FS on sda1, internal journal
[   45.679302] tda1004x: found firmware revision 23 -- ok
[   46.725845] No dock devices found.
[   46.887178] input: Power Button (FF) as /class/input/input5
[   46.893513] ACPI: Power Button (FF) [PWRF]
[   46.942401] input: Power Button (CM) as /class/input/input6
[   46.948656] ACPI: Power Button (CM) [PWRB]
[   46.997226] input: Sleep Button (CM) as /class/input/input7
[   47.003472] ACPI: Sleep Button (CM) [FUTS]
[   49.601501] eth0:  setting full-duplex.
[   51.217713] ppdev: user-space parallel port driver
[   52.086525] audit(1192649967.118:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5078 profile="/usr/sbin/cupsd"
[   52.292772] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   52.292780] apm: overridden by ACPI.
[   53.668799] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   53.668826] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   53.668884] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   55.615746] Failure registering capabilities with primary security module.
[   56.029819] Bluetooth: Core ver 2.11
[   56.030193] NET: Registered protocol family 31
[   56.030198] Bluetooth: HCI device and connection manager initialized
[   56.030203] Bluetooth: HCI socket layer initialized
[   56.057099] Bluetooth: L2CAP ver 2.8
[   56.057106] Bluetooth: L2CAP socket layer initialized
[   56.222472] Bluetooth: RFCOMM socket layer initialized
[   56.222852] Bluetooth: RFCOMM TTY layer initialized
[   56.222859] Bluetooth: RFCOMM ver 1.8
[   60.508402] NET: Registered protocol family 17
[   63.300620] NET: Registered protocol family 10
[   63.300866] lo: Disabled Privacy Extensions
[   73.829377] eth0: no IPv6 routers present
[  526.612360] eth0:  setting full-duplex.
[  526.612817] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  541.352850] eth0: no IPv6 routers present
richard@richard-desktop:~$

---

### Post by DenisTheinert on 2007-12-27
there are two options.

1. Add ID for Buffalo WLI-U2-KG54L to kernel.

```

static struct usb_device_id usb_ids[] = {
{ USB_DEVICE(0x0411, 0x00da), .driver_info = DEVICE_ZD1211B },
}

```

to /usr/src/linux/drivers/net/wireless/zd1211rw/zd_usb.c

2. Download 2.6.23 kernel ([www.kernel.org](www.kernel.org))

```

cd /usr/src/
tar jxf linux-2.6.23
ln -s /usr/src/linux-2.6.23 linux
cd linux
cp /boot/config-* .config
make oldconfig /* add your needs */
make-kpkg --initrd --revision=i686ver1 binary
dpkg -i ../kernel-image-linux-2.6.23.deb 

```

filenames may vary.

i post this information manly because the information in this thread and other threads did not work for me.
good luck ;)

---

### Post by gorby on 2008-01-07
Not sure why mines not working the code above is present in the version on compat wireless i just downloaded which compiled fine but i sill get the 
zd1211rw 1-6:1.0: RF UNKNOWN_A_RF 0xa is not supported msg. =s

---

### Post by stacka on 2008-01-26
Hi all,

got my  Buffalo wi-fi  WLI-U2-KG54L working this morning after a bit of fiddling.  I tried the 
deb package zd1211-firmware as suggested in some posts but had no joy.  in dmesg I was 
getting the 

zd1211rw 1-6:1.0: RF UNKNOWN_A_RF 0xa blah blah

error, and no wireless interface in the networking tools.  Following some advice on Japanese
posts i downloaded

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

after unpacking it 

bzip2 -d compat-wireless-2.6.tar.bz2
tar -xf compat-wireless-2.6.tar

i enter the directory created

cd compat-wireless-2.6

i installed with

make
sudo make install
sudo make load

(if you get an error complaining about the lack of a directory called 'build' then you need to 
download the kernel headers.  i think 'sudo aptitude install linux-headers' should do the trick)

now you just need to configure the wireless interface as usual (System -> Administration -> Network).

---

### Post by james waples on 2008-02-09
i managed to get a Buffalo WLI-U2-KG54L wireless USB stick working on 64studio 2.0.

get ndiswrapper and the driver downloadable from

cd to the directory after extraction and type

    make

and then as root

    make install

get the buffalo driver from

[http://www.buffalo-technology.com/support/getfile/?U2KG54_1-01-02-0002.zip](http://www.buffalo-technology.com/support/getfile/?U2KG54_1-01-02-0002.zip)

go into the [driver]/Win2000 folder and in a terminal type

     ndiswrapper -i NETU2G54.INF

check it detects the driver with

    ndiswrapper -l

it should show
    
    (driver present bla bla)
        (device present bla bla)

something like the above. 

if it does work, add to the bottom of /etc/modules

    modprobe ndiswrapper

and save. it should then work :confused:

i hope this helps and any errors that you may get, please return to me and i will try and sort it :lolflag:

james waples

---

### Post by james waples on 2008-02-09
really sorry, just for all you dullards out there, extract the buffalo driver first and cd into the U2KG54/Win2000/ folder

then ndiswrapper the .inf file using the -i suffix

---

