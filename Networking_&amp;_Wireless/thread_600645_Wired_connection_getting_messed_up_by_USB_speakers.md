---
title: "Wired connection getting messed up by USB speakers"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by vnetha on 2007-11-02
Hi,

I recently installed Gutsy on my old DELL OptiPlex GX280.
I barely managed to get internet working.
then tried to see if I can plug in my Logitech V20 USB speakers.
it doesn't work.

but worse, my internet stops working when i restart the computer.
I have to plug the speakers out,
restart the network card,
do a "sudo dhclient",
and restart the machine again,
to get internet working.

has anyone seen a similar problem?
or am I totally crazy??


thanks,
Vivek.

---

### Post by noob12 on 2007-11-04
You might get a clue about what is going on by comparing the output of **dmesg** run after a boot with the speakers unplugged and again after a boot with the speakers plugged in.

---

### Post by vnetha on 2007-11-05
Hi,

I don't seem to have any clue what is going on with my computer.
I thought it might be the speakers that are the problem.
I'm not so sure any more.

I've plugged the speakers out and restarted several times,
but can't get internet to work.
It seems to randomly decide to work sometimes and fail at other times.
without making any changes at all.

this is the output with the speakers plugged out...

```
vivek@vivek-desktop:~$ dmesg
[ 0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929
(prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-
generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007f686c00 (usable)
[ 0.000000] BIOS-e820: 000000007f686c00 - 000000007f688c00 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007f688c00 - 000000007f68ac00 (ACPI data)
[ 0.000000] BIOS-e820: 000000007f68ac00 - 0000000080000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[ 0.000000] 1142MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] found SMP MP-table at 000fe710
[ 0.000000] Entering add_active_range(0, 0, 521862) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 229376
[ 0.000000] HighMem 229376 -> 521862
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 521862
[ 0.000000] On node 0 totalpages: 521862
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 1760 pages used for memmap
[ 0.000000] Normal zone: 223520 pages, LIFO batch:31
[ 0.000000] HighMem zone: 2285 pages used for memmap
[ 0.000000] HighMem zone: 290201 pages, LIFO batch:31
[ 0.000000] DMI 2.3 present.
[ 0.000000] ACPI: RSDP signature @ 0xC00FEC00 checksum 0
[ 0.000000] ACPI: RSDP 000FEC00, 0014 (r0 DELL )
[ 0.000000] ACPI: RSDT 000FCC05, 0040 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: FACP 000FCC45, 0074 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: DSDT FFFD060C, 30BF (r1 DELL dt_ex 1000 MSFT 100000D)
[ 0.000000] ACPI: FACS 7F686C00, 0040
[ 0.000000] ACPI: SSDT FFFD3808, 00BA (r1 DELL st_ex 1000 MSFT 100000D)
[ 0.000000] ACPI: APIC 000FCCB9, 0072 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: BOOT 000FCD2B, 0028 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: ASF! 000FCD53, 0067 (r16 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: MCFG 000FCDBA, 003E (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: HPET 000FCDF8, 0038 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: PM-Timer IO Port: 0x808
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] Processor #0 15:4 APIC version 20
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[ 0.000000] Processor #1 15:4 APIC version 20
[ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[ 0.000000] Built 1 zonelists. Total pages: 517785
[ 0.000000] Kernel command line: root=UUID=29f715d1-f20a-4f61-b61b-4195a916b217 ro quiet
splash
[ 0.000000] mapped APIC to ffffd000 (fee00000)
[ 0.000000] mapped IOAPIC to ffffc000 (fec00000)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Detected 2992.808 MHz processor.
[ 10.041077] Console: colour VGA+ 80x25
[ 10.041359] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 10.041685] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 10.135689] Memory: 2057908k/2087448k available (2015k kernel code, 28416k reserved, 916k data,
364k init, 1169944k highmem)
[ 10.135699] virtual kernel memory layout:
[ 10.135700] fixmap : 0xfff4d000 - 0xfffff000 ( 712 kB)
[ 10.135701] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 10.135702] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
[ 10.135703] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 10.135704] .init : 0xc03e3000 - 0xc043e000 ( 364 kB)
[ 10.135705] .data : 0xc02f7d26 - 0xc03dce84 ( 916 kB)
[ 10.135707] .text : 0xc0100000 - 0xc02f7d26 (2015 kB)
[ 10.135710] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 10.135749] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[ 10.135840] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 10.135846] hpet0: 3 64-bit timers, 14318180 Hz
[ 10.216818] Calibrating delay using timer specific routine.. 5990.24 BogoMIPS (lpj=11980497)
[ 10.216841] Security Framework v1.0.0 initialized
[ 10.216846] SELinux: Disabled at boot.
[ 10.216858] Mount-cache hash table entries: 512
[ 10.216983] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d
00000000 00000000
[ 10.216991] monitor/mwait feature present.
[ 10.216993] using mwait in idle threads.
[ 10.216998] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 10.217001] CPU: L2 cache: 1024K
[ 10.217003] CPU: Physical Processor ID: 0
[ 10.217006] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000
00000000
[ 10.217016] Compat vDSO mapped to ffffe000.
[ 10.217032] Checking 'hlt' instruction... OK.
[ 10.232902] SMP alternatives: switching to UP code
[ 10.233336] Early unpacking initramfs... done
[ 10.527123] ACPI: Core revision 20070126
[ 10.544175] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[ 10.576367] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[ 10.576384] SMP alternatives: switching to SMP code
[ 10.576487] Booting processor 1/1 eip 3000
[ 10.586598] Initializing CPU#1
[ 10.664563] Calibrating delay using timer specific routine.. 5985.06 BogoMIPS (lpj=11970121)
[ 10.664573] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d
00000000 00000000
[ 10.664580] monitor/mwait feature present.
[ 10.664586] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 10.664589] CPU: L2 cache: 1024K
[ 10.664591] CPU: Physical Processor ID: 0
[ 10.664593] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000
00000000
[ 10.664971] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[ 10.665013] Total of 2 processors activated (11975.30 BogoMIPS).
[ 10.665161] ENABLING IO-APIC IRQs
[ 10.665348] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 10.812577] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 10.832583] Brought up 2 CPUs
[ 10.975519] migration_cost=102
[ 10.975692] Booting paravirtualized kernel on bare hardware
[ 10.975767] Time: 2:48:14 Date: 10/06/107
[ 10.975793] NET: Registered protocol family 16
[ 10.975882] EISA bus registered
[ 10.975888] ACPI: bus type pci registered
[ 11.000440] PCI: PCI BIOS revision 2.10 entry at 0xfb258, last bus=4
[ 11.000443] PCI: Using configuration type 1
[ 11.000445] Setting up standard PCI resources
[ 11.006017] ACPI: EC: Look up EC in DSDT
[ 11.032571] ACPI: Interpreter enabled
[ 11.032576] ACPI: (supports S0 S1 S3 S4 S5)
[ 11.032599] ACPI: Using IOAPIC for interrupt routing
[ 11.070711] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 11.070731] PCI: Probing PCI hardware (bus 00)
[ 11.071368] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[ 11.071372] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[ 11.071927] PCI: Transparent bridge - 0000:00:1e.0
[ 11.071987] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 11.072436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[ 11.072970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[ 11.073240] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[ 11.073512] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[ 11.395331] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[ 11.395662] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[ 11.395994] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[ 11.396327] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[ 11.396659] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[ 11.396989] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[ 11.397317] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[ 11.397647] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[ 11.397799] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 11.397810] pnp: PnP ACPI init
[ 11.397823] ACPI: bus type pnp registered
[ 11.425940] pnp: PnP ACPI: found 12 devices
[ 11.425944] ACPI: ACPI bus type pnp unregistered
[ 11.425949] PnPBIOS: Disabled by ACPI PNP
[ 11.426001] PCI: Using ACPI for IRQ routing
[ 11.426004] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 11.437704] NET: Registered protocol family 8
[ 11.437707] NET: Registered protocol family 20
[ 11.437768] pnp: 00:01: ioport range 0x800-0x85f has been reserved
[ 11.437772] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[ 11.437775] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[ 11.437785] pnp: 00:09: iomem range 0x0-0x9ffff could not be reserved
[ 11.437788] pnp: 00:09: iomem range 0x100000-0xffffff could not be reserved
[ 11.437791] pnp: 00:09: iomem range 0x1000000-0x7f686bff could not be reserved
[ 11.437795] pnp: 00:09: iomem range 0xc0000-0xfffff could not be reserved
[ 11.437800] pnp: 00:0a: ioport range 0x100-0x1fe could not be reserved
[ 11.437803] pnp: 00:0a: ioport range 0x200-0x277 has been reserved
[ 11.437806] pnp: 00:0a: ioport range 0x280-0x2e7 has been reserved
[ 11.437808] pnp: 00:0a: ioport range 0x2f0-0x2f7 has been reserved
[ 11.437811] pnp: 00:0a: ioport range 0x300-0x377 could not be reserved
[ 11.437814] pnp: 00:0a: ioport range 0x380-0x3bb has been reserved
[ 11.437817] pnp: 00:0a: ioport range 0x3c0-0x3e7 could not be reserved
[ 11.437819] pnp: 00:0a: ioport range 0x3f6-0x3f7 could not be reserved
[ 11.437823] pnp: 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[ 11.437826] pnp: 00:0a: iomem range 0xfeda0000-0xfedacfff has been reserved
[ 11.440141] Time: tsc clocksource has been installed.
[ 11.440204] Switched to high resolution mode on CPU 0
[ 11.440236] Switched to high resolution mode on CPU 1
[ 11.468184] PCI: Bridge: 0000:00:01.0
[ 11.468186] IO window: disabled.
[ 11.468190] MEM window: dfd00000-dfdfffff
[ 11.468194] PREFETCH window: disabled.
[ 11.468198] PCI: Bridge: 0000:00:1c.0
[ 11.468199] IO window: disabled.
[ 11.468204] MEM window: dfc00000-dfcfffff
[ 11.468208] PREFETCH window: disabled.
[ 11.468213] PCI: Bridge: 0000:00:1c.1
[ 11.468214] IO window: disabled.
[ 11.468219] MEM window: dfb00000-dfbfffff
[ 11.468223] PREFETCH window: disabled.
[ 11.468228] PCI: Bridge: 0000:00:1e.0
[ 11.468229] IO window: disabled.
[ 11.468234] MEM window: disabled.
[ 11.468237] PREFETCH window: disabled.
[ 11.468254] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 11.468260] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 11.468278] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 11.468284] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 11.468303] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[ 11.468308] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[ 11.468320] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 11.468331] NET: Registered protocol family 2
[ 11.516063] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 11.516143] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[ 11.517002] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 11.517258] TCP: Hash tables configured (established 131072 bind 65536)
[ 11.517261] TCP reno registered
[ 11.532196] checking if image is initramfs... it is
[ 12.110763] Freeing initrd memory: 7355k freed
[ 12.110856] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[ 12.110860] Simple Boot Flag at 0x7a set to 0x1
[ 12.111142] audit: initializing netlink socket (disabled)
[ 12.111154] audit(1194317294.680:1): initialized
[ 12.111260] highmem bounce pool size: 64 pages
[ 12.113595] VFS: Disk quotas dquot_6.5.1
[ 12.113659] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 12.113755] io scheduler noop registered
[ 12.113758] io scheduler anticipatory registered
[ 12.113760] io scheduler deadline registered
[ 12.113776] io scheduler cfq registered (default)
[ 12.113794] Boot video device is 0000:00:02.0
[ 12.113951] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 12.113993] assign_interrupt_mode Found MSI capability
[ 12.113996] Allocate Port Service[0000:00:01.0:pcie00]
[ 12.114086] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 12.114130] assign_interrupt_mode Found MSI capability
[ 12.114133] Allocate Port Service[0000:00:1c.0:pcie00]
[ 12.114172] Allocate Port Service[0000:00:1c.0:pcie02]
[ 12.114268] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[ 12.114310] assign_interrupt_mode Found MSI capability
[ 12.114312] Allocate Port Service[0000:00:1c.1:pcie00]
[ 12.114479] isapnp: Scanning for PnP cards...
[ 12.465945] isapnp: No Plug & Play device found
[ 12.492628] Real Time Clock Driver v1.12ac
[ 12.492837] hpet_resources: 0xfed00000 is busy
[ 12.492856] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 12.492963] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 12.493662] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 12.494432] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 12.494633] input: Macintosh mouse button emulation as /class/input/input0
[ 12.494772] PNP: No PS/2 controller found. Probing ports directly.
[ 12.497253] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 12.497261] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 12.497448] mice: PS/2 mouse device common for all mice
[ 12.497582] EISA: Probing bus 0 at eisa.0
[ 12.497615] EISA: Detected 0 cards.
[ 12.497695] TCP cubic registered
[ 12.497708] NET: Registered protocol family 1
[ 12.497728] Using IPI No-Shortcut mode
[ 12.497883] Magic number: 15:476:813
[ 12.498000] hash matches device ptys7
[ 12.498012] hash matches device ptypa
[ 12.498226] Freeing unused kernel memory: 364k freed
[ 13.718029] AppArmor: AppArmor initialized<5>audit(1194317296.180:2): type=1505
info="AppArmor initialized" pid=1187
[ 13.726748] fuse init (API version 7.8)
[ 13.731979] Failure registering capabilities with primary security module.
[ 14.282844] usbcore: registered new interface driver usbfs
[ 14.282880] usbcore: registered new interface driver hub
[ 14.307950] usbcore: registered new device driver usb
[ 14.433353] USB Universal Host Controller Interface driver v3.0
[ 14.433530] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 18
[ 14.433547] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 14.433553] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 14.433725] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 14.433763] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
[ 14.433914] usb usb1: configuration #1 chosen from 1 choice
[ 14.433952] hub 1-0:1.0: USB hub found
[ 14.433961] hub 1-0:1.0: 2 ports detected
[ 14.485927] Floppy drive(s): fd0 is 1.44M
[ 14.493266] SCSI subsystem initialized
[ 14.499444] libata version 2.21 loaded.
[ 14.500736] FDC 0 is a post-1991 82077
[ 14.534685] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 18
[ 14.534704] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 14.534710] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 14.534749] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[ 14.534785] ehci_hcd 0000:00:1d.7: debug port 1
[ 14.534793] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[ 14.534802] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80800
[ 14.538682] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 14.538788] usb usb2: configuration #1 chosen from 1 choice
[ 14.538831] hub 2-0:1.0: USB hub found
[ 14.538840] hub 2-0:1.0: 8 ports detected
[ 14.642726] tg3.c:v3.77 (May 31, 2007)
[ 14.642749] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 14.642762] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 14.642830] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 19
[ 14.642842] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 14.642847] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 14.642884] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 14.642917] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[ 14.643053] usb usb3: configuration #1 chosen from 1 choice
[ 14.643095] hub 3-0:1.0: USB hub found
[ 14.643106] hub 3-0:1.0: 2 ports detected
[ 14.663649] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-
T Ethernet 00:11:43:2f:fd:aa
[ 14.663660] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[ 14.663665] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[ 14.746557] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[ 14.746574] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 14.746580] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 14.746616] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 14.746649] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
[ 14.746793] usb usb4: configuration #1 chosen from 1 choice
[ 14.746834] hub 4-0:1.0: USB hub found
[ 14.746844] hub 4-0:1.0: 2 ports detected
[ 14.850485] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
[ 14.850499] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 14.850505] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 14.850538] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 14.850569] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000ff20
[ 14.850716] usb usb5: configuration #1 chosen from 1 choice
[ 14.850755] hub 5-0:1.0: USB hub found
[ 14.850765] hub 5-0:1.0: 2 ports detected
[ 14.960346] ata_piix 0000:00:1f.1: version 2.11
[ 14.960368] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[ 14.960413] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 14.960518] scsi0 : ata_piix
[ 14.960585] scsi1 : ata_piix
[ 14.960629] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[ 14.960635] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[ 15.250179] usb 4-1: new low speed USB device using uhci_hcd and address 2
[ 15.278411] ata1.00: ATAPI: LITE-ON CD-ROM LTN-489S, 8DS2, max UDMA/33
[ 15.424424] usb 4-1: configuration #1 chosen from 1 choice
[ 15.450344] ata1.00: configured for UDMA/33
[ 15.450376] ata2: port disabled. ignoring.
[ 15.450660] scsi 0:0:0:0: CD-ROM LITE-ON CD-ROM LTN-489S 8DS2 PQ: 0 ANSI: 5
[ 15.450748] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[ 15.606024] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 22
[ 15.606069] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 15.606123] scsi2 : ata_piix
[ 15.606200] scsi3 : ata_piix
[ 15.606247] ata3: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fea0 irq 22
[ 15.606253] ata4: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fea8 irq 22
[ 15.665965] usb 4-2: new low speed USB device using uhci_hcd and address 3
[ 15.770220] ata3.00: ATA-6: ST340014AS, 8.12, max UDMA/133
[ 15.770224] ata3.00: 78125000 sectors, multi 8: LBA48 NCQ (depth 0/32)
[ 15.786224] ata3.00: configured for UDMA/133
[ 15.842188] usb 4-2: configuration #1 chosen from 1 choice
[ 15.845255] usbcore: registered new interface driver hiddev
[ 15.860323] input: DELL DELL USB Keyboard as /class/input/input1
[ 15.860336] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.2-1
[ 15.872221] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[ 15.872256] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.
2-2
[ 15.872271] usbcore: registered new interface driver usbhid
[ 15.872276] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID
core driver
[ 15.941985] scsi 2:0:0:0: Direct-Access ATA ST340014AS 8.12 PQ: 0 ANSI: 5
[ 15.955792] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[ 15.955815] sd 2:0:0:0: [sda] Write Protect is off
[ 15.955821] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 15.955940] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 15.956021] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[ 15.956039] sd 2:0:0:0: [sda] Write Protect is off
[ 15.956043] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 15.956073] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 15.956079] sda:sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[ 15.959311] Uniform CD-ROM driver Revision: 3.20
[ 15.959367] sr 0:0:0:0: Attached scsi CD-ROM sr0
[ 15.965248] sda1 sda2 < sda5 >
[ 15.987751] sd 2:0:0:0: [sda] Attached SCSI disk
[ 15.995174] sr 0:0:0:0: Attached scsi generic sg0 type 5
[ 15.995206] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 16.248596] Attempting manual resume
[ 16.248600] swsusp: Resume From Partition 8:5
[ 16.248602] PM: Checking swsusp image.
[ 16.248786] PM: Resume from disk failed.
[ 16.288292] kjournald starting. Commit interval 5 seconds
[ 16.288306] EXT3-fs: mounted filesystem with ordered data mode.
[ 22.320408] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 22.361617] Linux agpgart interface v0.102 (c) Dave Jones
[ 22.386852] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 22.420485] agpgart: Detected an Intel 915G Chipset.
[ 22.421176] agpgart: Detected 7932K stolen memory.
[ 22.435504] agpgart: AGP aperture is 256M @ 0xc0000000
[ 22.799776] iTCO_vendor_support: vendor-support=0
[ 22.801110] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[ 22.801202] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[ 22.801214] iTCO_wdt: No card detected
[ 22.817200] input: PC Speaker as /class/input/input3
[ 22.965908] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[ 22.965912] don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[ 22.965914] you are certain that your <4>intel_rng: system has a functional
[ 22.965916] RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[ 23.038691] parport_pc 00:07: reported by Plug and Play ACPI
[ 23.038751] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO
[PCSPP,TRISTATE,COMPAT,ECP]
[ 23.545266] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 21
[ 23.545290] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[ 23.965762] intel8x0_measure_ac97_clock: measured 55083 usecs
[ 23.965766] intel8x0: clocking to 48000
[ 24.092608] lp0: using parport0 (interrupt-driven).
[ 24.138516] Adding 1646620k swap on /dev/sda5. Priority:-1 extents:1 across:1646620k
[ 24.368079] EXT3 FS on sda1, internal journal
[ 25.402644] input: Power Button (FF) as /class/input/input4
[ 25.402672] ACPI: Power Button (FF) [PWRF]
[ 25.402733] input: Power Button (CM) as /class/input/input5
[ 25.402759] ACPI: Power Button (CM) [VBTN]
[ 25.494116] No dock devices found.
[ 26.839932] ppdev: user-space parallel port driver
[ 26.934187] audit(1194317309.437:3): type=1503 operation="inode_permission"
requested_mask="a" denied_mask="a" name="/dev/tty" pid=4653 profile="/usr/sbin/cupsd"
[ 26.997540] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 26.997546] apm: disabled - APM is not SMP safe.
[ 27.338687] Failure registering capabilities with primary security module.
[ 27.502003] Bluetooth: Core ver 2.11
[ 27.502383] NET: Registered protocol family 31
[ 27.502389] Bluetooth: HCI device and connection manager initialized
[ 27.502394] Bluetooth: HCI socket layer initialized
[ 27.511301] Bluetooth: L2CAP ver 2.8
[ 27.511307] Bluetooth: L2CAP socket layer initialized
[ 27.611991] Bluetooth: RFCOMM socket layer initialized
[ 27.612386] Bluetooth: RFCOMM TTY layer initialized
[ 27.612392] Bluetooth: RFCOMM ver 1.8
[ 30.614635] [drm] Initialized drm 1.1.0 20060810
[ 30.617255] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 30.617742] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 41.324014] tg3: eth0: Link is up at 10 Mbps, full duplex.
[ 41.324019] tg3: eth0: Flow control is off for TX and off for RX.
[ 43.500954] NET: Registered protocol family 17
[ 109.124550] NET: Registered protocol family 10
[ 109.124820] lo: Disabled Privacy Extensions
[ 119.873225] eth0: no IPv6 routers present
```

Please help!


thanks,
Vivek.

---

### Post by noob12 on 2007-11-05
OK.  I'm guessing it doesn't have anything to do with the USB speakers.  

My only suggestion is still to try to compare what things look like when things work with what they look like when things don't work.

Try to capture the output of these commands when you have things working and also when you don't.  Then we can try to compare and see what's wrong.

```

dmesg

sudo ethtool eth0

sudo ethtool -k eth0

grep dhclient /var/log/syslog

ifconfig -a

cat /etc/resolv.conf

```

---

### Post by kevdog on 2007-11-05
noob12 makes an appearance -- welcome back

---

### Post by vnetha on 2007-11-07
Hi,

It has worked a few times before,
but for one reason or another, 
I haven't been able to get internet to work in the past couple of days.

I've restarted the computer and the network device several times.
and tried what few tricks I knew to force it to work, but to no avail.
I'm continuing to try.

meanwhile, here are the outputs when I have no connectivity...
```

vivek@vivek-desktop:~$ dmesg
[ 0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929
(prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu
2.6.22-14.46-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007f686c00 (usable)
[ 0.000000] BIOS-e820: 000000007f686c00 - 000000007f688c00 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007f688c00 - 000000007f68ac00 (ACPI data)
[ 0.000000] BIOS-e820: 000000007f68ac00 - 0000000080000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[ 0.000000] 1142MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] found SMP MP-table at 000fe710
[ 0.000000] Entering add_active_range(0, 0, 521862) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 229376
[ 0.000000] HighMem 229376 -> 521862
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 521862
[ 0.000000] On node 0 totalpages: 521862
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 1760 pages used for memmap
[ 0.000000] Normal zone: 223520 pages, LIFO batch:31
[ 0.000000] HighMem zone: 2285 pages used for memmap
[ 0.000000] HighMem zone: 290201 pages, LIFO batch:31
[ 0.000000] DMI 2.3 present.
[ 0.000000] ACPI: RSDP signature @ 0xC00FEC00 checksum 0
[ 0.000000] ACPI: RSDP 000FEC00, 0014 (r0 DELL )
[ 0.000000] ACPI: RSDT 000FCC05, 0040 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: FACP 000FCC45, 0074 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: DSDT FFFD060C, 30BF (r1 DELL dt_ex 1000 MSFT 100000D)
[ 0.000000] ACPI: FACS 7F686C00, 0040
[ 0.000000] ACPI: SSDT FFFD3808, 00BA (r1 DELL st_ex 1000 MSFT 100000D)
[ 0.000000] ACPI: APIC 000FCCB9, 0072 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: BOOT 000FCD2B, 0028 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: ASF! 000FCD53, 0067 (r16 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: MCFG 000FCDBA, 003E (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: HPET 000FCDF8, 0038 (r1 DELL GX280 7 ASL 61)
[ 0.000000] ACPI: PM-Timer IO Port: 0x808
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] Processor #0 15:4 APIC version 20
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[ 0.000000] Processor #1 15:4 APIC version 20
[ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[ 0.000000] Built 1 zonelists. Total pages: 517785
[ 0.000000] Kernel command line: root=UUID=29f715d1-f20a-4f61-b61b-4195a916b217 ro quiet
splash
[ 0.000000] mapped APIC to ffffd000 (fee00000)
[ 0.000000] mapped IOAPIC to ffffc000 (fec00000)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Detected 2992.739 MHz processor.
[ 12.926224] Console: colour VGA+ 80x25
[ 12.926506] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 12.926829] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 13.020879] Memory: 2057908k/2087448k available (2015k kernel code, 28416k reserved, 916k
data, 364k init, 1169944k highmem)
[ 13.020889] virtual kernel memory layout:
[ 13.020890] fixmap : 0xfff4d000 - 0xfffff000 ( 712 kB)
[ 13.020891] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 13.020892] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
[ 13.020893] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 13.020894] .init : 0xc03e3000 - 0xc043e000 ( 364 kB)
[ 13.020895] .data : 0xc02f7d26 - 0xc03dce84 ( 916 kB)
[ 13.020896] .text : 0xc0100000 - 0xc02f7d26 (2015 kB)
[ 13.020899] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 13.020937] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[ 13.021028] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 13.021034] hpet0: 3 64-bit timers, 14318180 Hz
[ 13.102006] Calibrating delay using timer specific routine.. 5990.22 BogoMIPS (lpj=11980455)
[ 13.102029] Security Framework v1.0.0 initialized
[ 13.102035] SELinux: Disabled at boot.
[ 13.102047] Mount-cache hash table entries: 512
[ 13.102172] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d
00000000 00000000
[ 13.102181] monitor/mwait feature present.
[ 13.102183] using mwait in idle threads.
[ 13.102188] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 13.102191] CPU: L2 cache: 1024K
[ 13.102193] CPU: Physical Processor ID: 0
[ 13.102196] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000
00000000
[ 13.102205] Compat vDSO mapped to ffffe000.
[ 13.102221] Checking 'hlt' instruction... OK.
[ 13.118090] SMP alternatives: switching to UP code
[ 13.118522] Early unpacking initramfs... done
[ 13.411997] ACPI: Core revision 20070126
[ 13.429018] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[ 13.461146] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[ 13.461165] SMP alternatives: switching to SMP code
[ 13.461266] Booting processor 1/1 eip 3000
[ 13.471376] Initializing CPU#1
[ 13.549751] Calibrating delay using timer specific routine.. 5985.07 BogoMIPS (lpj=11970150)
[ 13.549761] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d
00000000 00000000
[ 13.549767] monitor/mwait feature present.
[ 13.549773] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 13.549776] CPU: L2 cache: 1024K
[ 13.549778] CPU: Physical Processor ID: 0
[ 13.549781] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000
00000000
[ 13.550157] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[ 13.550199] Total of 2 processors activated (11975.30 BogoMIPS).
[ 13.550347] ENABLING IO-APIC IRQs
[ 13.550533] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 13.697769] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 13.717774] Brought up 2 CPUs
[ 13.803677] migration_cost=113
[ 13.803850] Booting paravirtualized kernel on bare hardware
[ 13.803925] Time: 2:55:48 Date: 10/07/107
[ 13.803951] NET: Registered protocol family 16
[ 13.804041] EISA bus registered
[ 13.804046] ACPI: bus type pci registered
[ 13.828566] PCI: PCI BIOS revision 2.10 entry at 0xfb258, last bus=4
[ 13.828569] PCI: Using configuration type 1
[ 13.828571] Setting up standard PCI resources
[ 13.834158] ACPI: EC: Look up EC in DSDT
[ 13.860705] ACPI: Interpreter enabled
[ 13.860709] ACPI: (supports S0 S1 S3 S4 S5)
[ 13.860732] ACPI: Using IOAPIC for interrupt routing
[ 13.898775] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 13.898795] PCI: Probing PCI hardware (bus 00)
[ 13.899421] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[ 13.899426] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[ 13.899979] PCI: Transparent bridge - 0000:00:1e.0
[ 13.900039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 13.900484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[ 13.901012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[ 13.901282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[ 13.901556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[ 14.223262] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[ 14.223593] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[ 14.223924] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[ 14.224250] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[ 14.224579] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[ 14.224910] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[ 14.225237] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[ 14.225573] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[ 14.225726] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 14.225737] pnp: PnP ACPI init
[ 14.225750] ACPI: bus type pnp registered
[ 14.253805] pnp: PnP ACPI: found 12 devices
[ 14.253808] ACPI: ACPI bus type pnp unregistered
[ 14.253813] PnPBIOS: Disabled by ACPI PNP
[ 14.253867] PCI: Using ACPI for IRQ routing
[ 14.253871] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 14.265557] NET: Registered protocol family 8
[ 14.265559] NET: Registered protocol family 20
[ 14.265620] pnp: 00:01: ioport range 0x800-0x85f has been reserved
[ 14.265624] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[ 14.265627] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[ 14.265637] pnp: 00:09: iomem range 0x0-0x9ffff could not be reserved
[ 14.265640] pnp: 00:09: iomem range 0x100000-0xffffff could not be reserved
[ 14.265644] pnp: 00:09: iomem range 0x1000000-0x7f686bff could not be reserved
[ 14.265647] pnp: 00:09: iomem range 0xc0000-0xfffff could not be reserved
[ 14.265652] pnp: 00:0a: ioport range 0x100-0x1fe could not be reserved
[ 14.265655] pnp: 00:0a: ioport range 0x200-0x277 has been reserved
[ 14.265658] pnp: 00:0a: ioport range 0x280-0x2e7 has been reserved
[ 14.265660] pnp: 00:0a: ioport range 0x2f0-0x2f7 has been reserved
[ 14.265663] pnp: 00:0a: ioport range 0x300-0x377 could not be reserved
[ 14.265666] pnp: 00:0a: ioport range 0x380-0x3bb has been reserved
[ 14.265669] pnp: 00:0a: ioport range 0x3c0-0x3e7 could not be reserved
[ 14.265671] pnp: 00:0a: ioport range 0x3f6-0x3f7 could not be reserved
[ 14.265675] pnp: 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[ 14.265678] pnp: 00:0a: iomem range 0xfeda0000-0xfedacfff has been reserved
[ 14.269361] Time: tsc clocksource has been installed.
[ 14.269427] Switched to high resolution mode on CPU 0
[ 14.269459] Switched to high resolution mode on CPU 1
[ 14.296039] PCI: Bridge: 0000:00:01.0
[ 14.296041] IO window: disabled.
[ 14.296046] MEM window: dfd00000-dfdfffff
[ 14.296050] PREFETCH window: disabled.
[ 14.296054] PCI: Bridge: 0000:00:1c.0
[ 14.296056] IO window: disabled.
[ 14.296061] MEM window: dfc00000-dfcfffff
[ 14.296064] PREFETCH window: disabled.
[ 14.296069] PCI: Bridge: 0000:00:1c.1
[ 14.296071] IO window: disabled.
[ 14.296076] MEM window: dfb00000-dfbfffff
[ 14.296079] PREFETCH window: disabled.
[ 14.296084] PCI: Bridge: 0000:00:1e.0
[ 14.296086] IO window: disabled.
[ 14.296090] MEM window: disabled.
[ 14.296094] PREFETCH window: disabled.
[ 14.296111] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 14.296118] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 14.296136] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 14.296142] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 14.296161] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[ 14.296166] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[ 14.296177] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 14.296188] NET: Registered protocol family 2
[ 14.341286] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 14.341368] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[ 14.342233] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 14.342489] TCP: Hash tables configured (established 131072 bind 65536)
[ 14.342492] TCP reno registered
[ 14.357417] checking if image is initramfs... it is
[ 14.935784] Freeing initrd memory: 7355k freed
[ 14.935883] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[ 14.935887] Simple Boot Flag at 0x7a set to 0x1
[ 14.936175] audit: initializing netlink socket (disabled)
[ 14.936189] audit(1194404148.624:1): initialized
[ 14.936290] highmem bounce pool size: 64 pages
[ 14.938622] VFS: Disk quotas dquot_6.5.1
[ 14.938693] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 14.938795] io scheduler noop registered
[ 14.938797] io scheduler anticipatory registered
[ 14.938799] io scheduler deadline registered
[ 14.938815] io scheduler cfq registered (default)
[ 14.938833] Boot video device is 0000:00:02.0
[ 14.938989] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 14.939030] assign_interrupt_mode Found MSI capability
[ 14.939034] Allocate Port Service[0000:00:01.0:pcie00]
[ 14.939123] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 14.939166] assign_interrupt_mode Found MSI capability
[ 14.939169] Allocate Port Service[0000:00:1c.0:pcie00]
[ 14.939211] Allocate Port Service[0000:00:1c.0:pcie02]
[ 14.939305] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[ 14.939347] assign_interrupt_mode Found MSI capability
[ 14.939350] Allocate Port Service[0000:00:1c.1:pcie00]
[ 14.939517] isapnp: Scanning for PnP cards...
[ 15.290977] isapnp: No Plug & Play device found
[ 15.317989] Real Time Clock Driver v1.12ac
[ 15.318206] hpet_resources: 0xfed00000 is busy
[ 15.318223] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 15.318325] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 15.319031] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 15.319797] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 15.320002] input: Macintosh mouse button emulation as /class/input/input0
[ 15.320140] PNP: No PS/2 controller found. Probing ports directly.
[ 15.322694] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 15.322703] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 15.322898] mice: PS/2 mouse device common for all mice
[ 15.323030] EISA: Probing bus 0 at eisa.0
[ 15.323063] EISA: Detected 0 cards.
[ 15.323142] TCP cubic registered
[ 15.323154] NET: Registered protocol family 1
[ 15.323177] Using IPI No-Shortcut mode
[ 15.323332] Magic number: 15:654:914
[ 15.323430] hash matches device ptywd
[ 15.323668] Freeing unused kernel memory: 364k freed
[ 16.543362] AppArmor: AppArmor initialized<5>audit(1194404150.124:2): type=1505
info="AppArmor initialized" pid=1187
[ 16.552095] fuse init (API version 7.8)
[ 16.557229] Failure registering capabilities with primary security module.
[ 17.080870] usbcore: registered new interface driver usbfs
[ 17.080904] usbcore: registered new interface driver hub
[ 17.080937] usbcore: registered new device driver usb
[ 17.082133] USB Universal Host Controller Interface driver v3.0
[ 17.082196] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 18
[ 17.082212] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 17.082218] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 17.082354] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 17.082386] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
[ 17.082539] usb usb1: configuration #1 chosen from 1 choice
[ 17.082584] hub 1-0:1.0: USB hub found
[ 17.082593] hub 1-0:1.0: 2 ports detected
[ 17.183956] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 19
[ 17.183975] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 17.183981] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 17.184020] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[ 17.184054] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[ 17.184211] usb usb2: configuration #1 chosen from 1 choice
[ 17.184259] hub 2-0:1.0: USB hub found
[ 17.184268] hub 2-0:1.0: 2 ports detected
[ 17.288069] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[ 17.288085] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 17.288091] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 17.288126] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[ 17.288158] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
[ 17.288298] usb usb3: configuration #1 chosen from 1 choice
[ 17.288343] hub 3-0:1.0: USB hub found
[ 17.288357] hub 3-0:1.0: 2 ports detected
[ 17.298768] Floppy drive(s): fd0 is 1.44M
[ 17.307193] SCSI subsystem initialized
[ 17.315442] libata version 2.21 loaded.
[ 17.319632] FDC 0 is a post-1991 82077
[ 17.391815] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 18
[ 17.391834] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 17.391840] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 17.391879] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[ 17.391915] ehci_hcd 0000:00:1d.7: debug port 1
[ 17.391923] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[ 17.391933] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80800
[ 17.395827] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 17.395935] usb usb4: configuration #1 chosen from 1 choice
[ 17.395978] hub 4-0:1.0: USB hub found
[ 17.395987] hub 4-0:1.0: 8 ports detected
[ 17.499894] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
[ 17.499906] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 17.499910] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 17.499939] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 17.499969] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000ff20
[ 17.500076] usb usb5: configuration #1 chosen from 1 choice
[ 17.500108] hub 5-0:1.0: USB hub found
[ 17.500115] hub 5-0:1.0: 2 ports detected
[ 17.607184] ata_piix 0000:00:1f.1: version 2.11
[ 17.607205] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[ 17.607247] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 17.607333] scsi0 : ata_piix
[ 17.607392] scsi1 : ata_piix
[ 17.607431] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[ 17.607436] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq
15
[ 17.923642] ata1.00: ATAPI: LITE-ON CD-ROM LTN-489S, 8DS2, max UDMA/33
[ 18.095548] ata1.00: configured for UDMA/33
[ 18.095582] ata2: port disabled. ignoring.
[ 18.095867] scsi 0:0:0:0: CD-ROM LITE-ON CD-ROM LTN-489S 8DS2 PQ: 0 ANSI: 5
[ 18.095953] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[ 18.251242] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 22
[ 18.251280] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 18.251328] scsi2 : ata_piix
[ 18.251399] scsi3 : ata_piix
[ 18.251437] ata3: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fea0 irq
22
[ 18.251442] ata4: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fea8 irq
22
[ 18.287200] usb 3-1: new low speed USB device using uhci_hcd and address 2
[ 18.415438] ata3.00: ATA-6: ST340014AS, 8.12, max UDMA/133
[ 18.415442] ata3.00: 78125000 sectors, multi 8: LBA48 NCQ (depth 0/32)
[ 18.431443] ata3.00: configured for UDMA/133
[ 18.461658] usb 3-1: configuration #1 chosen from 1 choice
[ 18.587201] scsi 2:0:0:0: Direct-Access ATA ST340014AS 8.12 PQ: 0 ANSI: 5
[ 18.587655] tg3.c:v3.77 (May 31, 2007)
[ 18.587683] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 18.587699] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 18.601249] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[ 18.601366] sd 2:0:0:0: [sda] Write Protect is off
[ 18.601372] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 18.601404] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or
FUA
[ 18.601488] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[ 18.601505] sd 2:0:0:0: [sda] Write Protect is off
[ 18.601509] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 18.601540] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or
FUA
[ 18.601547] sda:sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[ 18.602467] Uniform CD-ROM driver Revision: 3.20
[ 18.602544] sr 0:0:0:0: Attached scsi CD-ROM sr0
[ 18.608209] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express)
10/100/1000Base-T Ethernet 00:11:43:2f:fd:aa
[ 18.608220] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[ 18.608224] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[ 18.608420] sda1 sda2 < sda5 >
[ 18.630940] sd 2:0:0:0: [sda] Attached SCSI disk
[ 18.637815] sr 0:0:0:0: Attached scsi generic sg0 type 5
[ 18.637851] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 18.703013] usb 3-2: new low speed USB device using uhci_hcd and address 3
[ 18.879431] usb 3-2: configuration #1 chosen from 1 choice
[ 18.882482] usbcore: registered new interface driver hiddev
[ 18.897690] input: DELL DELL USB Keyboard as /class/input/input1
[ 18.897705] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.2-1
[ 18.908538] Attempting manual resume
[ 18.908542] swsusp: Resume From Partition 8:5
[ 18.908544] PM: Checking swsusp image.
[ 18.908725] PM: Resume from disk failed.
[ 18.909551] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[ 18.909584] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.
2-2
[ 18.909603] usbcore: registered new interface driver usbhid
[ 18.909609] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID
core driver
[ 18.948148] kjournald starting. Commit interval 5 seconds
[ 18.948158] EXT3-fs: mounted filesystem with ordered data mode.
[ 25.181057] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 25.267824] iTCO_vendor_support: vendor-support=0
[ 25.284379] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[ 25.284470] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[ 25.284482] iTCO_wdt: No card detected
[ 25.305008] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 25.619172] input: PC Speaker as /class/input/input3
[ 25.625869] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[ 25.625874] don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[ 25.625876] you are certain that your <4>intel_rng: system has a functional
[ 25.625878] RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[ 25.789195] Linux agpgart interface v0.102 (c) Dave Jones
[ 25.797881] agpgart: Detected an Intel 915G Chipset.
[ 25.798577] agpgart: Detected 7932K stolen memory.
[ 25.813628] agpgart: AGP aperture is 256M @ 0xc0000000
[ 25.833298] parport_pc 00:07: reported by Plug and Play ACPI
[ 25.833362] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO
[PCSPP,TRISTATE,COMPAT,ECP]
[ 26.246838] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 21
[ 26.246861] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[ 26.666767] intel8x0_measure_ac97_clock: measured 55099 usecs
[ 26.666770] intel8x0: clocking to 48000
[ 26.810818] lp0: using parport0 (interrupt-driven).
[ 26.856786] Adding 1646620k swap on /dev/sda5. Priority:-1 extents:1 across:1646620k
[ 27.078002] EXT3 FS on sda1, internal journal
[ 28.131603] input: Power Button (FF) as /class/input/input4
[ 28.131631] ACPI: Power Button (FF) [PWRF]
[ 28.131693] input: Power Button (CM) as /class/input/input5
[ 28.131719] ACPI: Power Button (CM) [VBTN]
[ 28.255477] No dock devices found.
[ 29.550135] ppdev: user-space parallel port driver
[ 29.662054] audit(1194404163.543:3): type=1503 operation="inode_permission"
requested_mask="a" denied_mask="a" name="/dev/tty" pid=4655 profile="/usr/sbin/cupsd"
[ 29.717740] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 29.717747] apm: disabled - APM is not SMP safe.
[ 30.022572] Failure registering capabilities with primary security module.
[ 30.186891] Bluetooth: Core ver 2.11
[ 30.187264] NET: Registered protocol family 31
[ 30.187270] Bluetooth: HCI device and connection manager initialized
[ 30.187275] Bluetooth: HCI socket layer initialized
[ 30.196006] Bluetooth: L2CAP ver 2.8
[ 30.196012] Bluetooth: L2CAP socket layer initialized
[ 30.264091] Bluetooth: RFCOMM socket layer initialized
[ 30.264454] Bluetooth: RFCOMM TTY layer initialized
[ 30.264459] Bluetooth: RFCOMM ver 1.8
[ 33.349821] [drm] Initialized drm 1.1.0 20060810
[ 33.354086] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 33.354774] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 43.813282] tg3: eth0: Link is up at 10 Mbps, full duplex.
[ 43.813287] tg3: eth0: Flow control is off for TX and off for RX.
[ 45.993941] NET: Registered protocol family 17
[ 69.443051] UDF-fs: No VRS found
[ 69.449940] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 69.479237] ISOFS: changing to secondary root
[ 110.991734] NET: Registered protocol family 10
[ 110.992011] lo: Disabled Privacy Extensions
[ 121.668520] eth0: no IPv6 routers present
vivek@vivek-desktop:~$ sudo ethtool eth0
[sudo] password for vivek:
Settings for eth0:
Supported ports: [ MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 10Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: g
Wake-on: d
Current message level: 0x000000ff (255)
Link detected: yes
vivek@vivek-desktop:~$ sudo ethtool -k eth0
Offload parameters for eth0:
Cannot get device udp large send offload settings: Operation not supported
rx-checksumming: on
tx-checksumming: on
scatter-gather: on
tcp segmentation offload: on
udp fragmentation offload: off
generic segmentation offload: off
vivek@vivek-desktop:~$ grep dhclient /var/log/syslog
Nov 6 06:48:22 vivek-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.5
Nov 6 06:48:22 vivek-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov 6 06:48:22 vivek-desktop dhclient: All rights reserved.
Nov 6 06:48:22 vivek-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 6 06:48:22 vivek-desktop dhclient:
Nov 6 06:48:23 vivek-desktop dhclient: Listening on LPF/eth0/00:11:43:2f:fd:aa
Nov 6 06:48:23 vivek-desktop dhclient: Sending on LPF/eth0/00:11:43:2f:fd:aa
Nov 6 06:48:23 vivek-desktop dhclient: Sending on Socket/fallback
Nov 6 06:48:23 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 3
Nov 6 06:48:26 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 7
Nov 6 06:48:33 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 10
Nov 6 06:48:43 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 11
Nov 6 06:48:54 vivek-desktop dhclient: No DHCPOFFERS received.
Nov 6 06:48:54 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov 6 06:51:46 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 4
Nov 6 06:51:50 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 6
Nov 6 06:51:56 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 12
Nov 6 06:52:08 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 9
Nov 6 06:52:17 vivek-desktop dhclient: No DHCPOFFERS received.
Nov 6 06:52:17 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov 6 06:56:47 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 3
Nov 6 06:56:50 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 4
Nov 6 06:56:54 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 11
Nov 6 06:57:05 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 9
Nov 6 06:57:14 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 4
Nov 6 06:57:18 vivek-desktop dhclient: No DHCPOFFERS received.
Nov 6 06:57:18 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov 6 06:59:59 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 6 07:00:05 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 6 07:00:26 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 6
Nov 6 07:00:32 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 14
Nov 6 07:00:46 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 11
Nov 6 07:00:57 vivek-desktop dhclient: No DHCPOFFERS received.
Nov 6 07:00:57 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov 6 18:56:20 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 6 18:56:27 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 6 18:56:42 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 5
Nov 6 18:56:47 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 6
Nov 6 18:56:53 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 6
Nov 6 18:56:59 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 12
Nov 6 18:57:11 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 2
Nov 6 18:57:13 vivek-desktop dhclient: No DHCPOFFERS received.
Nov 6 18:57:13 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
vivek@vivek-desktop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:11:43:2F:FD:AA
inet6 addr: fe80::211:43ff:fe2f:fdaa/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:43 dropped:0 overruns:0 frame:477
TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:15327 (14.9 KB)
Interrupt:16
eth0:avah Link encap:Ethernet HWaddr 00:11:43:2F:FD:AA
inet addr:169.254.8.107 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:16
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:49 errors:0 dropped:0 overruns:0 frame:0
TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4680 (4.5 KB) TX bytes:4680 (4.5 KB)
vivek@vivek-desktop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!
search socal.rr.com
nameserver 192.168.1.1
```

Please help!


thanks,
Vivek.

---

### Post by noob12 on 2007-11-07
This from the ifconfig output
```

RX packets:0 errors:43 dropped:0 overruns:0 frame:477

```
suggests a number of possible issues to look at:  timing or checksum issues, or a problem with your physical connection.

First check the physical cable.  Try replacing it with another one that is known to work.

---

### Post by vnetha on 2007-11-07
Hi, 

I replaced the network cable and things are working again.
but i don't know it things are working for good,
or if everything will break once i restart..
so just for kicks, here are the outputs again...

```
vivek@vivek-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f686c00 (usable)
[    0.000000]  BIOS-e820: 000000007f686c00 - 000000007f688c00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f688c00 - 000000007f68ac00 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f68ac00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 521862) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521862
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521862
[    0.000000] On node 0 totalpages: 521862
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2285 pages used for memmap
[    0.000000]   HighMem zone: 290201 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FEC00 checksum 0
[    0.000000] ACPI: RSDP 000FEC00, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FCC05, 0040 (r1 DELL    GX280          7 ASL        61)
[    0.000000] ACPI: FACP 000FCC45, 0074 (r1 DELL    GX280          7 ASL        61)
[    0.000000] ACPI: DSDT FFFD060C, 30BF (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 7F686C00, 0040
[    0.000000] ACPI: SSDT FFFD3808, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FCCB9, 0072 (r1 DELL    GX280          7 ASL        61)
[    0.000000] ACPI: BOOT 000FCD2B, 0028 (r1 DELL    GX280          7 ASL        61)
[    0.000000] ACPI: ASF! 000FCD53, 0067 (r16 DELL    GX280          7 ASL        61)
[    0.000000] ACPI: MCFG 000FCDBA, 003E (r1 DELL    GX280          7 ASL        61)
[    0.000000] ACPI: HPET 000FCDF8, 0038 (r1 DELL    GX280          7 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 517785
[    0.000000] Kernel command line: root=UUID=29f715d1-f20a-4f61-b61b-4195a916b217 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2992.874 MHz processor.
[   34.640445] Console: colour VGA+ 80x25
[   34.640726] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   34.641052] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   34.735041] Memory: 2057908k/2087448k available (2015k kernel code, 28416k reserved, 916k data, 364k init, 1169944k highmem)
[   34.735050] virtual kernel memory layout:
[   34.735051]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   34.735053]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   34.735054]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   34.735055]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   34.735056]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   34.735057]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   34.735058]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   34.735061] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   34.735101] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   34.735193] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   34.735199] hpet0: 3 64-bit timers, 14318180 Hz
[   34.816169] Calibrating delay using timer specific routine.. 5990.24 BogoMIPS (lpj=11980484)
[   34.816191] Security Framework v1.0.0 initialized
[   34.816196] SELinux:  Disabled at boot.
[   34.816209] Mount-cache hash table entries: 512
[   34.816335] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   34.816343] monitor/mwait feature present.
[   34.816345] using mwait in idle threads.
[   34.816350] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   34.816353] CPU: L2 cache: 1024K
[   34.816355] CPU: Physical Processor ID: 0
[   34.816357] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   34.816367] Compat vDSO mapped to ffffe000.
[   34.816383] Checking 'hlt' instruction... OK.
[   34.832250] SMP alternatives: switching to UP code
[   34.832673] Early unpacking initramfs... done
[   35.126213] ACPI: Core revision 20070126
[   35.143233] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   35.175363] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   35.175381] SMP alternatives: switching to SMP code
[   35.175483] Booting processor 1/1 eip 3000
[   35.185593] Initializing CPU#1
[   35.263913] Calibrating delay using timer specific routine.. 5985.02 BogoMIPS (lpj=11970050)
[   35.263925] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   35.263931] monitor/mwait feature present.
[   35.263937] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   35.263940] CPU: L2 cache: 1024K
[   35.263942] CPU: Physical Processor ID: 0
[   35.263945] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   35.264322] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   35.264367] Total of 2 processors activated (11975.26 BogoMIPS).
[   35.264514] ENABLING IO-APIC IRQs
[   35.264701] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   35.411929] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   35.431935] Brought up 2 CPUs
[   35.517998] migration_cost=125
[   35.518171] Booting paravirtualized kernel on bare hardware
[   35.518247] Time:  4:01:02  Date: 10/08/107
[   35.518273] NET: Registered protocol family 16
[   35.518362] EISA bus registered
[   35.518369] ACPI: bus type pci registered
[   35.542894] PCI: PCI BIOS revision 2.10 entry at 0xfb258, last bus=4
[   35.542897] PCI: Using configuration type 1
[   35.542899] Setting up standard PCI resources
[   35.548472] ACPI: EC: Look up EC in DSDT
[   35.575001] ACPI: Interpreter enabled
[   35.575006] ACPI: (supports S0 S1 S3 S4 S5)
[   35.575028] ACPI: Using IOAPIC for interrupt routing
[   35.613105] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.613126] PCI: Probing PCI hardware (bus 00)
[   35.613755] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   35.613760] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[   35.614316] PCI: Transparent bridge - 0000:00:1e.0
[   35.614376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.614823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   35.615352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   35.615623] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[   35.615906] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[   35.937475] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   35.937807] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   35.938137] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   35.938464] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   35.938793] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   35.939123] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   35.939450] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   35.939787] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   35.939940] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.939951] pnp: PnP ACPI init
[   35.939963] ACPI: bus type pnp registered
[   35.968022] pnp: PnP ACPI: found 12 devices
[   35.968025] ACPI: ACPI bus type pnp unregistered
[   35.968030] PnPBIOS: Disabled by ACPI PNP
[   35.968084] PCI: Using ACPI for IRQ routing
[   35.968088] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   35.979762] NET: Registered protocol family 8
[   35.979765] NET: Registered protocol family 20
[   35.979827] pnp: 00:01: ioport range 0x800-0x85f has been reserved
[   35.979830] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[   35.979833] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[   35.979844] pnp: 00:09: iomem range 0x0-0x9ffff could not be reserved
[   35.979847] pnp: 00:09: iomem range 0x100000-0xffffff could not be reserved
[   35.979850] pnp: 00:09: iomem range 0x1000000-0x7f686bff could not be reserved
[   35.979854] pnp: 00:09: iomem range 0xc0000-0xfffff could not be reserved
[   35.979859] pnp: 00:0a: ioport range 0x100-0x1fe could not be reserved
[   35.979862] pnp: 00:0a: ioport range 0x200-0x277 has been reserved
[   35.979864] pnp: 00:0a: ioport range 0x280-0x2e7 has been reserved
[   35.979867] pnp: 00:0a: ioport range 0x2f0-0x2f7 has been reserved
[   35.979870] pnp: 00:0a: ioport range 0x300-0x377 could not be reserved
[   35.979872] pnp: 00:0a: ioport range 0x380-0x3bb has been reserved
[   35.979875] pnp: 00:0a: ioport range 0x3c0-0x3e7 could not be reserved
[   35.979878] pnp: 00:0a: ioport range 0x3f6-0x3f7 could not be reserved
[   35.979881] pnp: 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   35.979884] pnp: 00:0a: iomem range 0xfeda0000-0xfedacfff has been reserved
[   35.983520] Time: tsc clocksource has been installed.
[   35.983590] Switched to high resolution mode on CPU 0
[   35.983620] Switched to high resolution mode on CPU 1
[   36.010243] PCI: Bridge: 0000:00:01.0
[   36.010245]   IO window: disabled.
[   36.010250]   MEM window: dfd00000-dfdfffff
[   36.010253]   PREFETCH window: disabled.
[   36.010257] PCI: Bridge: 0000:00:1c.0
[   36.010259]   IO window: disabled.
[   36.010264]   MEM window: dfc00000-dfcfffff
[   36.010267]   PREFETCH window: disabled.
[   36.010272] PCI: Bridge: 0000:00:1c.1
[   36.010274]   IO window: disabled.
[   36.010279]   MEM window: dfb00000-dfbfffff
[   36.010282]   PREFETCH window: disabled.
[   36.010287] PCI: Bridge: 0000:00:1e.0
[   36.010288]   IO window: disabled.
[   36.010293]   MEM window: disabled.
[   36.010296]   PREFETCH window: disabled.
[   36.010314] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.010320] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   36.010338] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.010344] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   36.010363] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   36.010369] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   36.010380] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   36.010391] NET: Registered protocol family 2
[   36.055450] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   36.055534] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   36.056396] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   36.056663] TCP: Hash tables configured (established 131072 bind 65536)
[   36.056666] TCP reno registered
[   36.071580] checking if image is initramfs... it is
[   36.650303] Freeing initrd memory: 7355k freed
[   36.650403] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   36.650407] Simple Boot Flag at 0x7a set to 0x1
[   36.650698] audit: initializing netlink socket (disabled)
[   36.650710] audit(1194494462.624:1): initialized
[   36.650811] highmem bounce pool size: 64 pages
[   36.653143] VFS: Disk quotas dquot_6.5.1
[   36.653213] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   36.653315] io scheduler noop registered
[   36.653318] io scheduler anticipatory registered
[   36.653320] io scheduler deadline registered
[   36.653336] io scheduler cfq registered (default)
[   36.653353] Boot video device is 0000:00:02.0
[   36.653509] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   36.653550] assign_interrupt_mode Found MSI capability
[   36.653553] Allocate Port Service[0000:00:01.0:pcie00]
[   36.653642] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   36.653685] assign_interrupt_mode Found MSI capability
[   36.653688] Allocate Port Service[0000:00:1c.0:pcie00]
[   36.653730] Allocate Port Service[0000:00:1c.0:pcie02]
[   36.653823] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   36.653865] assign_interrupt_mode Found MSI capability
[   36.653868] Allocate Port Service[0000:00:1c.1:pcie00]
[   36.654038] isapnp: Scanning for PnP cards...
[   37.005503] isapnp: No Plug & Play device found
[   37.032255] Real Time Clock Driver v1.12ac
[   37.032473] hpet_resources: 0xfed00000 is busy
[   37.032490] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.032593] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.033303] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.034068] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.034278] input: Macintosh mouse button emulation as /class/input/input0
[   37.034415] PNP: No PS/2 controller found. Probing ports directly.
[   37.036975] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.036983] serio: i8042 AUX port at 0x60,0x64 irq 12
[   37.037178] mice: PS/2 mouse device common for all mice
[   37.037312] EISA: Probing bus 0 at eisa.0
[   37.037344] EISA: Detected 0 cards.
[   37.037424] TCP cubic registered
[   37.037436] NET: Registered protocol family 1
[   37.037459] Using IPI No-Shortcut mode
[   37.037611]   Magic number: 15:14:9
[   37.037953] Freeing unused kernel memory: 364k freed
[   38.258241] AppArmor: AppArmor initialized<5>audit(1194494464.124:2):  type=1505 info="AppArmor initialized" pid=1187
[   38.267011] fuse init (API version 7.8)
[   38.272108] Failure registering capabilities with primary security module.
[   38.886210] usbcore: registered new interface driver usbfs
[   38.886249] usbcore: registered new interface driver hub
[   38.886284] usbcore: registered new device driver usb
[   38.887501] USB Universal Host Controller Interface driver v3.0
[   38.887565] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 18
[   38.887580] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   38.887585] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   38.887721] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   38.887752] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
[   38.887908] usb usb1: configuration #1 chosen from 1 choice
[   38.887949] hub 1-0:1.0: USB hub found
[   38.887958] hub 1-0:1.0: 2 ports detected
[   38.907366] SCSI subsystem initialized
[   38.915864] libata version 2.21 loaded.
[   38.990478] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 19
[   38.990494] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   38.990500] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   38.990537] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   38.990568] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[   38.990705] usb usb2: configuration #1 chosen from 1 choice
[   38.990746] hub 2-0:1.0: USB hub found
[   38.990755] hub 2-0:1.0: 2 ports detected
[   39.035763] Floppy drive(s): fd0 is 1.44M
[   39.052114] FDC 0 is a post-1991 82077
[   39.094117] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   39.094133] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   39.094139] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   39.094174] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   39.094206] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
[   39.094356] usb usb3: configuration #1 chosen from 1 choice
[   39.094398] hub 3-0:1.0: USB hub found
[   39.094408] hub 3-0:1.0: 2 ports detected
[   39.198051] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
[   39.198066] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   39.198072] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   39.198109] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   39.198140] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000ff20
[   39.198277] usb usb4: configuration #1 chosen from 1 choice
[   39.198318] hub 4-0:1.0: USB hub found
[   39.198327] hub 4-0:1.0: 2 ports detected
[   39.302692] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 18
[   39.302711] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   39.302717] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   39.302762] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   39.302800] ehci_hcd 0000:00:1d.7: debug port 1
[   39.302810] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   39.302823] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80800
[   39.306713] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.306865] usb usb5: configuration #1 chosen from 1 choice
[   39.306918] hub 5-0:1.0: USB hub found
[   39.306930] hub 5-0:1.0: 8 ports detected
[   39.410023] tg3.c:v3.77 (May 31, 2007)
[   39.410053] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.410067] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   39.430040] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:11:43:2f:fd:aa
[   39.430052] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   39.430057] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   39.432321] ata_piix 0000:00:1f.1: version 2.11
[   39.432336] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   39.432371] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   39.432441] scsi0 : ata_piix
[   39.432487] scsi1 : ata_piix
[   39.432517] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   39.432521] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   39.749916] ata1.00: ATAPI: LITE-ON CD-ROM LTN-489S, 8DS2, max UDMA/33
[   39.921827] ata1.00: configured for UDMA/33
[   39.921859] ata2: port disabled. ignoring.
[   39.922144] scsi 0:0:0:0: CD-ROM            LITE-ON  CD-ROM LTN-489S  8DS2 PQ: 0 ANSI: 5
[   39.922230] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   40.077524] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 22
[   40.077565] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   40.077612] scsi2 : ata_piix
[   40.077685] scsi3 : ata_piix
[   40.077723] ata3: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fea0 irq 22
[   40.077729] ata4: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fea8 irq 22
[   40.193452] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   40.241737] ata3.00: ATA-6: ST340014AS, 8.12, max UDMA/133
[   40.241741] ata3.00: 78125000 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   40.257742] ata3.00: configured for UDMA/133
[   40.367653] usb 3-1: configuration #1 chosen from 1 choice
[   40.413505] scsi 2:0:0:0: Direct-Access     ATA      ST340014AS       8.12 PQ: 0 ANSI: 5
[   40.430740] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   40.430745] Uniform CD-ROM driver Revision: 3.20
[   40.430803] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   40.431271] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[   40.431293] sd 2:0:0:0: [sda] Write Protect is off
[   40.431298] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.431329] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.431400] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[   40.431416] sd 2:0:0:0: [sda] Write Protect is off
[   40.431420] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.431449] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.431454]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   40.435505] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   40.439653]  sda1 sda2 < sda5 >
[   40.462194] sd 2:0:0:0: [sda] Attached SCSI disk
[   40.609255] usb 3-2: new low speed USB device using uhci_hcd and address 3
[   40.678437] Attempting manual resume
[   40.678441] swsusp: Resume From Partition 8:5
[   40.678443] PM: Checking swsusp image.
[   40.678630] PM: Resume from disk failed.
[   40.712623] kjournald starting.  Commit interval 5 seconds
[   40.712636] EXT3-fs: mounted filesystem with ordered data mode.
[   40.785405] usb 3-2: configuration #1 chosen from 1 choice
[   40.788425] usbcore: registered new interface driver hiddev
[   40.803677] input: DELL DELL USB Keyboard as /class/input/input1
[   40.803690] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.2-1
[   40.815471] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   40.815494] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-2
[   40.815507] usbcore: registered new interface driver usbhid
[   40.815511] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   46.708959] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.719087] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.897096] Linux agpgart interface v0.102 (c) Dave Jones
[   47.209647] agpgart: Detected an Intel 915G Chipset.
[   47.210360] agpgart: Detected 7932K stolen memory.
[   47.225377] agpgart: AGP aperture is 256M @ 0xc0000000
[   47.226033] iTCO_vendor_support: vendor-support=0
[   47.287003] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   47.287101] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   47.287113] iTCO_wdt: No card detected
[   47.642427] parport_pc 00:07: reported by Plug and Play ACPI
[   47.642487] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   47.648984] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   47.648988]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   47.648990]  you are certain that your <4>intel_rng: system has a functional
[   47.648992]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   47.667079] input: PC Speaker as /class/input/input3
[   48.103115] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 21
[   48.103138] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   48.521419] intel8x0_measure_ac97_clock: measured 55118 usecs
[   48.521423] intel8x0: clocking to 48000
[   48.650422] lp0: using parport0 (interrupt-driven).
[   48.696315] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   48.909270] EXT3 FS on sda1, internal journal
[   49.977585] input: Power Button (FF) as /class/input/input4
[   49.977615] ACPI: Power Button (FF) [PWRF]
[   49.977674] input: Power Button (CM) as /class/input/input5
[   49.977700] ACPI: Power Button (CM) [VBTN]
[   50.090118] No dock devices found.
[   51.431180] ppdev: user-space parallel port driver
[   51.530236] audit(1194494477.925:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4650 profile="/usr/sbin/cupsd"
[   51.574008] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   51.574015] apm: disabled - APM is not SMP safe.
[   51.870501] Failure registering capabilities with primary security module.
[   52.034822] Bluetooth: Core ver 2.11
[   52.035202] NET: Registered protocol family 31
[   52.035209] Bluetooth: HCI device and connection manager initialized
[   52.035215] Bluetooth: HCI socket layer initialized
[   52.044207] Bluetooth: L2CAP ver 2.8
[   52.044213] Bluetooth: L2CAP socket layer initialized
[   52.112011] Bluetooth: RFCOMM socket layer initialized
[   52.112372] Bluetooth: RFCOMM TTY layer initialized
[   52.112379] Bluetooth: RFCOMM ver 1.8
[   53.242547] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   53.242552] tg3: eth0: Flow control is off for TX and off for RX.
[   55.135583] [drm] Initialized drm 1.1.0 20060810
[   55.176896] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   55.178044] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   56.502482] NET: Registered protocol family 17
[   58.011397] NET: Registered protocol family 10
[   58.011671] lo: Disabled Privacy Extensions
[   68.283852] eth0: no IPv6 routers present
vivek@vivek-desktop:~$ sudo ethtool eth0
[sudo] password for vivek:
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes
vivek@vivek-desktop:~$ sudo ethtool -k eth0
Offload parameters for eth0:
Cannot get device udp large send offload settings: Operation not supported
rx-checksumming: on
tx-checksumming: on
scatter-gather: on
tcp segmentation offload: on
udp fragmentation offload: off
generic segmentation offload: off
vivek@vivek-desktop:~$ grep dhclient /var/log/syslog
Nov  6 06:48:22 vivek-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.5
Nov  6 06:48:22 vivek-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov  6 06:48:22 vivek-desktop dhclient: All rights reserved.
Nov  6 06:48:22 vivek-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov  6 06:48:22 vivek-desktop dhclient: 
Nov  6 06:48:23 vivek-desktop dhclient: Listening on LPF/eth0/00:11:43:2f:fd:aa
Nov  6 06:48:23 vivek-desktop dhclient: Sending on   LPF/eth0/00:11:43:2f:fd:aa
Nov  6 06:48:23 vivek-desktop dhclient: Sending on   Socket/fallback
Nov  6 06:48:23 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  6 06:48:26 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov  6 06:48:33 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov  6 06:48:43 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  6 06:48:54 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 06:48:54 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov  6 06:51:46 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov  6 06:51:50 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 06:51:56 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov  6 06:52:08 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov  6 06:52:17 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 06:52:17 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov  6 06:56:47 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  6 06:56:50 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov  6 06:56:54 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  6 06:57:05 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov  6 06:57:14 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov  6 06:57:18 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 06:57:18 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov  6 06:59:59 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 07:00:05 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 07:00:26 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 07:00:32 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov  6 07:00:46 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  6 07:00:57 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 07:00:57 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  6 18:56:20 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 18:56:27 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 18:56:42 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  6 18:56:47 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 18:56:53 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 18:56:59 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov  6 18:57:11 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Nov  6 18:57:13 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 18:57:13 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  6 19:11:59 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 19:12:05 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 19:12:18 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  6 19:12:26 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov  6 19:12:38 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  6 19:12:49 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 19:12:49 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  6 19:24:17 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 19:24:24 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 19:24:35 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 19:24:41 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov  6 19:24:50 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  6 19:25:01 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  6 19:25:06 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 19:25:06 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  6 19:25:35 vivek-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.5
Nov  6 19:25:35 vivek-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov  6 19:25:35 vivek-desktop dhclient: All rights reserved.
Nov  6 19:25:35 vivek-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov  6 19:25:35 vivek-desktop dhclient: 
Nov  6 19:25:36 vivek-desktop dhclient: Listening on LPF/eth0/00:11:43:2f:fd:aa
Nov  6 19:25:36 vivek-desktop dhclient: Sending on   LPF/eth0/00:11:43:2f:fd:aa
Nov  6 19:25:36 vivek-desktop dhclient: Sending on   Socket/fallback
Nov  6 19:25:40 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  6 19:25:45 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  6 19:25:53 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov  6 19:26:02 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov  6 19:26:11 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 19:26:11 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov  6 19:28:56 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 19:29:02 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 19:29:12 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 19:29:18 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov  6 19:29:25 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov  6 19:29:32 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov  6 19:29:42 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Nov  6 19:29:43 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 19:29:43 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  6 20:42:11 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 20:42:30 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov  6 20:42:37 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  6 20:42:45 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov  6 20:43:01 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 20:43:01 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  6 20:56:17 vivek-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.5
Nov  6 20:56:17 vivek-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov  6 20:56:17 vivek-desktop dhclient: All rights reserved.
Nov  6 20:56:17 vivek-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov  6 20:56:17 vivek-desktop dhclient: 
Nov  6 20:56:18 vivek-desktop dhclient: Listening on LPF/eth0/00:11:43:2f:fd:aa
Nov  6 20:56:18 vivek-desktop dhclient: Sending on   LPF/eth0/00:11:43:2f:fd:aa
Nov  6 20:56:18 vivek-desktop dhclient: Sending on   Socket/fallback
Nov  6 20:56:22 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  6 20:56:25 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 20:56:31 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 20:56:37 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  6 20:56:45 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  6 20:56:53 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 20:56:53 vivek-desktop dhclient: No working leases in persistent database - sleeping.
Nov  6 20:59:01 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 20:59:13 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov  6 20:59:20 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov  6 20:59:33 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  6 20:59:44 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 20:59:44 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  6 21:07:18 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 21:07:26 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 21:07:40 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 21:07:46 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov  6 21:07:58 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov  6 21:08:11 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  6 21:08:11 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  7 06:22:38 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  7 06:22:44 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  7 06:22:51 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  7 06:22:54 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  7 06:23:00 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov  7 06:23:14 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  7 06:23:22 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  7 06:23:22 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  7 06:29:10 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  7 06:29:32 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  7 06:29:37 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  7 06:29:42 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov  7 06:29:49 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  7 06:30:00 vivek-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  7 06:30:03 vivek-desktop dhclient: No DHCPOFFERS received.
Nov  7 06:30:03 vivek-desktop dhclient: Trying recorded lease 192.168.1.100
Nov  7 20:01:22 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  7 20:01:22 vivek-desktop dhclient: DHCPACK from 192.168.1.1
Nov  7 20:01:23 vivek-desktop dhclient: bound to 192.168.1.100 -- renewal in 288204 seconds.
vivek@vivek-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:43:2F:FD:AA  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe2f:fdaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1451952 (1.3 MB)  TX bytes:79400 (77.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vivek@vivek-desktop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search socal.rr.com


nameserver 192.168.1.1
```


thanks,
Vivek.

---

### Post by noob12 on 2007-11-08
Yes.  This looks much better now.  No receive errors on the interface anymore and an instant response on the DHCP renewal request.  
```

Nov  7 20:01:22 vivek-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  7 20:01:22 vivek-desktop dhclient: DHCPACK from 192.168.1.1
Nov  7 20:01:23 vivek-desktop dhclient: bound to 192.168.1.100 -- renewal in 288204 seconds.

```

---

