---
title: "ISA ethernet card not appearing"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by lo_mein_dreams on 2007-09-25
Here it goes:

I have a E2000Cplus ISA ethernet card and it does not show up on my ubuntu 6.10 machine. I am not sure why, it actually did show up in the network connections once the last time I installed, for some arbitrary reason I cannot figure out, but that was temporary.

I know the card works because under windows 98 everything is fine.

I've "used" linux off and on for a while, but I haven't done anything in depth.

Here are some outputs (I'm not sure which ones I should give):

```
sudo lshw
felix                     
    description: Mini Tower Computer
    product: 2153E3U
    vendor: IBM
    version: 0000000000000000
    serial: AF248KR
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.0
    configuration: chassis=mini-tower
  *-core
       description: Motherboard
       product: 0000000000000000
       vendor: 0000000000000000
       physical id: 0
       version: 0000000000000000
       serial: 0000000000000000
     *-firmware
          description: BIOS
          vendor: ACER
          physical id: 0
          version: V3.2 V70EN8A (10/29/98)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video
     *-cpu
          description: CPU
          product: AMD-K6(tm) 3D processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 400
          bus info: cpu@0
          version: 5.8.12
          slot: Socket 7
          size: 450MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 pge mmx syscall 3dnow k6_mtrr up
        *-cache
             description: L1 cache
             physical id: 0
             size: 64KB
     *-memory:0 UNCLAIMED
          product: Standard EDO ECC DIMM Memory Controller
          physical id: 500
          capacity: 256MB
     *-memory:1 UNCLAIMED
          product: Standard SDRAM Memory Controller
          physical id: 87
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: M1541
          vendor: ALi Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e7ffffff
        *-pci
             description: PCI bridge
             product: M1541 PCI to AGP Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master vga_palette
           *-display
                description: VGA compatible controller
                product: 3D Rage Pro AGP 1X/2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 5c
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master vga_palette cap_list
                resources: iomemory:85000000-85ffffff ioport:8000-80ff iomemory:84300000-84300fff
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:86100000-86100fff irq:10
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ALI15x3_IDE
             resources: ioport:7000-700f irq:14
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: WDC WD200EB-11CSF0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 04.01B04
                   serial: WD-WMAAV1415836
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 4769MB
                      capabilities: primary
                 *-volume:1
                      description: Linux swap / Solaris partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 478MB
                      capabilities: primary nofs
                 *-volume:2
                      description: W95 FAT32 partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 13GB
                      capabilities: primary
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 90840D5
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: PAS23B15
                   serial: V50D68TA
                   size: 8047MB
                   capacity: 8047MB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: smart=on
                 *-volume
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 8040MB
                      capabilities: primary bootable
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-tape
                   product: SuperStation-Int
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 1023GB
              *-cdrom
                   description: IDE CD-ROM
                   product: CRD-8480C
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.04
                   serial: 1999/08/12
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
```


```
lspci
00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] (rev b5)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/
```


There is also this unix info file that came with the card (on a driver cd), which I figure I'll give as it might be some help


```
************************************************
*  Driver Installation SCO UNIX Open System 5  *
************************************************

The E2000 adapters are fully NE2000 compatible. Use the NE2000
driver bundled with Open System 5.

METHOD 1 --
 1. From the 'SINGLE USER MODE', enter the root password in order to
    have 'System Maintenance Mode'.

 2. Enter 'netconfig' after '#'.

 3. The 'Network Configuration Manager' window will appear, choose 'Hardware'
    and select 'Add new LAN adapter'.

 4. When the 'Add new LAN adapter' window appears, select 'NOVELL NE2000' and
    [ENTER] to continue.

 5. The 'Search for network adapter' box will be displayed. Choose 'no'.

 6. After the "Network Driver Configuration" window appears, enter the I/O
    address and the interrupt vector and press 'ok'.

 7. In the "Add protocol" window, there are two items: "SCO IPX/SPX" or
    "SCO TCP/IP". Choose "SCO TCP/IP".

 8. After the "SCO TCP/IP configuration" window appears, enter the proper
    values for "Local Host name", "IP address", "Netmask", and so on.

 9. When the message box shows "the following products were successfully
    configured into the system", installation is done. Exit the "Network
    Driver Configuration" window.

10. After the 'Question' box appears, push the OK button to re-link the Kernel.

11. Enter 'haltsys' to reboot the UNIX system.


METHOD 2 --
1. From the 'X window' mode, click 'System Adaministration' icon.

2. In the 'System Adaministration' window, choose 'Networks'.

3. A window will appear, choose 'Network Configuration Manager'.

4. After the 'Network Configuration Manager' window appears, the installation
   procedure is the same as Method 1, beginning at Step 3.
```

---

### Post by noob12 on 2007-09-25
If it sits off this bridge, then that would explain things.   No driver has claimed this bridge.
```

        *-isa UNCLAIMED
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master

```

---

### Post by lo_mein_dreams on 2007-09-25
I'm presuming it does, the modem I have also doesn't seem to work in either of my ISA slots. Anyone know where to acquire this driver?

---

### Post by noob12 on 2007-09-25
Can you run **lspci -nn**  (and post it) so we see the device ids for the bridge.  The plain lspci output doesn't show this.

---

### Post by lo_mein_dreams on 2007-09-25
Here. Hope it helps.

```
lspci -nn
00:00.0 0600: 10b9:1541 (rev 04)
00:01.0 0604: 10b9:5243 (rev 04)
00:02.0 0c03: 10b9:5237 (rev 03)
00:07.0 0601: 10b9:1533 (rev b5)
00:0f.0 0101: 10b9:5229 (rev 20)
01:00.0 0300: 1002:4742 (rev 5c)

```

---

### Post by noob12 on 2007-09-26
Sorry not much.  This id 10b9:1533 is the 1533 bridge.  The only association I could find in the 2.6.20-16 is the alim7101_wdt module, which only runs the watchdog timer.   Did this module have trouble loading by any chance?  (Check your dmesg).   I suspect you need more to really operate the bridge, but I don't know much about this type of thing.

---

### Post by lo_mein_dreams on 2007-09-26
```
dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fffa000 (usable)
[17179569.184000]  BIOS-e820: 000000000fffa000 - 000000000fffe000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000fffe000 - 0000000010000000 (ACPI NVS)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65530
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61434 pages, LIFO batch:15
[17179569.184000] DMI 2.0 present.
[17179569.184000] ACPI: RSDP (v000 IBM                                   ) @ 0x000fe030
[17179569.184000] ACPI: RSDT (v001 IBM    V70XA    0x00000001 IBM  0x00000000) @ 0x0fffa000
[17179569.184000] ACPI: FADT (v001 IBM    V70XA    0x00000001 IBM  0x00000000) @ 0x0fffa028
[17179569.184000] ACPI: DSDT (v001   IBM    V70XA  0x00001000 MSFT 0x0100000a) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1998) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:f0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (0120a000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 448.972 MHz processor.
[   31.648790] Using tsc for high-res timesource
[   31.650469] Console: colour VGA+ 80x25
[   31.652019] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.653321] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   31.701012] Memory: 250344k/262120k available (1910k kernel code, 11288k reserved, 1070k data, 308k init, 0k highmem)
[   31.701031] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.780545] Calibrating delay using timer specific routine.. 899.53 BogoMIPS (lpj=1799064)
[   31.780827] Security Framework v1.0.0 initialized
[   31.780856] SELinux:  Disabled at boot.
[   31.780957] Mount-cache hash table entries: 512
[   31.781935] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[   31.781982] CPU: After vendor identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[   31.782027] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
[   31.782041] CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000 00000000
[   31.782145] Checking 'hlt' instruction... OK.
[   31.796644] SMP alternatives: switching to UP code
[   31.797841] Freeing SMP alternatives: 16k freed
[   31.798534] checking if image is initramfs... it is
[   34.385810] Freeing initrd memory: 5254k freed
[   34.385844] CPU0: AMD-K6(tm) 3D processor stepping 0c
[   34.385874] SMP motherboard not detected.
[   34.385888] Local APIC not detected. Using dummy APIC emulation.
[   34.386283] Brought up 1 CPUs
[   34.386418] migration_cost=0
[   34.388412] NET: Registered protocol family 16
[   34.388675] EISA bus registered
[   34.404176] PCI: PCI BIOS revision 2.10 entry at 0xf0200, last bus=1
[   34.404204] PCI: Using configuration type 1
[   34.404214] Setting up standard PCI resources
[   34.409748] ACPI: Interpreter disabled.
[   34.409769] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.409830] pnp: PnP ACPI: disabled
[   34.409845] PnPBIOS: Scanning system for PnP BIOS support...
[   34.410073] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5b10
[   34.410095] PnPBIOS: PnP BIOS version 1.0, entry 0xf9e00:0x0, dseg 0xf0000
[   34.416243] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   34.416644] PCI: Probing PCI hardware
[   34.416661] PCI: Probing PCI hardware (bus 00)
[   34.417483] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[   34.417913] Boot video device is 0000:01:00.0
[   34.420599] PCI: Using ALI IRQ Router
[   34.420617] PCI: Using IRQ router ALI [10b9/1533] at 0000:00:07.0
[   34.429949] pnp: 00:08: ioport range 0xf000-0xf03f has been reserved
[   34.429967] pnp: 00:08: ioport range 0xf040-0xf05f has been reserved
[   34.432232] PCI: Bridge: 0000:00:01.0
[   34.432248]   IO window: 8000-8fff
[   34.432264]   MEM window: 80300000-843fffff
[   34.432278]   PREFETCH window: 84400000-860fffff
[   34.432432] NET: Registered protocol family 2
[   34.468189] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   34.468975] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   34.469602] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   34.469962] TCP: Hash tables configured (established 8192 bind 4096)
[   34.469979] TCP reno registered
[   34.476023] audit: initializing netlink socket (disabled)
[   34.476083] audit(1190730708.016:1): initialized
[   34.477177] VFS: Disk quotas dquot_6.5.1
[   34.477298] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.477660] Initializing Cryptographic API
[   34.477686] io scheduler noop registered
[   34.477739] io scheduler anticipatory registered
[   34.477780] io scheduler deadline registered
[   34.477892] io scheduler cfq registered (default)
[   34.477926] Activating ISA DMA hang workarounds.
[   34.479297] isapnp: Scanning for PnP cards...
[   34.633529] isapnp: Card 'Onboard PnP Audio'
[   34.633544] isapnp: Card 'PnP ISA Ethernet Adapter'
[   34.633557] isapnp: 2 Plug & Play cards detected total
[   34.962010] Real Time Clock Driver v1.12ac
[   34.962557] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.964130] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   34.968371] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   34.970240] mice: PS/2 mouse device common for all mice
[   34.976044] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.976921] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.976947] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.978038] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   34.981261] serio: i8042 AUX port at 0x60,0x64 irq 12
[   34.981419] serio: i8042 KBD port at 0x60,0x64 irq 1
[   34.982930] EISA: Probing bus 0 at eisa.0
[   34.983022] Cannot allocate resource for EISA slot 7
[   34.983034] Cannot allocate resource for EISA slot 8
[   34.983044] EISA: Detected 0 cards.
[   34.983543] TCP bic registered
[   34.983637] NET: Registered protocol family 1
[   34.983673] NET: Registered protocol family 8
[   34.983683] NET: Registered protocol family 20
[   34.983810] Using IPI No-Shortcut mode
[   34.986610] Freeing unused kernel memory: 308k freed
[   35.016150] input: AT Translated Set 2 keyboard as /class/input/input0
[   36.622769] Capability LSM initialized
[   40.563590] ALI15X3: IDE controller at PCI slot 0000:00:0f.0
[   40.563653] ALI15X3: chipset revision 32
[   40.563665] ALI15X3: not 100% native mode: will probe irqs later
[   40.563721]     ide0: BM-DMA at 0x7000-0x7007, BIOS settings: hda:DMA, hdb:DMA
[   40.563786]     ide1: BM-DMA at 0x7008-0x700f, BIOS settings: hdc:DMA, hdd:DMA
[   40.563835] Probing IDE interface ide0...
[   40.849576] hda: WDC WD200EB-11CSF0, ATA DISK drive
[   41.129474] hdb: Maxtor 90840D5, ATA DISK drive
[   41.186550] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   41.188749] Probing IDE interface ide1...
[   41.925325] hdc: SuperStation-Int, ATAPI TAPE drive
[   42.708936] hdd: CRD-8480C, ATAPI CD/DVD-ROM drive
[   42.765012] ide1 at 0x170-0x177,0x376 on irq 15
[   42.829821] hda: max request size: 128KiB
[   42.881018] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, (U)DMA
[   42.881053] hda: cache flushes not supported
[   42.881261]  hda: hda1 hda2 hda3
[   42.909138] hdb: max request size: 128KiB
[   42.910229] hdb: 16481808 sectors (8438 MB) w/256KiB Cache, CHS=16351/16/63, (U)DMA
[   42.910258] hdb: cache flushes not supported
[   42.910442]  hdb: hdb1
[   43.199140] hdd: ATAPI 48X CD-ROM drive, 128kB Cache
[   43.199178] Uniform CD-ROM driver Revision: 3.20
[   44.646801] usbcore: registered new driver usbfs
[   44.649650] usbcore: registered new driver hub
[   44.660408] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   44.663197] PCI: Found IRQ 10 for device 0000:00:02.0
[   44.663299] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   44.665427] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   44.665496] ohci_hcd 0000:00:02.0: irq 10, io mem 0x86100000
[   44.723586] usb usb1: configuration #1 chosen from 1 choice
[   44.724849] hub 1-0:1.0: USB hub found
[   44.724954] hub 1-0:1.0: 2 ports detected
[   45.033077] Attempting manual resume
[   45.127620] kjournald starting.  Commit interval 5 seconds
[   45.127710] EXT3-fs: mounted filesystem with ordered data mode.
[   68.297198] ide-tape: hdc <-> ht0: SONY SuperStation-Int rev 1.06
[   68.318718] ide-tape: hdc: overriding capabilities->speed (assuming 650KB/sec)
[   68.318739] ide-tape: hdc: overriding capabilities->max_speed (assuming 650KB/sec)
[   68.319440] Linux agpgart interface v0.101 (c) Dave Jones
[   68.325417] ide-tape: hdc <-> ht0: 650KBps, 14*32kB buffer, 6336kB pipeline, 100ms tDSC
[   68.326828] agpgart: Detected ALi M1541 chipset
[   68.336461] agpgart: AGP aperture is 128M @ 0xe0000000
[   70.019436] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   70.032309] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   73.866563] parport: PnPBIOS parport detected.
[   73.866689] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   73.905937] Floppy drive(s): fd0 is 1.44M
[   73.924209] FDC 0 is a post-1991 82077
[   73.994734] logips2pp: Detected unknown logitech mouse model 0
[   74.420396] input: ImPS/2 Logitech Wheel Mouse as /class/input/input1
[   75.385486] input: PC Speaker as /class/input/input2
[   75.993996] pnp: Device 01:01.01 activated.
[   76.013164] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 426kHz
[   77.266749] pnp: Device 01:01.00 activated.
[   77.269541] pnp: Device 01:01.00 disabled.
[   77.269561] cs4232-pnpbios: probe of 01:01.00 failed with error -2
[   77.269721] CS4232 soundcard not found or device busy
[   77.970797] ts: Compaq touchscreen protocol output
[   79.684315] lp0: using parport0 (interrupt-driven).
[   79.903260] Adding 489972k swap on /dev/disk/by-uuid/7b86fe69-8ec1-470d-83af-9d033735a8d2.  Priority:-1 extents:1 across:489972k
[   80.256114] EXT3 FS on hda1, internal journal
[  118.285263] IBM machine detected. Enabling interrupts during APM calls.
[  118.285297] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  141.023205] NET: Registered protocol family 10
[  141.023875] lo: Disabled Privacy Extensions
[  141.024369] IPv6 over IPv4 tunneling driver
[  151.286514] Bluetooth: Core ver 2.8
[  151.286544] NET: Registered protocol family 31
[  151.286555] Bluetooth: HCI device and connection manager initialized
[  151.286640] Bluetooth: HCI socket layer initialized
[  151.460619] Bluetooth: L2CAP ver 2.8
[  151.460644] Bluetooth: L2CAP socket layer initialized
[  152.925107] Bluetooth: RFCOMM socket layer initialized
[  152.925198] Bluetooth: RFCOMM TTY layer initialized
[  152.925210] Bluetooth: RFCOMM ver 1.7
[  165.171185] ISO 9660 Extensions: Microsoft Joliet Level 3
[  165.244162] ISO 9660 Extensions: RRIP_1991A
[15380.471926] attempt to access beyond end of device
[15380.471965] fd0: rw=0, want=1444, limit=1440
[15380.475084] UDF-fs: No VRS found
[15427.236021] attempt to access beyond end of device
[15427.236060] fd0: rw=0, want=1444, limit=1440
[15427.238934] UDF-fs: No VRS found
[15437.427766] Unable to identify CD-ROM format.
[15447.420626] Unable to identify CD-ROM format.
[15447.445211] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```
Hmm... I feel illiterate, but it does seem to see my ethernet card. It also says the sound is ISA, which now that I look does not seem to be working as well. Not sure what to make of anything else.

---

### Post by noob12 on 2007-09-26
That's encouraging.   Do you know what kind of ethernet card it is?   I think that you are probably going to have to load the driver explicitly along with options telling it the IRQ and I/O base port.

---

### Post by lo_mein_dreams on 2007-09-28
Type? I'm don't completely understand. I don't know the official manufacturer, it just lists "NE2000 compatible".

---

### Post by noob12 on 2007-09-28
OK.  That's probably useful.  That means you should use the **ne** driver (type **modinfo ne** for details), but you still need to figure out the i/o base address and irq, which hopefully you can find out from your BIOS.

---

### Post by lo_mein_dreams on 2007-09-28
Well for this I think I am in luck. The card came with a little booklet with "Specifications"

_I/O Addresses:_ 200, 220, 240, 260, 280, 2A0, 2C0, 2E0, 300 (Default), 320, 340, 360, 380, 3A0, 3C0, 3E0

_IRQs:_ 2/9, 3 (Default), 4, 5, 10, 11, 12, 15

I went to my bios and looked for anything mentioning its Base Address and IRQ. I found information on my serial port and parallel port, but nothing showed up for isa (or anything else).

_Serial:_ 
Base Address: 2F8h
IRQ: 3

_Parallel:_
Base Address: 378h
IRQ: 7

Is there any other way for me to find the exact info for the device?

---

### Post by noob12 on 2007-09-28
[COLOR="Red"]UPDATE:  Based on feedback from survient on this thread [http://ubuntuforums.org/showthread.php?t=567637](http://ubuntuforums.org/showthread.php?t=567637), this procedure doesn't work, so the docs seem to be out of date.  Maybe some variant of it will.[/COLOR]


I don't know.  Here is a blind wild swing.  (Any chance you can get PCI-based card into this box?  Is this all worth it?)

I am basing this on the file pnp.txt (pnp.txt.gz) in the 2.6.20 docs.  It is the same in 2.6.17, so I'm hoping this will be accurate.
 
See if these files exist
```

ls /sys/bus/pnp/devices/*/name

```

If the exist, then look for the ethernet card in there
```

grep -n -i ethernet /sys/bus/pnp/devices/*/name

```


[COLOR="Red"]_You MUST replace the example 00:0f in everything below this point with whatever you actually find on your system.  The 00:0f is just an example. _[/COLOR]

If the above produces output like the following 
```

/sys/bus/pnp/devices/00:0f/name:PnP ISA Ethernet Adapter

```
then you can proceed

Type 
```
cat /sys/bus/pnp/devices/00:0f/resources
```
If that shows you a base address and irq, you have it.

If instead you see **DISABLED** then try the following
```

echo "auto" > /driver/bus/pnp/devices/00:0f/resources

cat /sys/bus/pnp/devices/00:0f/resources

```
which should show you the io port and irq.

Let's see if that works.  If it does, you should be able to use those values to load the **ne** module.

EDIT: Note -- I'm no longer watching this thread.  If you need me, you may need to send a PM. Good luck.

---

### Post by noob12 on 2007-10-14
OK.  Supposedly once you have the io base address and irq you can load the ne driver with the appropriate options.

I just scanned the source code and it does look like it will try to figure things out even without the user-supplied options even though modinfo says they're required parameters.

So I would first try this
```

sudo modprobe ne

# then take a look at the tail of /var/log/kern.log to see if it says anything interesting
tail -15 /var/log/kern.log

```

If it doesn't seem to have found the card, try specifing the values explicitly.

This will do it from the command line once
```

sudo modprobe irq=*nn* io=*XXXX*

```
where *nn* is the irq number and *XXXX* is the base address.  I think it will take hex values for the base address if you include the 0x prefix, like 0x280 or whatever.

See if that works.  If it does you should get a device showing up in your **ifconfig -a** output.  Once you determine what works, I can suggest instructions to set it up to happen automatically at boot time.

---

### Post by lo_mein_dreams on 2007-10-16
sudo modprobe ne worked, I didn't even need any of the information I've gathered. I'm surprised this didn't happen by default at some point, but I'm glad it works now.

I haven't restarted yet, but if I did, would I have to type the command each time?

---

### Post by az on 2007-10-16
> **lo_mein_dreams said:**
> sudo modprobe ne worked, I didn't even need any of the information I've gathered. I'm surprised this didn't happen by default at some point, but I'm glad it works now.

I haven't restarted yet, but if I did, would I have to type the command each time?

Edit /etc/modules
and add the word 

ne

on a line by itself.  That way it will get loaded each time you boot.

I would suggest you file a bug report, but probing the isa bus is sometime problematic and simply can't be done.   If you are inclined to file a bug report, file it with the udev package.

---

### Post by noob12 on 2007-10-16
lo_mein_dreams:

Yeah, az's instructions will work for you so that it loads automatically at boot:

I'm sorry I led you on the wild goose chase to get the irq and base addr but I was basing that on the fact that the modinfo said these params were required when loading the module.  Examining the source code showed they aren't.  If I had known that from the start I would have just suggested the **modprobe ne** initially and we'd have cut to the result pretty quickly.

Cheers.

---

### Post by lo_mein_dreams on 2007-10-16
noob12: Don't worry about it :). I learned things, and that was good.

az: thank you much.

---

