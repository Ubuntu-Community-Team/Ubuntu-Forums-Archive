---
title: "ra2500 on Gutsy AMD64 half working..."
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by NEUR0M4NCER on 2008-03-02
Just got my new PC, and installed my old PCI WiFi card (Belkin F5D7000). Put Gutsy AMD64 on, worked fine, connected to my (unsecured) wireless network. Then got Sky Wireless Broadband, which uses WPA-PSK.

The Wireless card (through Network Manager) sees the Sky wireless network, and its strength, asks for a password when I try to connect, then 1 minute later, asks again. And again. Fortunately, i've still got my old network running (good thing I didn't cancel Virgin Broadband yet), so i've still got access, but I really need to get going on the Sky network, and can't see a reason why it's not working. I've seen the tutorials on here, but if my card's working already, do I still need to re-install the ralink drivers/use NdisWrapper?

Also... does Network Manager automatically select the correct channel for the router, as the Sky setup stuff specifies channel 11, but there's no way of selecting it in NM.

AND! Most of the how-tos here require switching to a wired connection at some point - my routers are both in another room, and my PC setup... well let's just say it's very wirey, and it wouldn't like being moved to another room...

Hope someone can help!


**edit**
And    $ lshw -C network    returns the logical name of my interface as wmaster0 - that's not right... is it?

---

### Post by NEUR0M4NCER on 2008-03-02
Here's the output of dmesg (or as much as terminal would let me copy) - the part towards the end seems to be relevent to this problem...

```
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ed00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515818
[    0.000000] Kernel command line: root=UUID=ff937675-748e-40e7-af5a-5788448e09f3 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   23.262276] time.c: Detected 2194.806 MHz processor.
[   23.263540] Console: colour VGA+ 80x25
[   23.263555] Checking aperture...
[   23.263564] Calgary: detecting Calgary via BIOS EBDA area
[   23.263566] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   23.285647] Memory: 2055792k/2096832k available (2274k kernel code, 40652k reserved, 1185k data, 296k init)
[   23.285690] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   23.364158] Calibrating delay using timer specific routine.. 4392.97 BogoMIPS (lpj=8785959)
[   23.364187] Security Framework v1.0.0 initialized
[   23.364195] SELinux:  Disabled at boot.
[   23.364375] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.365678] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.366293] Mount-cache hash table entries: 256
[   23.366423] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.366426] CPU: L2 cache: 2048K
[   23.366429] CPU 0/0 -> Node 0
[   23.366431] using mwait in idle threads.
[   23.366432] CPU: Physical Processor ID: 0
[   23.366434] CPU: Processor Core ID: 0
[   23.366440] CPU0: Thermal monitoring enabled (TM2)
[   23.366451] SMP alternatives: switching to UP code
[   23.366697] Early unpacking initramfs... done
[   23.668379] ACPI: Core revision 20070126
[   23.668417] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.721832] Using local APIC timer interrupts.
[   23.767342] result 12470490
[   23.767344] Detected 12.470 MHz APIC timer.
[   23.767740] SMP alternatives: switching to SMP code
[   23.767823] Booting processor 1/2 APIC 0x1
[   23.778054] Initializing CPU#1
[   23.855582] Calibrating delay using timer specific routine.. 4389.66 BogoMIPS (lpj=8779336)
[   23.855588] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.855590] CPU: L2 cache: 2048K
[   23.855592] CPU 1/1 -> Node 0
[   23.855593] CPU: Physical Processor ID: 0
[   23.855595] CPU: Processor Core ID: 1
[   23.855600] CPU1: Thermal monitoring enabled (TM2)
[   23.855875] Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   23.855949] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.879578] Brought up 2 CPUs
[   23.941325] migration_cost=18
[   23.941487] NET: Registered protocol family 16
[   23.941559] ACPI: bus type pci registered
[   23.941565] PCI: Using configuration type 1
[   23.943875] ACPI: EC: Look up EC in DSDT
[   23.947309] ACPI: Interpreter enabled
[   23.947312] ACPI: (supports S0 S1 S3 S4 S5)
[   23.947328] ACPI: Using IOAPIC for interrupt routing
[   23.947480] Error attaching device data
[   23.947512] Error attaching device data
[   23.947542] Error attaching device data
[   23.947577] Error attaching device data
[   23.953330] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.953343] PCI: Probing PCI hardware (bus 00)
[   23.953801] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   23.953804] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   23.954262] PCI: Transparent bridge - 0000:00:1e.0
[   23.954312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.954426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   23.954494] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   23.954585] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   23.954652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   23.956549] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   23.956641] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   23.956731] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   23.956821] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   23.956914] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.957005] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.957095] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.957186] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   23.957267] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.957276] pnp: PnP ACPI init
[   23.957282] ACPI: bus type pnp registered
[   23.960606] pnp: PnP ACPI: found 17 devices
[   23.960608] ACPI: ACPI bus type pnp unregistered
[   23.960651] PCI: Using ACPI for IRQ routing
[   23.960653] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.960721] NET: Registered protocol family 8
[   23.960723] NET: Registered protocol family 20
[   23.960734] PCI-GART: No AMD northbridge found.
[   23.960778] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   23.960784] pnp: 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   23.960787] pnp: 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
[   23.960792] pnp: 00:09: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   23.960795] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   23.960798] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   23.960803] pnp: 00:0e: ioport range 0x290-0x29f has been reserved
[   23.960808] pnp: 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[   23.960814] pnp: 00:10: iomem range 0x0-0x9ffff could not be reserved
[   23.960816] pnp: 00:10: iomem range 0xc0000-0xcffff has been reserved
[   23.960818] pnp: 00:10: iomem range 0xe0000-0xfffff could not be reserved
[   23.960821] pnp: 00:10: iomem range 0x100000-0x7fffffff could not be reserved
[   23.961059] PCI: Bridge: 0000:00:01.0
[   23.961061]   IO window: e000-efff
[   23.961065]   MEM window: fa000000-feafffff
[   23.961067]   PREFETCH window: d0000000-dfffffff
[   23.961070] PCI: Bridge: 0000:00:1c.0
[   23.961072]   IO window: disabled.
[   23.961075]   MEM window: disabled.
[   23.961079]   PREFETCH window: cff00000-cfffffff
[   23.961083] PCI: Bridge: 0000:00:1c.1
[   23.961084]   IO window: disabled.
[   23.961087]   MEM window: disabled.
[   23.961091]   PREFETCH window: cfe00000-cfefffff
[   23.961095] PCI: Bridge: 0000:00:1e.0
[   23.961096]   IO window: disabled.
[   23.961100]   MEM window: feb00000-febfffff
[   23.961103]   PREFETCH window: disabled.
[   23.961116] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.961120] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.961134] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.961139] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.961153] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.961157] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   23.961166] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.961175] NET: Registered protocol family 2
[   23.963458] Time: tsc clocksource has been installed.
[   23.999592] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   24.000214] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   24.004584] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   24.005264] TCP: Hash tables configured (established 262144 bind 65536)
[   24.005266] TCP reno registered
[   24.015684] checking if image is initramfs... it is
[   24.611959] Freeing initrd memory: 7204k freed
[   24.615624] audit: initializing netlink socket (disabled)
[   24.615643] audit(1204442055.292:1): initialized
[   24.617291] VFS: Disk quotas dquot_6.5.1
[   24.617332] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.617408] io scheduler noop registered
[   24.617409] io scheduler anticipatory registered
[   24.617411] io scheduler deadline registered
[   24.617485] io scheduler cfq registered (default)
[   24.618523] Boot video device is 0000:03:00.0
[   24.618631] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.618660] assign_interrupt_mode Found MSI capability
[   24.618663] Allocate Port Service[0000:00:01.0:pcie00]
[   24.618730] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.618765] assign_interrupt_mode Found MSI capability
[   24.618767] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.618794] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.618860] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.618895] assign_interrupt_mode Found MSI capability
[   24.618896] Allocate Port Service[0000:00:1c.1:pcie00]
[   24.618918] Allocate Port Service[0000:00:1c.1:pcie02]
[   24.635415] Real Time Clock Driver v1.12ac
[   24.635496] Linux agpgart interface v0.102 (c) Dave Jones
[   24.635498] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.635589] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.636119] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.636619] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.636727] input: Macintosh mouse button emulation as /class/input/input0
[   24.636788] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   24.639295] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.639299] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.639425] mice: PS/2 mouse device common for all mice
[   24.639623] TCP cubic registered
[   24.639674] NET: Registered protocol family 1
[   24.639829] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.639835] Freeing unused kernel memory: 296k freed
[   24.667002] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.770854] AppArmor: AppArmor initialized<5>audit(1204442056.448:2):  type=1505 info="AppArmor initialized" pid=1227
[   25.782750] fuse init (API version 7.8)
[   25.793394] Failure registering capabilities with primary security module.
[   25.815948] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  0E, should be 09 [20070126]
[   25.815955] ACPI: SSDT 7FFC0090, 0235 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[   25.816325] ACPI: SSDT 7FFC0520, 0235 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[   25.816485] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.816494] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   26.158333] usbcore: registered new interface driver usbfs
[   26.158355] usbcore: registered new interface driver hub
[   26.158374] usbcore: registered new device driver usb
[   26.158897] USB Universal Host Controller Interface driver v3.0
[   26.158985] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   26.158995] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.158998] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.159120] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.159144] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d480
[   26.159232] usb usb1: configuration #1 chosen from 1 choice
[   26.159252] hub 1-0:1.0: USB hub found
[   26.159257] hub 1-0:1.0: 2 ports detected
[   26.204061] SCSI subsystem initialized
[   26.254242] libata version 2.21 loaded.
[   26.261865] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   26.262291] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   26.262297] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   26.262351] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   26.262383] ehci_hcd 0000:00:1d.7: debug port 1
[   26.262388] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   26.262395] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9ffbc00
[   26.266288] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.266361] usb usb2: configuration #1 chosen from 1 choice
[   26.266380] hub 2-0:1.0: USB hub found
[   26.266386] hub 2-0:1.0: 8 ports detected
[   26.370214] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   26.370225] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.370228] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.370607] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   26.370632] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[   26.370715] usb usb3: configuration #1 chosen from 1 choice
[   26.370736] hub 3-0:1.0: USB hub found
[   26.370741] hub 3-0:1.0: 2 ports detected
[   26.474395] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.474405] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.474408] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.474427] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   26.474451] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d880
[   26.474527] usb usb4: configuration #1 chosen from 1 choice
[   26.474546] hub 4-0:1.0: USB hub found
[   26.474550] hub 4-0:1.0: 2 ports detected
[   26.578775] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   26.578786] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   26.578790] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   26.578814] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   26.578836] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000dc00
[   26.578906] usb usb5: configuration #1 chosen from 1 choice
[   26.578925] hub 5-0:1.0: USB hub found
[   26.578928] hub 5-0:1.0: 2 ports detected
[   26.686319] ata_piix 0000:00:1f.1: version 2.11
[   26.686335] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   26.686365] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   26.686472] scsi0 : ata_piix
[   26.686506] scsi1 : ata_piix
[   26.686594] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001ffa0 irq 14
[   26.686597] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001ffa8 irq 15
[   27.024221] ata1.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P58, max UDMA/66
[   27.024227] ata1.00: limited to UDMA/33 due to 40-wire cable
[   27.212791] ata1.00: configured for UDMA/33
[   27.212816] ata2: port disabled. ignoring.
[   27.240923] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P58 PQ: 0 ANSI: 5
[   27.241009] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   27.241039] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   27.241075] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   27.241137] scsi2 : ata_piix
[   27.241171] scsi3 : ata_piix
[   27.241189] ata3: SATA max UDMA/133 cmd 0x000000000001d400 ctl 0x000000000001d082 bmdma 0x000000000001c880 irq 19
[   27.241192] ata4: SATA max UDMA/133 cmd 0x000000000001d000 ctl 0x000000000001cc02 bmdma 0x000000000001c888 irq 19
[   27.405710] ata3.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[   27.405716] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   27.421764] ata3.00: configured for UDMA/133
[   27.588791] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   27.701024] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   27.701030] Uniform CD-ROM driver Revision: 3.20
[   27.701094] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   27.701241] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   27.701250] sd 2:0:0:0: [sda] Write Protect is off
[   27.701252] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.701263] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.701298] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   27.701305] sd 2:0:0:0: [sda] Write Protect is off
[   27.701307] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.701318] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.701321]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   27.703685] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   27.719789]  sda1 sda2 < sda5 >
[   27.738810] sd 2:0:0:0: [sda] Attached SCSI disk
[   27.945616] Attempting manual resume
[   27.945619] swsusp: Resume From Partition 8:5
[   27.945620] PM: Checking swsusp image.
[   27.945766] PM: Resume from disk failed.
[   27.976554] kjournald starting.  Commit interval 5 seconds
[   27.976565] EXT3-fs: mounted filesystem with ordered data mode.
[   34.497987] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.558859] intel_rng: FWH not detected
[   34.611218] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.665581] parport_pc 00:06: reported by Plug and Play ACPI
[   34.665637] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   34.745710] iTCO_vendor_support: vendor-support=0
[   34.746610] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   34.746675] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   34.746708] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.806884] input: PC Speaker as /class/input/input2
[   34.977946] nvidia: module license 'NVIDIA' taints kernel.
[   35.234611] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.234621] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   35.234720] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   35.252273] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 23 (level, low) -> IRQ 23
[   35.329497] ieee80211_init: failed to initialize WME (err=-17)
[   35.351166] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   35.351192] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   35.351213] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   35.351247] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   35.351494] wmaster0: Selected rate control algorithm 'simple'
[   35.444359] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.444820] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.466803] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   35.651716] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   35.902537] loop: module loaded
[   35.914469] lp0: using parport0 (interrupt-driven).
[   36.001357] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k
[   36.326005] EXT3 FS on sda1, internal journal
[   37.106946] No dock devices found.
[   37.251593] input: Power Button (FF) as /class/input/input4
[   37.251609] ACPI: Power Button (FF) [PWRF]
[   37.251696] input: Power Button (CM) as /class/input/input5
[   37.251706] ACPI: Power Button (CM) [PWRB]
[   37.860082] ppdev: user-space parallel port driver
[   38.096907] audit(1204442069.279:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4820 profile="/usr/sbin/cupsd"
[   38.466500] Failure registering capabilities with primary security module.
[   48.062555] NET: Registered protocol family 17
[   57.013537] wlan0: Initial auth_alg=0
[   57.013542] wlan0: authenticate with AP 00:14:78:b5:fd:1c
[   57.014895] wlan0: RX authentication from 00:14:78:b5:fd:1c (alg=0 transaction=2 status=0)
[   57.014899] wlan0: authenticated
[   57.014901] wlan0: associate with AP 00:14:78:b5:fd:1c
[   57.017034] wlan0: RX AssocResp from 00:14:78:b5:fd:1c (capab=0x421 status=0 aid=1)
[   57.017037] wlan0: associated
[   64.604126] NET: Registered protocol family 10
[   64.604264] lo: Disabled Privacy Extensions
[   65.617840] wlan0: duplicate address detected!
[   78.328623] wlan0: deauthenticate(reason=3)
[   97.675703] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   99.788956] wlan0: Initial auth_alg=0
[   99.788962] wlan0: authenticate with AP 00:1b:2f:7d:c4:b4
[   99.790158] wlan0: RX authentication from 00:1b:2f:7d:c4:b4 (alg=0 transaction=2 status=0)
[   99.790163] wlan0: authenticated
[   99.790166] wlan0: associate with AP 00:1b:2f:7d:c4:b4
[   99.791944] wlan0: authentication frame received from 00:1b:2f:7d:c4:b4, but not in authenticate state - ignored
[   99.792886] wlan0: authentication frame received from 00:1b:2f:7d:c4:b4, but not in authenticate state - ignored
[   99.793449] wlan0: RX AssocResp from 00:1b:2f:7d:c4:b4 (capab=0x471 status=0 aid=1)
[   99.793453] wlan0: associated
[   99.793523] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   99.793526] wlan0: failed to set TX queue parameters for queue 2
[   99.793531] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   99.793534] wlan0: failed to set TX queue parameters for queue 3
[   99.793538] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   99.793542] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   99.796816] wlan0: association frame received from 00:1b:2f:7d:c4:b4, but not in associate state - ignored
[   99.797783] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.786983] wlan0: RX deauthentication from 00:1b:2f:7d:c4:b4 (reason=1)
[  103.786989] wlan0: deauthenticated
[  104.786754] wlan0: authenticate with AP 00:1b:2f:7d:c4:b4
[  104.787963] wlan0: RX authentication from 00:1b:2f:7d:c4:b4 (alg=0 transaction=2 status=0)
[  104.787970] wlan0: authenticated
[  104.787974] wlan0: associate with AP 00:1b:2f:7d:c4:b4
[  104.791303] wlan0: RX ReassocResp from 00:1b:2f:7d:c4:b4 (capab=0x471 status=0 aid=1)
[  104.791307] wlan0: associated
[  108.781279] wlan0: RX deauthentication from 00:1b:2f:7d:c4:b4 (reason=1)
[  108.781285] wlan0: deauthenticated
[  109.780698] wlan0: authenticate with AP 00:1b:2f:7d:c4:b4
[  109.781898] wlan0: RX authentication from 00:1b:2f:7d:c4:b4 (alg=0 transaction=2 status=0)
[  109.781903] wlan0: authenticated
[  109.781907] wlan0: associate with AP 00:1b:2f:7d:c4:b4
[  109.785466] wlan0: RX ReassocResp from 00:1b:2f:7d:c4:b4 (capab=0x471 status=0 aid=1)
[  109.785470] wlan0: associated
[  110.443889] wlan0: no IPv6 routers present
[  113.775397] wlan0: RX deauthentication from 00:1b:2f:7d:c4:b4 (reason=1)
[  113.775403] wlan0: deauthenticated
[  114.774644] wlan0: authenticate with AP 00:1b:2f:7d:c4:b4
[  114.776729] wlan0: RX authentication from 00:1b:2f:7d:c4:b4 (alg=0 transaction=2 status=0)
[  114.776735] wlan0: authenticated
[  114.776739] wlan0: associate with AP 00:1b:2f:7d:c4:b4
[  114.780066] wlan0: RX ReassocResp from 00:1b:2f:7d:c4:b4 (capab=0x471 status=0 aid=1)
[  114.780070] wlan0: associated
[  118.769636] wlan0: RX deauthentication from 00:1b:2f:7d:c4:b4 (reason=1)
[  118.769642] wlan0: deauthenticated
[  119.768589] wlan0: authenticate with AP 00:1b:2f:7d:c4:b4
[  119.769792] wlan0: RX authentication from 00:1b:2f:7d:c4:b4 (alg=0 transaction=2 status=0)
[  119.769798] wlan0: authenticated
[  119.769802] wlan0: associate with AP 00:1b:2f:7d:c4:b4
[  119.773164] wlan0: RX ReassocResp from 00:1b:2f:7d:c4:b4 (capab=0x471 status=0 aid=1)
[  119.773167] wlan0: associated
[  123.763847] wlan0: RX deauthentication from 00:1b:2f:7d:c4:b4 (reason=1)
[  123.763853] wlan0: deauthenticated
[  124.763216] wlan0: authenticate with AP 00:1b:2f:7d:c4:b4
[  124.764442] wlan0: RX authentication from 00:1b:2f:7d:c4:b4 (alg=0 transaction=2 status=0)
[  124.764448] wlan0: authenticated
[  124.764451] wlan0: associate with AP 00:1b:2f:7d:c4:b4
[  124.767851] wlan0: RX ReassocResp from 00:1b:2f:7d:c4:b4 (capab=0x471 status=0 aid=1)
[  124.767855] wlan0: associated
[  128.692393] wlan0: deauthenticate(reason=3)
[  129.957320] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  130.853134] wlan0: Initial auth_alg=0
[  130.853140] wlan0: authenticate with AP 00:14:78:b5:fd:1c
[  130.854476] wlan0: RX authentication from 00:14:78:b5:fd:1c (alg=0 transaction=2 status=0)
[  130.854481] wlan0: authenticated
[  130.854485] wlan0: associate with AP 00:14:78:b5:fd:1c
[  130.856612] wlan0: RX AssocResp from 00:14:78:b5:fd:1c (capab=0x421 status=0 aid=1)
[  130.856615] wlan0: associated
[  130.860779] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  141.220632] wlan0: no IPv6 routers present
[  146.800737] wlan0: deauthenticate(reason=3)
[  148.081686] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  149.025671] wlan0: Initial auth_alg=0
[  149.025677] wlan0: authenticate with AP 00:14:78:b5:fd:1c
[  149.028106] wlan0: RX authentication from 00:14:78:b5:fd:1c (alg=0 transaction=2 status=0)
[  149.028112] wlan0: authenticated
[  149.028116] wlan0: associate with AP 00:14:78:b5:fd:1c
[  149.030240] wlan0: RX AssocResp from 00:14:78:b5:fd:1c (capab=0x421 status=0 aid=1)
[  149.030244] wlan0: associated
[  149.034406] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  159.693480] wlan0: no IPv6 routers present
[  169.762117] wlan0: duplicate address detected!
[13935.239135] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13953.424871] wlan0: deauthenticate(reason=3)
[13954.666106] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13955.649994] wlan0: Initial auth_alg=0
[13955.650001] wlan0: authenticate with AP 00:14:78:b5:fd:1c
[13955.651938] wlan0: RX authentication from 00:14:78:b5:fd:1c (alg=0 transaction=2 status=0)
[13955.651944] wlan0: authenticated
[13955.651948] wlan0: associate with AP 00:14:78:b5:fd:1c
[13955.654072] wlan0: RX AssocResp from 00:14:78:b5:fd:1c (capab=0x421 status=0 aid=1)
[13955.654076] wlan0: associated
[13955.658235] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13955.764413] wlan0: duplicate address detected!
[13962.391225] wlan0: duplicate address detected!

```

---

### Post by wieman01 on 2008-03-02
My Ralink tutorial does not require an Ethernet connection, the Ubuntu CD will do. Want do give it a go (signature)?

---

### Post by NEUR0M4NCER on 2008-03-02
Do you mean the ndiswrapper method? Going out for an hour, but i'll give it a bash when I get back - is there a way to reverse it (i.e. so I don't need to fresh install to check what to do next)?


Thanks!

---

### Post by wieman01 on 2008-03-02
Yes, the 'ndiswrapper' method. You can reverse it by un-blacklisting the native driver. You'll see what I mean. Give it a shot and post there if you encounter problems. You also need to get the 64-bit Windows driver for your device.

---

