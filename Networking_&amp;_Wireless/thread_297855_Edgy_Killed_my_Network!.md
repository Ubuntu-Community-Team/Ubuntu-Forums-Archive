---
title: "Edgy Killed my Network!"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by KevinCLovesU on 2006-11-11
I just upgraded to Edgy using the update manager and now I cannot connect to the internet. Please help, I am willing to give any command line outputs if necessary. (I'm stuck on this windows machine. ugh.)

---

### Post by deepwave on 2006-11-11
Err... need more input ;-)

Did you have any errors when updating?  What device do use to connect to the Internet?  As for general console commands to play around with:

ifconfig (for checking the status network devices)
iwconfig (same thing but for wireless)
dmesg (kernel message, great if you expect a glaring error)

---

### Post by KevinCLovesU on 2006-11-11
I had no errors when updating, however I chose not to delete the "no longer supported by canonical" items.

I'm not sure what device I use to connect to the internet, as it's built in to my HP Pavillion notebook. My wireless router is a Linksys, but even a direct cat5 hookup won't work.

I don't see any errors in the outputs of those commands.


Obviously you know how much this sucks for me. I'll answer any questions you have. Hopefully we can get this fixed. Thanks in advance!

---

### Post by NorthCoast on 2006-11-11
^^What he said

from a console window do:
ifconfig
iwconfig (wireless)
route -n

we go from there.

---

### Post by KevinCLovesU on 2006-11-11
I'll get those outputs to you soon. BTW, we can rule out hardware failure as my Knoppix disc can get me on the network.

---

### Post by KevinCLovesU on 2006-11-11
Here you go.

```
kevin@kevin-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


kevin@kevin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


kevin@kevin-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


kevin@kevin-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
[17179569.184000]  BIOS-e820: 000000000bef0000 - 000000000beff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000beff000 - 000000000bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000bf00000 - 000000000c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 190MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 48880
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 44784 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7290
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0bef8cca
[17179569.184000] ACPI: FADT (v001 ATI    Raptor   0x06040000 ATI  0x000f4240) @ 0x0befee2b
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0befee9f
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x0befeec7
[17179569.184000] ACPI: DSDT (v001    ATI U1_M1535 0x06040000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3fc0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=1f91ecc3-aa44-4509-a9c2-1026368170a6 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01182000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1855.191 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.520000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.520000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179569.528000] Memory: 183060k/195520k available (1829k kernel code, 11948k reserved, 1038k data, 288k init, 0k highmem)
[17179569.528000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.608000] Calibrating delay using timer specific routine.. 3712.62 BogoMIPS (lpj=7425244)
[17179569.608000] Security Framework v1.0.0 initialized
[17179569.608000] SELinux:  Disabled at boot.
[17179569.608000] Mount-cache hash table entries: 512
[17179569.608000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[17179569.608000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[17179569.608000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.608000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.608000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[17179569.608000] CPU: AMD mobile AMD Athlon(tm) XP2500+ stepping 00
[17179569.608000] Checking 'hlt' instruction... OK.
[17179569.624000] SMP alternatives: switching to UP code
[17179569.624000] Freeing SMP alternatives: 0k freed
[17179569.624000] checking if image is initramfs... it is
[17179570.244000] Freeing initrd memory: 6628k freed
[17179570.244000] ACPI: Core revision 20060707
[17179570.244000] ACPI: Looking for DSDT ... not found!
[17179570.248000] ACPI: setting ELCR to 0200 (from 0e28)
[17179570.252000] NET: Registered protocol family 16
[17179570.252000] EISA bus registered
[17179570.252000] ACPI: bus type pci registered
[17179570.256000] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[17179570.256000] PCI: Using configuration type 1
[17179570.256000] Setting up standard PCI resources
[17179572.456000] ACPI: Interpreter enabled
[17179572.456000] ACPI: Using PIC for interrupt routing
[17179572.456000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.456000] PCI: Probing PCI hardware (bus 00)
[17179572.460000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:10.0
[17179572.460000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[17179572.460000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[17179572.460000] Boot video device is 0000:01:05.0
[17179572.460000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.460000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179572.460000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[17179572.460000] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[17179572.460000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *0, disabled.
[17179572.460000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *0, disabled.
[17179572.464000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[17179572.464000] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 *11)
[17179572.464000] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[17179572.464000] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[17179572.464000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[17179572.464000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179572.468000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.468000] pnp: PnP ACPI init
[17179572.472000] pnp: PnP ACPI: found 11 devices
[17179572.472000] PnPBIOS: Disabled by ACPI PNP
[17179572.472000] PCI: Using ACPI for IRQ routing
[17179572.472000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.472000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[17179572.472000] pnp: 00:07: ioport range 0x480-0x48f has been reserved
[17179572.472000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179572.472000] pnp: 00:07: ioport range 0x4d6-0x4d6 has been reserved
[17179572.472000] pnp: 00:07: ioport range 0x8000-0x807f could not be reserved
[17179572.476000] PCI: Bridge: 0000:00:01.0
[17179572.476000]   IO window: 9000-9fff
[17179572.476000]   MEM window: d0100000-d01fffff
[17179572.476000]   PREFETCH window: e0000000-efffffff
[17179572.476000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179572.476000]   IO window: 00001000-000010ff
[17179572.476000]   IO window: 00001400-000014ff
[17179572.476000]   PREFETCH window: 10000000-11ffffff
[17179572.476000]   MEM window: 12000000-13ffffff
[17179572.476000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[17179572.476000] PCI: setting IRQ 11 as level-triggered
[17179572.476000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[17179572.476000] NET: Registered protocol family 2
[17179572.512000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179572.512000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.512000] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.512000] TCP: Hash tables configured (established 8192 bind 4096)
[17179572.512000] TCP reno registered
[17179572.512000] Simple Boot Flag at 0x36 set to 0x1
[17179572.512000] audit: initializing netlink socket (disabled)
[17179572.512000] audit(1163298667.512:1): initialized
[17179572.512000] VFS: Disk quotas dquot_6.5.1
[17179572.512000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.512000] Initializing Cryptographic API
[17179572.512000] io scheduler noop registered
[17179572.512000] io scheduler anticipatory registered
[17179572.512000] io scheduler deadline registered
[17179572.512000] io scheduler cfq registered (default)
[17179572.512000] ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb.
[17179572.512000] Activating ISA DMA hang workarounds.
[17179572.512000] isapnp: Scanning for PnP cards...
[17179572.780000] isapnp: No Plug & Play device found
[17179572.804000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.804000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.804000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.804000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[17179572.804000] PCI: setting IRQ 3 as level-triggered
[17179572.804000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3
[17179572.804000] 0000:00:08.0: ttyS1 at I/O 0x8828 (irq = 3) is a 8250
[17179572.804000] 0000:00:08.0: ttyS2 at I/O 0x8840 (irq = 3) is a 8250
[17179572.804000] 0000:00:08.0: ttyS3 at I/O 0x8850 (irq = 3) is a 8250
[17179572.808000] Couldn't register serial port 0000:00:08.0: -28
[17179572.808000] mice: PS/2 mouse device common for all mice
[17179572.808000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.808000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.808000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.808000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179572.812000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.812000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.812000] EISA: Probing bus 0 at eisa.0
[17179572.812000] Cannot allocate resource for EISA slot 1
[17179572.812000] Cannot allocate resource for EISA slot 8
[17179572.812000] EISA: Detected 0 cards.
[17179572.812000] TCP bic registered
[17179572.812000] NET: Registered protocol family 1
[17179572.812000] NET: Registered protocol family 8
[17179572.812000] NET: Registered protocol family 20
[17179572.812000] Using IPI Shortcut mode
[17179572.812000] ACPI: (supports S0 S3 S4 S5)
[17179572.812000] Freeing unused kernel memory: 288k freed
[17179572.852000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.044000] Capability LSM initialized
[17179574.344000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179574.344000] ACPI: Thermal Zone [THRM] (70 C)
[17179574.676000] alim15x3: ATI Radeon IGP Northbridge is not yet fully tested.
[17179574.676000] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[17179574.676000] ACPI: Unable to derive IRQ for device 0000:00:10.0
[17179574.676000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[17179574.676000] ALI15X3: chipset revision 196
[17179574.676000] ALI15X3: not 100% native mode: will probe irqs later
[17179574.676000]     ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb:pio
[17179574.676000]     ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:pio, hdd:pio
[17179574.676000] Probing IDE interface ide0...
[17179575.008000] hda: TOSHIBA MK4025GAS, ATA DISK drive
[17179575.680000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.728000] Probing IDE interface ide1...
[17179576.464000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, ATAPI CD/DVD-ROM drive
[17179576.800000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.812000] hda: max request size: 128KiB
[17179576.820000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[17179576.820000] hda: cache flushes supported
[17179576.820000]  hda: hda1 hda2 < hda5 >
[17179576.916000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179576.916000] Uniform CD-ROM driver Revision: 3.20
[17179577.212000] usbcore: registered new driver usbfs
[17179577.212000] usbcore: registered new driver hub
[17179577.212000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.212000] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[17179577.212000] PCI: setting IRQ 10 as level-triggered
[17179577.212000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 10 (level, low) -> IRQ 10
[17179577.212000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179577.212000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179577.436000] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[17179577.492000] usb usb1: configuration #1 chosen from 1 choice
[17179577.492000] hub 1-0:1.0: USB hub found
[17179577.492000] hub 1-0:1.0: 4 ports detected
[17179577.748000] kjournald starting.  Commit interval 5 seconds
[17179577.748000] EXT3-fs: mounted filesystem with ordered data mode.
[17179594.012000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[17179594.012000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0024]
[17179594.012000] Yenta O2: res at 0x94/0xD4: 00/ea
[17179594.012000] Yenta O2: enabling read prefetch/write burst
[17179594.048000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.140000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[17179594.140000] Socket status: 30000007
[17179594.140000] agpgart: Detected Ati IGP320/M chipset
[17179594.148000] agpgart: AGP aperture is 64M @ 0xd4000000
[17179594.228000] input: PC Speaker as /class/input/input1
[17179594.272000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179594.272000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[17179594.360000] Real Time Clock Driver v1.12ac
[17179594.660000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[17179594.660000]   originally by Donald Becker <becker@scyld.com>
[17179594.660000]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
[17179594.660000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[17179594.660000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179594.660000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179594.660000] natsemi eth0: NatSemi DP8381[56] at 0xd0003000 (0000:00:12.0), 00:0d:9d:c8:f6:8b, IRQ 11, port TP.
[17179594.668000] parport: PnPBIOS parport detected.
[17179594.668000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179594.788000] FDC 0 is a post-1991 82077
[17179594.812000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.816000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.104000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179595.104000] PCI: setting IRQ 5 as level-triggered
[17179595.104000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[17179595.260000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[17179595.260000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179595.264000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.264000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.264000] cs: IO port probe 0xa00-0xaff: clean.
[17179595.548000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[17179595.584000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179595.632000] ts: Compaq touchscreen protocol output
[17179597.880000] AC'97 1 does not respond - RESET
[17179597.896000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179597.896000] ali mixer 1 creating error.
[17179598.056000] lp0: using parport0 (interrupt-driven).
[17179598.116000] Adding 554200k swap on /dev/disk/by-uuid/387399d5-8a02-49b7-a03c-c70fb771431f.  Priority:-1 extents:1 across:554200k
[17179598.200000] EXT3 FS on hda1, internal journal
[17179598.416000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179598.416000] md: bitmap version 4.39
[17179598.640000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179599.388000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179599.388000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179599.388000] ide: failed opcode was: unknown
[17179601.068000] NET: Registered protocol family 17
[17179606.028000] ACPI: AC Adapter [ACAD] (on-line)
[17179606.068000] ACPI: Battery Slot [BAT1] (battery present)
[17179606.084000] ACPI: Power Button (FF) [PWRF]
[17179606.084000] ACPI: Power Button (CM) [PWRB]
[17179606.084000] ACPI: Lid Switch [LID]
[17179606.196000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179606.196000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[17179606.196000] ACPI Exception (evxface-0545): AE_BAD_PARAMETER, Removing notify handler [20060707]
[17179606.224000] pcc_acpi: loading...
[17179606.336000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179606.640000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[17179606.640000] Detected 1855.460 MHz processor.
[17179606.664000] powernow: No PST tables match this cpuid (0x7a0)
[17179606.664000] powernow: This is indicative of a broken BIOS.
[17179606.664000] powernow: Trying ACPI perflib
[17179606.664000] powernow: Minimum speed 530 MHz. Maximum speed 1855 MHz.
[17179609.896000] [drm] Initialized drm 1.0.1 20051102
[17179610.104000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179610.104000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179610.108000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179611.132000] mtrr: 0xe0000000,0x10000000 overlaps existing 0xe0000000,0x4000000
[17179611.132000] mtrr: 0xe0000000,0x10000000 overlaps existing 0xe0000000,0x4000000
[17179611.132000] mtrr: 0xe0000000,0x10000000 overlaps existing 0xe0000000,0x4000000
[17179611.132000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179611.132000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179611.132000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[17179611.308000] [drm] Setting GART location based on new memory map
[17179611.308000] [drm] writeback test succeeded in 1 usecs
[17179611.372000] apm: BIOS not found.
[17179615.936000] Bluetooth: Core ver 2.8
[17179615.936000] NET: Registered protocol family 31
[17179615.936000] Bluetooth: HCI device and connection manager initialized
[17179615.936000] Bluetooth: HCI socket layer initialized
[17179616.000000] Bluetooth: L2CAP ver 2.8
[17179616.000000] Bluetooth: L2CAP socket layer initialized
[17179616.052000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179616.080000] Bluetooth: RFCOMM socket layer initialized
[17179616.080000] Bluetooth: RFCOMM TTY layer initialized
[17179616.080000] Bluetooth: RFCOMM ver 1.7
[17179625.340000] NET: Registered protocol family 10
[17179625.340000] lo: Disabled Privacy Extensions
[17179625.340000] IPv6 over IPv4 tunneling driver
```

---

### Post by trubblemaker on 2006-11-11
yeah I'm going to say that more input is needed.  for some unknown reason your wireless driver isn't loading. So show me this
```

cat /etc/network/interfaces   # will tell me what interface you use to use
lspci                         # will tell me what hardware you have
ndiswrapper -l                # just incase you used to use ndiswrapper
```

**IF** you did use to use ndiswrapper, you should completely remove it and you should reinstall it from source, see the last link in my signature for an easy howto.

---

### Post by deepwave on 2006-11-12
One thing that looks worrying for me, is that you only have lo as a device.

lo being a kernel provided loopback device.  Since you can do both wireless and direct cat5 hookup (a.k.a. ethernet), you should have at least a eth0 entry in ifconfig.

Also since you said Knoppix works, try using it to get info too.  That way you can compare the two results.  Good news is that if Knoppix works, you will be able to get it running under Ubuntu.

---

### Post by KevinCLovesU on 2006-11-12
Trubble, I will try that if i must, but not now.

Deepwave, I too notice the lack of eth0, but being the n00b I am, I have no idea where to go from there.

Here's the output from knoppix.

```
knoppix@1[knoppix]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:C8:F6:8B
          inet addr:192.168.1.104  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:3683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2420411 (2.3 MiB)  TX bytes:572155 (558.7 KiB)
          Interrupt:11 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1000 (1000.0 b)  TX bytes:1000 (1000.0 b)
```

---

### Post by trubblemaker on 2006-11-12
> **deepwave said:**
> One thing that looks worrying for me, is that you only have lo as a device.


not really a worry, I have pre-up commands in my "/etc/network/interface" and if they fail I only have lo show up, not really an issue, they just aren't loaded.  This is an issue of drivers, not loading. don't worry about the script the output from 
```

cat /etc/network/interfaces   # will tell me what interface you use to use
lspci                         # will tell me what hardware you have

``` 

will really tell the story of what's up with your network.  dmesg *should* have said something, but..... it's not so lets see 
what your have for hardware, 
```
lspci                        
```
and what you used to for connecting, 
```
cat /etc/network/interfaces
```
and then we'll take it from there..... and FYI the lspci can be done in knoppix if that helps, /etc/network/interfaces, needs to be read from ubuntu or if you mount your hard drive in knoppix. (the following commands will work if you only have one partition for your hard drive, if you have more it's more complicated.)
```

mkdir old
mount /dev/hda1 old
cat old/etc/network/interfaces

```

---

### Post by KevinCLovesU on 2006-11-12
Here you are:

(output from cat old/etc/network/interfaces)
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid Linksys




auto wlan0

```

And from lspci (please note that I did not have my wifi adapter connected at the time of giving the command, just a cat5.)

```

knoppix@2[knoppix]$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

```


thx

---

### Post by deepwave on 2006-11-12
> **KevinCLovesU said:**
> Here you are:

(output from cat old/etc/network/interfaces)
```



iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```

And from lspci (please note that I did not have my wifi adapter connected at the time of giving the command, just a cat5.)

```

knoppix@2[knoppix]$ lspci
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

```


Well one thing you can add is auto eth0 to your /etc/network/interfaces.  Just like that the auto eth1.  But that is minor.

And you know what Ethernet device you have.  Now you things you might need:
- the kernel module for that device.  lsmod gives you the current running kernel modules.

---

### Post by deepwave on 2006-11-12
Some looking around and I found:

The kernel module (if the Ubuntu kernel compiled that driver as a module) most likely is dp83815.

This tool/package might help: nictools-pci.  I never tried it out, but it claims to have a diagnosis tool for several cards including the MacPhyter card.  Might be a problem to get, if your Ubuntu network does not work... :-k 

A guess you can always try (in Ubuntu):
modprobe dp83815
/etc/init.d/networking restart

See if that gets your network working under Ubuntu.

---

### Post by trubblemaker on 2006-11-12
[QUOTE=KevinCLovesU;1748616]Here you are:

(output from cat old/etc/network/interfaces)
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


```

keys so the issue is like deepwave said, you need the auto on your "auto eth0" for your interface to come up on boot.  Hence you not having it when you type "ifconfig" 
you can manually bring it up with:
```
sudo ifconfig eth0 up
sudo dhclient eth0
```
if you need help with wireless, post back, it does look like your using ndiswrapper, so unfortunately if it's not working out of the box after upgrade try the 'from source',  in my sig, and serioiusly don't be afraid., it's 10 steps and really is a nood, styled script without any scaryness.

---

### Post by KevinCLovesU on 2006-11-12
Okay trubble, "ifconfig eth0 up" DOES make my network work! However, I cannot make this stay, when the computer is restarted, the command must be repeated. How is this fixed?

Also, wlan0 does not work. You keep telling me to compile ndis from source, but ndiswrapper -l tells me that the drivers and hardware are present. Your how to also makes references to broadcom chips, but I have an atheros. (Specifically, Netgeard WG111T.)

---

### Post by trubblemaker on 2006-11-12
For wireless

[INDENT]sorry never seen wlan0 used for aethos, but, the upgrade breaks ndiswrapper so don't listen to what it says, it's not loading,,,, wait, it's not loaded try 
```

sudo rmmod madwifi
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifup wlan0

```
[/INDENT]

**to fix it on boot and clean up your /etc/network/interfaces**
[INDENT](deep wave was on the right track)
```

auto lo **eth0 wlan0**

iface lo inet loopback

iface eth0 inet dhcp

# this is a duplicate that's installed auto by kernel, for your aethos card but as your not using it comment it out, or comment out wlan0
#auto ath0
#iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Linksys


```

if this works you need to uninstall madwifi or ndiswrapper.  pick they don't play nice together.  I'd probably use madwifi, because it's better native support, ndiswrapper isn't bad but it's not as specific as madwifi.[/INDENT]

---

