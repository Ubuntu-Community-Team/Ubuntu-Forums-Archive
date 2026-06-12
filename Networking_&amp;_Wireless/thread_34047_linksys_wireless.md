---
title: "linksys wireless"
date: 2005-05-13
forum: Networking &amp; Wireless
---

### Post by simple on 2005-05-13
hmm, kubuntu isn't detecting my wireless pci card, it's wrt54g linksys, i think >> not so sure that's the card..and i have ndiswarpper on a cd, i untar it and goto the terminal to make install, but it's saying my pass is wrong when i do su and try to "authenticate"..so where can i edit the pass i guess or see what it is.. and alos, i have the cd and it has the driver i need, bcmwl5 i think it is if my memory is right, do i need ndiswrapper?

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=simple]do i need ndiswrapper?[/QUOTE]

yes. This might help. I am also asking jdong for a new ndiswrapper backport.

[http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wrt54g](http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wrt54g)

---

### Post by simple on 2005-05-13
[QUOTE=poofyhairguy]yes. This might help. I am also asking jdong for a new ndiswrapper backport.

[http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wrt54g](http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wrt54g)[/QUOTE]
thank you, i can set up ndiswrapper and the write driver and all..but when i try to "make install" in ndiswrapper, i get these errors
> make -c driver install
make[1]: entering directory 'home/simple/ndiswrapper-0.11/driver'
make -c /lib/modules/2.6.10-5-386/build subdirs=/home/simple/ndiswrapper-0.11/driver \
      ndiswrapper_version =0.11 \
      extra_version= modules
make = *** /lib/modules/2.610-5-386/build: no such file or dir. stop.
make entering an unkown dir/make: leaving an unknown dir
dirmake [1] *** [defualt] error 2
make [1] : leave dir 'home/simple/ndiswerapper-0.11/driver'
make *** [install] error 2

---

### Post by xristos on 2005-05-13
I think you should apt-get install the source files of your kernel !

---

### Post by simple on 2005-05-13
[QUOTE=xristos]I think you should apt-get install the source files of your kernel ![/QUOTE]that shouldn't be too hard without internet access. i installed kubuntu straight from the install cd, why isn't that taken care of.

---

### Post by simple on 2005-05-13
no?

---

### Post by simple on 2005-05-13
i've gone through getting the kernel hearders, needed to get build-essentials, and still having an erro > make -C driver install
make[1]: Entering directory `/home/simple/ndiswrapper-0.11/driver'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/simple/ndiswrapper-0.11/driver \
        NDISWRAPPER_VERSION=0.11 \
        EXTRA_VERSION= modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/simple/ndiswrapper-0.11/driver/wrapper.o
/home/simple/ndiswrapper-0.11/driver/wrapper.c: In function `ndis_suspend_pci':
/home/simple/ndiswrapper-0.11/driver/wrapper.c:930: error: too many arguments to function `pci_save_state'
/home/simple/ndiswrapper-0.11/driver/wrapper.c: In function `ndis_resume_pci':
/home/simple/ndiswrapper-0.11/driver/wrapper.c:957: error: too many arguments to function `pci_restore_state'
/home/simple/ndiswrapper-0.11/driver/wrapper.c: In function `ndis_init_one_pci':
/home/simple/ndiswrapper-0.11/driver/wrapper.c:1525: error: too many arguments to function `pci_restore_state'
make[3]: *** [/home/simple/ndiswrapper-0.11/driver/wrapper.o] Error 1
make[2]: *** [_module_/home/simple/ndiswrapper-0.11/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/simple/ndiswrapper-0.11/driver'
make: *** [install] Error 2

---

### Post by simple on 2005-05-13
>    1.
      bcwml5  invalid driver!
   2.
      root@simpleb0x:/home/simple/ndiswrapper-0.11 # modprobe ndsiwrapper
   3.
      FATAL: Module ndsiwrapper not found.
   4.
      root@simpleb0x:/home/simple/ndiswrapper-0.11 # modprobe ndiswrapper
   5.
      FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)
   6.
      root@simpleb0x:/home/simple/ndiswrapper-0.11 # dmesg
   7.
       (ACPI data)
   8.
       BIOS-e820: 000000001f7ce000 - 000000001f7f0000 (ACPI NVS)
   9.
       BIOS-e820: 000000001f7f0000 - 000000001f800000 (reserved)
  10.
       BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
  11.
      503MB LOWMEM available.
  12.
      found SMP MP-table at 000ff780
  13.
      On node 0 totalpages: 128960
  14.
        DMA zone: 4096 pages, LIFO batch:1
  15.
        Normal zone: 124864 pages, LIFO batch:16
  16.
        HighMem zone: 0 pages, LIFO batch:1
  17.
      DMI 2.3 present.
  18.
      ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb5f0
  19.
      ACPI: RSDT (v001 A M I  OEMRSDT  0x02000516 MSFT 0x00000097) @ 0x1f7c0000
  20.
      ACPI: FADT (v001 A M I  OEMFACP  0x02000516 MSFT 0x00000097) @ 0x1f7c0200
  21.
      ACPI: MADT (v001 A M I  OEMAPIC  0x02000516 MSFT 0x00000097) @ 0x1f7c0390
  22.
      ACPI: OEMB (v001 A M I  AMI_OEM  0x02000516 MSFT 0x00000097) @ 0x1f7ce040
  23.
      ACPI: MCFG (v001 A M I  OEMMCFG  0x02000516 MSFT 0x00000097) @ 0x1f7c47f0
  24.
      ACPI: DSDT (v001  A0005 A0005074 0x00000074 INTL 0x02002026) @ 0x00000000
  25.
      ACPI: PM-Timer IO Port: 0x808
  26.
      ACPI: Local APIC address 0xfee00000
  27.
      ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
  28.
      Processor #0 15:4 APIC version 20
  29.
      ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
  30.
      Processor #1 15:4 APIC version 20
  31.
      WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
  32.
      ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
  33.
      IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
  34.
      ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
  35.
      ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
  36.
      ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
  37.
      ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
  38.
      ACPI: IRQ0 used by override.
  39.
      ACPI: IRQ2 used by override.
  40.
      ACPI: IRQ9 used by override.
  41.
      Enabling APIC mode:  Flat.  Using 1 I/O APICs
  42.
      Using ACPI (MADT) for SMP configuration information
  43.
      Built 1 zonelists
  44.
      Kernel command line: root=/dev/sda1 ro quiet splash
  45.
      mapped APIC to ffffd000 (fee00000)
  46.
      mapped IOAPIC to ffffc000 (fec00000)
  47.
      Initializing CPU#0
  48.
      PID hash table entries: 2048 (order: 11, 32768 bytes)
  49.
      Detected 2801.438 MHz processor.
  50.
      Using pmtmr for high-res timesource
  51.
      Console: colour VGA+ 80x25
  52.
      Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
  53.
      Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
  54.
      Memory: 503836k/515840k available (1436k kernel code, 11448k reserved, 754k data, 224k init, 0k highmem)
  55.
      Checking if this processor honours the WP bit even in supervisor mode... Ok.
  56.
      Calibrating delay loop... 5537.79 BogoMIPS (lpj=2768896)
  57.
      Security Framework v1.0.0 initialized
  58.
      SELinux:  Disabled at boot.
  59.
      Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
  60.
      CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000
  61.
      CPU: After vendor identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000
  62.
      monitor/mwait feature present.
  63.
      using mwait in idle threads.
  64.
      CPU: Trace cache: 12K uops, L1 D cache: 16K
  65.
      CPU: L2 cache: 1024K
  66.
      CPU: After all inits, caps: bfebfbff 00100000 00000000 00000080 0000441d 00000000
  67.
      CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
  68.
      Enabling fast FPU save and restore... done.
  69.
      Enabling unmasked SIMD FPU exception support... done.
  70.
      Checking 'hlt' instruction... OK.
  71.
      Checking for popad bug... OK.
  72.
      ACPI: Looking for DSDT in initrd... not found!
  73.
      ENABLING IO-APIC IRQs
  74.
      ..TIMER: vector=0x31 pin1=2 pin2=-1
  75.
      checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
  76.
      Freeing initrd memory: 4336k freed
  77.
      NET: Registered protocol family 16
  78.
      EISA bus registered
  79.
      PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
  80.
      PCI: Using MMCONFIG
  81.
      mtrr: v2.0 (20020519)
  82.
      ACPI: Subsystem revision 20050211
  83.
      ACPI: Interpreter enabled
  84.
      ACPI: Using IOAPIC for interrupt routing
  85.
      ACPI: PCI Root Bridge [PCI0] (00:00)
  86.
      PCI: Probing PCI hardware (bus 00)
  87.
      PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
  88.
      PCI: Transparent bridge - 0000:00:1e.0
  89.
      ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
  90.
      ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
  91.
      ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
  92.
      ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
  93.
      ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
  94.
      ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
  95.
      ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
  96.
      ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
  97.
      ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
  98.
      ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
  99.
      Linux Plug and Play Support v0.97 (c) Adam Belay
 100.
      pnp: PnP ACPI init
 101.
      pnp: PnP ACPI: found 17 devices
 102.
      PnPBIOS: Disabled by ACPI PNP
 103.
      PCI: Using ACPI for IRQ routing
 104.
      ** PCI interrupts are no longer routed automatically.  If this
 105.
      ** causes a device to stop working, it is probably because the
 106.
      ** driver failed to call pci_enable_device().  As a temporary
 107.
      ** workaround, the "pci=routeirq" argument restores the old
 108.
      ** behavior.  If this argument makes the device work again,
 109.
      ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
 110.
      ** so I can fix the driver.
 111.
      pnp: 00:07: ioport range 0x680-0x6ff has been reserved
 112.
      audit: initializing netlink socket (disabled)
 113.
      audit(1115998781.184:0): initialized
 114.
      VFS: Disk quotas dquot_6.5.1
 115.
      Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 116.
      devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
 117.
      devfs: boot_options: 0x0
 118.
      Initializing Cryptographic API
 119.
      isapnp: Scanning for PnP cards...
 120.
      isapnp: No Plug & Play device found
 121.
      serio: i8042 AUX port at 0x60,0x64 irq 12
 122.
      serio: i8042 KBD port at 0x60,0x64 irq 1
 123.
      Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
 124.
      io scheduler noop registered
 125.
      io scheduler anticipatory registered
 126.
      io scheduler deadline registered
 127.
      io scheduler cfq registered
 128.
      RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
 129.
      input: AT Translated Set 2 keyboard on isa0060/serio0
 130.
      EISA: Probing bus 0 at eisa0
 131.
      EISA: Detected 0 cards.
 132.
      NET: Registered protocol family 2
 133.
      IP: routing cache hash table of 4096 buckets, 32Kbytes
 134.
      TCP: Hash tables configured (established 32768 bind 65536)
 135.
      NET: Registered protocol family 8
 136.
      NET: Registered protocol family 20
 137.
      Restarting tasks...<6> Strange, kswapd0 not stopped
 138.
      Strange, kseriod not stopped
 139.
      done
 140.
      ACPI wakeup devices:
 141.
      P0P1 P0P3 BNIC P0P4 P0P5 P0P6 P0P7 PS2K PS2M USB1 USB2 USB3 USB4 EUSB MC97
 142.
      ACPI: (supports S0 S1 S3 S4 S5)
 143.
      RAMDISK: cramfs filesystem found at block 0
 144.
      RAMDISK: Loading 4336KiB [1 disk] into ram disk... done.
 145.
      VFS: Mounted root (cramfs filesystem) readonly.
 146.
      Freeing unused kernel memory: 224k freed
 147.
      ACPI: Processor [CPU1] (supports 8 throttling states)
 148.
      NET: Registered protocol family 1
 149.
      SCSI subsystem initialized
 150.
      libata version 1.10 loaded.
 151.
      ata_piix version 1.03
 152.
      ACPI: PCI interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
 153.
      PCI: Setting latency timer of device 0000:00:1f.2 to 64
 154.
      ata1: SATA max UDMA/133 cmd 0xC080 ctl 0xC002 bmdma 0xB800 irq 19
 155.
      ata2: SATA max UDMA/133 cmd 0xBC00 ctl 0xB882 bmdma 0xB808 irq 19
 156.
      ata1: dev 0 cfg 49:2f00 82:3069 83:7c01 84:4003 85:3069 86:3c01 87:4003 88:203f
 157.
      ata1: dev 0 ATA, max UDMA/100, 390721968 sectors: lba48
 158.
      ata1: dev 0 configured for UDMA/100
 159.
      scsi0 : ata_piix
 160.
      ATA: abnormal status 0x7F on port 0xBC07
 161.
      ata2: disabling port
 162.
      scsi1 : ata_piix
 163.
      elevator: using anticipatory as default io scheduler
 164.
        Vendor: ATA       Model: ST3200822AS       Rev: 3.02
 165.
        Type:   Direct-Access                      ANSI SCSI revision: 05
 166.
      Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
 167.
      ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
 168.
      usbcore: registered new driver usbfs
 169.
      usbcore: registered new driver hub
 170.
      Initializing USB Mass Storage driver...
 171.
      usbcore: registered new driver usb-storage
 172.
      USB Mass Storage support registered.
 173.
      SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
 174.
      SCSI device sda: drive cache: write back
 175.
      SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
 176.
      SCSI device sda: drive cache: write back
 177.
      /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
 178.
      Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
 179.
      Stopping tasks: ===|
 180.
      Freeing memory... done (487 pages freed)
 181.
      Restarting tasks... done
 182.
      EXT3-fs: mounted filesystem with ordered data mode.
 183.
      kjournald starting.  Commit interval 5 seconds
 184.
      Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1
 185.
      EXT3 FS on sda1, internal journal
 186.
      Probing IDE interface ide0...
 187.
      hda: HP DVD Writer 630, ATAPI CD/DVD-ROM drive
 188.
      hdb: CRD-8322B, ATAPI CD/DVD-ROM drive
 189.
      Probing IDE interface ide1...
 190.
      Probing IDE interface ide2...
 191.
      Probing IDE interface ide3...
 192.
      Probing IDE interface ide4...
 193.
      Probing IDE interface ide5...
 194.
      ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
 195.
      hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
 196.
      Uniform CD-ROM driver Revision: 3.20
 197.
      hdb: ATAPI 32X CD-ROM drive, 128kB Cache
 198.
      parport: PnPBIOS parport detected.
 199.
      parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
 200.
      lp0: using parport0 (interrupt-driven).
 201.
      mice: PS/2 mouse device common for all mice
 202.
      input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
 203.
      ts: Compaq touchscreen protocol output
 204.
      ieee1394: Initialized config rom entry `ip1394'
 205.
      sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
 206.
      Capability LSM initialized
 207.
      device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
 208.
      md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
 209.
      cdrom: open failed.
 210.
      Real Time Clock Driver v1.12
 211.
      input: PC Speaker
 212.
      inserting floppy driver for 2.6.10-5-386
 213.
      Floppy drive(s): fd0 is 1.44M
 214.
      FDC 0 is a post-1991 82077
 215.
      Linux agpgart interface v0.100 (c) Dave Jones
 216.
      agpgart: Detected an Intel 915G Chipset.
 217.
      agpgart: Maximum main memory to use for agp memory: 431M
 218.
      agpgart: Detected 7932K stolen memory.
 219.
      agpgart: AGP aperture is 256M @ 0xd0000000
 220.
      cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
 221.
      pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 222.
      shpchp: shpc_init : shpc_cap_offset == 0
 223.
      shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
 224.
      Evaluate _OSC Set fails. Status = 0x0005
 225.
      pciehp: add_host_bridge: status 5
 226.
      pciehp: Fails to gain control of native hot-plug
 227.
      USB Universal Host Controller Interface driver v2.2
 228.
      ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
 229.
      uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
 230.
      PCI: Setting latency timer of device 0000:00:1d.0 to 64
 231.
      uhci_hcd 0000:00:1d.0: irq 23, io base 0xc400
 232.
      uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
 233.
      hub 1-0:1.0: USB hub found
 234.
      hub 1-0:1.0: 2 ports detected
 235.
      ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
 236.
      uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
 237.
      PCI: Setting latency timer of device 0000:00:1d.1 to 64
 238.
      uhci_hcd 0000:00:1d.1: irq 19, io base 0xc480
 239.
      uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
 240.
      hub 2-0:1.0: USB hub found
 241.
      hub 2-0:1.0: 2 ports detected
 242.
      ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
 243.
      uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
 244.
      PCI: Setting latency timer of device 0000:00:1d.2 to 64
 245.
      uhci_hcd 0000:00:1d.2: irq 18, io base 0xc800
 246.
      uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
 247.
      hub 3-0:1.0: USB hub found
 248.
      hub 3-0:1.0: 2 ports detected
 249.
      ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
 250.
      uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
 251.
      PCI: Setting latency timer of device 0000:00:1d.3 to 64
 252.
      uhci_hcd 0000:00:1d.3: irq 16, io base 0xc880
 253.
      uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
 254.
      hub 4-0:1.0: USB hub found
 255.
      hub 4-0:1.0: 2 ports detected
 256.
      usb 4-1: new full speed USB device using uhci_hcd and address 2
 257.
      ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
 258.
      ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
 259.
      PCI: Setting latency timer of device 0000:00:1d.7 to 64
 260.
      ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xcfe37c00
 261.
      ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
 262.
      PCI: cache line size of 128 is not supported by device 0000:00:1d.7
 263.
      ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
 264.
      hub 5-0:1.0: USB hub found
 265.
      hub 5-0:1.0: 8 ports detected
 266.
      hw_random: RNG not detected
 267.
      ICH6: IDE controller at PCI slot 0000:00:1f.1
 268.
      ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
 269.
      ICH6: chipset revision 3
 270.
      ICH6: not 100% native mode: will probe irqs later
 271.
      ICH6: port 0x01f0 already claimed by ide0
 272.
      ICH6: neither IDE port enabled (BIOS)
 273.
      usb 4-1: device not accepting address 2, error -71
 274.
      ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
 275.
      ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 20 (level, low) -> IRQ 20
 276.
      ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[cffff800-cfffffff]  Max Packet=[2048]
 277.
      usb 4-1: new full speed USB device using uhci_hcd and address 4
 278.
      8139too Fast Ethernet driver 0.9.27
 279.
      ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 21
 280.
      eth0: RealTek RTL8139 at 0xe800, 00:11:d8:18:c3:9b, IRQ 21
 281.
      eth0:  Identified 8139 chip type 'RTL-8101'
 282.
      8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
 283.
      scsi2 : SCSI emulation for USB Mass Storage devices
 284.
      usb-storage: device found at 4
 285.
      usb-storage: waiting for device to settle before scanning
 286.
      eth0: link down
 287.
      ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000bc21d4]
 288.
      NET: Registered protocol family 17
 289.
        Vendor: Generic   Model: USB SD Reader     Rev: 1.00
 290.
        Type:   Direct-Access                      ANSI SCSI revision: 00
 291.
      Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
 292.
        Vendor: Generic   Model: USB CF Reader     Rev: 1.01
 293.
        Type:   Direct-Access                      ANSI SCSI revision: 00
 294.
      Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 1
 295.
        Vendor: Generic   Model: USB SM Reader     Rev: 1.02
 296.
        Type:   Direct-Access                      ANSI SCSI revision: 00
 297.
      Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 2
 298.
        Vendor: Generic   Model: USB MS Reader     Rev: 1.03
 299.
        Type:   Direct-Access                      ANSI SCSI revision: 00
 300.
      Attached scsi removable disk sde at scsi2, channel 0, id 0, lun 3
 301.
      usb-storage: device scan complete
 302.
      ACPI: Power Button (FF) [PWRF]
 303.
      ibm_acpi: ec object not found
 304.
      apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
 305.
      apm: overridden by ACPI.
 306.
      NET: Registered protocol family 10
 307.
      Disabled Privacy Extensions on device c02f0500(lo)
 308.
      IPv6 over IPv4 tunneling driver
 309.
      eth0: no IPv6 routers present
 310.
      UDF-fs: No VRS found
 311.
      ISO 9660 Extensions: Microsoft Joliet Level 3
 312.
      ISOFS: changing to secondary root
 313.
      ndiswrapper: Unknown symbol task_nice
 314.
      ndiswrapper: Unknown symbol task_nice
 315.
      ndiswrapper: Unknown symbol task_nice
 316.
      ndiswrapper: Unknown symbol task_nice
 317.
      ndiswrapper: Unknown symbol task_nice
 318.
      ndiswrapper: Unknown symbol task_nice
 319.
      ndiswrapper: Unknown symbol task_nice
 320.
      UDF-fs: No VRS found
 321.
      ISO 9660 Extensions: Microsoft Joliet Level 3
 322.
      ISOFS: changing to secondary root
 323.
      ndiswrapper: Unknown symbol task_nice  k thakns for the responses, i've gone and edited the wrapper.c file, and got ndiswrapper installed, then try doing stuff and it just isn't happening. whatever

---

### Post by simple on 2005-05-13
gah, last error i hope, and a respone i'm hoping too...when i try to do "modprobe ndiswrapper" > FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)is the error message, i did a google search and there was two results, both from this board but the french one
edit...i followed the guide [ndiswrapper and bcmwlf guide](http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10) completely...

---

### Post by xjb2003x on 2005-05-14
Whenever I go through the steps in [http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10)
I get the same error message you did whenever you went to do 

sudo modprobe ndiswapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Did you happen to find a fix?

---

### Post by xristos on 2005-05-14
[QUOTE=xjb2003x]FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/QUOTE]

Are you root when you do that ?
To be root type sudo -s -H and enter the password of your normal user account

---

### Post by simple on 2005-05-18
[QUOTE=xristos]Are you root when you do that ?
To be root type sudo -s -H and enter the password of your normal user account[/QUOTE]
 well my fix was a fresh install of kubuntu, installing ndiswrapper from kynaptic and on my way... then it was fine

---

### Post by djpharoah on 2005-05-18
your getting that error when ever you run 
```
modprobe ndiswrapper
``` 
because the bcmwl5.inf file that you used is either corrupted or not the same for your chipset.

i had the same problem when i tried installing my Linksys WPC54GS card, i used the bcmwl5a.inf from the cd which somehow didnt work..so i used a generic Belkin bcmwl5a.inf from the net a...

and voilaa

---

