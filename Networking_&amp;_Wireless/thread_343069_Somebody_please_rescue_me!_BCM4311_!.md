---
title: "Somebody please rescue me! BCM4311 !"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by matt_risi on 2007-01-20
Alright guys.

I've been searching around these forums looking for a way to get my BCM4311 card working in ubuntu, so it can be of use to me, and so that I can get away from Windows for everyday use, which I regret to say I'm posting from now. I just can't get the darn thing to work, and I'm running to wits end with Windows. The other day all I wanted to do was retrieve a file from my xbox over the network, but that involved finding and downloading an FTP client, which proved to be either piracy, spyware, or just a general pain in the ***. I had the delusion that if I just went to the DOS prompt and types "sudo apt-get install gftp" that I'd be able to get what I wanted to do on MY COMPUTER done. ](*,) 

For the love of everything sacred, someone PLEASE give me some direction as to what I can do to get this thing working. I've tried the ubuntu support document regarding this, but at the stage where I need to cabextract, the prompt tells me it's unable to find the program I'm talking about, let alone install it.

I've also simply installed ndiswrapper, blacklisted bcm33xx and installed bcmwl5.inf as the driver, but it doesn't find the hardware in the network manager, and my wireless light remains off, even as the card is listed in lspci.

ANY other successful means of installing this card are welcome.

---

### Post by teaker1s on 2007-01-20
follow the guide in my signature to the letter and it will work:guitar:

I expect that either the driver is invalid
[COLOR="Red"]sudo ndiswrapper -l[/COLOR]

or ndiswrapper isn't running try this and does light come on
[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]

---

### Post by matt_risi on 2007-01-20
That's the guide that failed for me, and the light doesn't come on after sudo modprobe ndiswrapper. Can you think of anything else, I can't take this Windows crap much longer.

---

### Post by teaker1s on 2007-01-21
make sure switch is on

yes terminal
[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]
[COLOR="Red"]ndiswraper-l[/COLOR]

if it says the driver is invalid you will need one from your manufacturers cd, if it says fatal error then you will need to install  **ndiswrapper-utils-1.8**

---

### Post by matt_risi on 2007-01-21
"sudo modprobe ndiswrapper" goes fine.

"sudo ndiswrapper -l" lists the driver, says it's installed and fine, but doesn't say anything about the hardware being detected, which is my issue.

---

### Post by teaker1s on 2007-01-21
okay well of the top of my head the only idea's I have  and have experienced are:-

1)check if bios has any wireless choices-if it does they should be set so card has power and can be seen powered on
2)The driver doesn't work correctly and you will need another driver file-where did you get the current one
3)version of ndiswrapper you are using doesn't work with your hardware.



the most likely ones are numbers 1 and 2

---

### Post by matt_risi on 2007-01-21
Nothing in the bios about the adapter being powered on. Windows recognizes the adapter fine on boot and doesn't require any tweaking to activate, so it must be activated by default. I've used this driver on my last laptop (bcm4318 card), and used it again for this card (bcm4311) as instructed in the tutorial.

---

### Post by jmrichky on 2007-01-21
I tried several different guides, some of them twice.  I finally found this one:  [COLOR="Red"][http://www.ubuntuforums.org/showthread.php?t=340689]("http://www.ubuntuforums.org/showthread.php?t=340689")[/COLOR]
and it worked flawlessly.

Also, please post the output of [COLOR="Red"]dmesg[/COLOR].

---

### Post by teaker1s on 2007-01-21
sounds like bad driver file, ndiswrapper project has list of cards\chipsets and drivers that will work

---

### Post by haiku99 on 2007-01-21
> **matt_risi said:**
> Nothing in the bios about the adapter being powered on. Windows recognizes the adapter fine on boot and doesn't require any tweaking to activate, so it must be activated by default. I've used this driver on my last laptop (bcm4318 card), and used it again for this card (bcm4311) as instructed in the tutorial.


FWIW I got my BCM4311 working with Ndiswrapper and used drivers I copied from my XP partition...
and this howto   [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by matt_risi on 2007-01-21
Both of those guides are for cards that aren't mine.. should I still try them?

Later: I tried the guide from jmrichky, but it's still not detecting the hardware. It's listed in lspci and the driver installs fine, just no hardware detected.

---

### Post by matt_risi on 2007-01-21
dmesg output:

[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f670000 (usable)
[17179569.184000]  BIOS-e820: 000000001f670000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 502MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7d20
[17179569.184000] On node 0 totalpages: 128624
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124528 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f7c70
[17179569.184000] ACPI: RSDT (v001 HP     30BB     0x06040000  LTP 0x00000000) @ 0x1f67f1a2
[17179569.184000] ACPI: FADT (v001 HP     30BB     0x06040000 LOHR 0x0000005a) @ 0x1f686dfc
[17179569.184000] ACPI: MADT (v001 HP     30BB     0x06040000 LOHR 0x0000005a) @ 0x1f686e70
[17179569.184000] ACPI: HPET (v001 HP     30BB     0x06040000 LOHR 0x0000005a) @ 0x1f686ed8
[17179569.184000] ACPI: MCFG (v001 HP     30BB     0x06040000 LOHR 0x0000005a) @ 0x1f686f10
[17179569.184000] ACPI: BOOT (v001 HP     30BB     0x06040000  LTP 0x00000001) @ 0x1f686fd8
[17179569.184000] ACPI: MADT (v001 HP     30BB     0x06040000  LTP 0x00000000) @ 0x1f686f7e
[17179569.184000] ACPI: SSDT (v001  HP    30BB     0x00001000 INTL 0x20050624) @ 0x1f67f8bc
[17179569.184000] ACPI: SSDT (v001 HP     30BB     0x00003001 INTL 0x20050624) @ 0x1f67f6e0
[17179569.184000] ACPI: SSDT (v001 HP     30BB     0x00003000 INTL 0x20050624) @ 0x1f67f1ea
[17179569.184000] ACPI: DSDT (v001 HP     30BB     0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: 2 duplicate APIC table ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.184000] Memory: 500456k/514496k available (1910k kernel code, 13532k reserved, 1069k data, 308k init, 0k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xe0000000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1729.535 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3463.31 BogoMIPS (lpj=6926639)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 1024K
[17179569.268000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000140 0000c109 00000000 00000000
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] Freeing SMP alternatives: 16k freed
[17179569.284000] checking if image is initramfs... it is
[17179569.796000] Freeing initrd memory: 5321k freed
[17179569.796000] ACPI: Core revision 20060707
[17179569.796000] ACPI: Looking for DSDT ... not found!
[17179569.828000] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[17179569.828000] Total of 1 processors activated (3463.31 BogoMIPS).
[17179569.828000] ENABLING IO-APIC IRQs
[17179569.828000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179569.980000] Brought up 1 CPUs
[17179569.980000] migration_cost=0
[17179569.980000] NET: Registered protocol family 16
[17179569.980000] EISA bus registered
[17179569.980000] ACPI: bus type pci registered
[17179569.980000] PCI: Using MMCONFIG
[17179569.980000] Setting up standard PCI resources
[17179569.980000] ACPI: Interpreter enabled
[17179569.980000] ACPI: Using IOAPIC for interrupt routing
[17179569.984000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179569.984000] PCI: Probing PCI hardware (bus 00)
[17179569.984000] Boot video device is 0000:00:02.0
[17179569.984000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179569.984000] PCI: Transparent bridge - 0000:00:1e.0
[17179569.984000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179569.992000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179569.992000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179569.992000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179569.992000] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[17179569.996000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3)
[17179569.996000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[17179569.996000] ACPI: PCI Interrupt Link [LNKD] (IRQs *4)
[17179569.996000] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[17179569.996000] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[17179569.996000] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[17179569.996000] ACPI: PCI Interrupt Link [LNKH] (IRQs *7)
[17179569.996000] ACPI: Embedded Controller [EC0] (gpe 23) interrupt mode.
[17179569.996000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179569.996000] pnp: PnP ACPI init
[17179570.000000] pnp: PnP ACPI: found 10 devices
[17179570.000000] PnPBIOS: Disabled by ACPI PNP
[17179570.000000] PCI: Using ACPI for IRQ routing
[17179570.000000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.000000] pnp: 00:06: ioport range 0x6a0-0x6af has been reserved
[17179570.000000] pnp: 00:06: ioport range 0x6b0-0x6ff has been reserved
[17179570.000000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.000000] PCI: Bridge: 0000:00:1c.0
[17179570.000000]   IO window: 2000-2fff
[17179570.000000]   MEM window: d6000000-d7ffffff
[17179570.000000]   PREFETCH window: d2000000-d3ffffff
[17179570.000000] PCI: Bridge: 0000:00:1c.1
[17179570.000000]   IO window: 3000-3fff
[17179570.000000]   MEM window: d4000000-d5ffffff
[17179570.000000]   PREFETCH window: d0000000-d1ffffff
[17179570.000000] PCI: Bridge: 0000:00:1e.0
[17179570.000000]   IO window: 4000-4fff
[17179570.000000]   MEM window: d8000000-d80fffff
[17179570.000000]   PREFETCH window: disabled.
[17179570.000000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.000000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.000000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.000000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.000000] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[17179570.000000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.000000] NET: Registered protocol family 2
[17179570.028000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.028000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.028000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.028000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.028000] TCP reno registered
[17179570.028000] Simple Boot Flag at 0x35 set to 0x1
[17179570.028000] audit: initializing netlink socket (disabled)
[17179570.028000] audit(1169386771.028:1): initialized
[17179570.028000] VFS: Disk quotas dquot_6.5.1
[17179570.028000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.028000] Initializing Cryptographic API
[17179570.028000] io scheduler noop registered
[17179570.028000] io scheduler anticipatory registered
[17179570.028000] io scheduler deadline registered
[17179570.028000] io scheduler cfq registered (default)
[17179570.028000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.028000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.028000] assign_interrupt_mode Found MSI capability
[17179570.028000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.028000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.028000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179570.028000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.028000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.028000] assign_interrupt_mode Found MSI capability
[17179570.028000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179570.028000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179570.028000] Allocate Port Service[0000:00:1c.1:pcie03]
[17179570.028000] isapnp: Scanning for PnP cards...
[17179570.384000] isapnp: No Plug & Play device found
[17179570.404000] Real Time Clock Driver v1.12ac
[17179570.404000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.404000] mice: PS/2 mouse device common for all mice
[17179570.404000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.404000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.404000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.404000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.416000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.420000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.424000] EISA: Probing bus 0 at eisa.0
[17179570.424000] Cannot allocate resource for EISA slot 1
[17179570.424000] Cannot allocate resource for EISA slot 2
[17179570.424000] Cannot allocate resource for EISA slot 3
[17179570.424000] Cannot allocate resource for EISA slot 4
[17179570.424000] EISA: Detected 0 cards.
[17179570.424000] TCP bic registered
[17179570.424000] NET: Registered protocol family 1
[17179570.424000] NET: Registered protocol family 8
[17179570.424000] NET: Registered protocol family 20
[17179570.424000] Using IPI No-Shortcut mode
[17179570.424000] ACPI: (supports S0 S3 S4 S5)
[17179570.424000] Freeing unused kernel memory: 308k freed
[17179570.444000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.552000] Capability LSM initialized
[17179571.580000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179571.580000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179571.580000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.580000] ACPI: Getting cpuindex for acpiid 0x1
[17179571.584000] ACPI: Thermal Zone [THR1] (39 C)
[17179571.864000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179571.864000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 209
[17179571.864000] ICH7: chipset revision 2
[17179571.864000] ICH7: not 100% native mode: will probe irqs later
[17179571.864000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179571.864000] Probing IDE interface ide0...
[17179572.268000] hda: PHILIPS DVD-RAM SDVD8821, ATAPI CD/DVD-ROM drive
[17179572.940000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179572.952000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[17179572.952000] Uniform CD-ROM driver Revision: 3.20
[17179573.032000] SCSI subsystem initialized
[17179573.032000] libata version 1.20 loaded.
[17179573.036000] ahci 0000:00:1f.2: version 1.2
[17179573.036000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 217
[17179578.856000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179578.856000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[17179578.856000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[17179578.856000] ata1: SATA max UDMA/133 cmd 0xE0046500 ctl 0x0 bmdma 0x0 irq 225
[17179578.856000] ata2: SATA max UDMA/133 cmd 0xE0046580 ctl 0x0 bmdma 0x0 irq 225
[17179578.856000] ata3: SATA max UDMA/133 cmd 0xE0046600 ctl 0x0 bmdma 0x0 irq 225
[17179578.856000] ata4: SATA max UDMA/133 cmd 0xE0046680 ctl 0x0 bmdma 0x0 irq 225
[17179579.232000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179579.232000] ata1: dev 0 cfg 49:2f00 82:306b 83:7c09 84:6003 85:3069 86:3c09 87:6003 88:203f
[17179579.232000] ata1: dev 0 ATA-7, max UDMA/100, 195371568 sectors: LBA48
[17179579.232000] ata1: dev 0 configured for UDMA/100
[17179579.232000] scsi0 : ahci
[17179579.436000] ata2: SATA link down (SStatus 0)
[17179579.436000] scsi1 : ahci
[17179579.640000] ata3: SATA link down (SStatus 0)
[17179579.640000] scsi2 : ahci
[17179579.844000] ata4: SATA link down (SStatus 0)
[17179579.844000] scsi3 : ahci
[17179579.844000]   Vendor: ATA       Model: ST9100828AS       Rev: 3.BH
[17179579.844000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179579.848000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179579.848000] sda: Write Protect is off
[17179579.848000] sda: Mode Sense: 00 3a 00 00
[17179579.848000] SCSI device sda: drive cache: write back
[17179579.848000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179579.848000] sda: Write Protect is off
[17179579.848000] sda: Mode Sense: 00 3a 00 00
[17179579.848000] SCSI device sda: drive cache: write back
[17179579.848000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[17179579.904000] sd 0:0:0:0: Attached scsi disk sda
[17179580.148000] Probing IDE interface ide1...
[17179580.180000] usbcore: registered new driver usbfs
[17179580.180000] usbcore: registered new driver hub
[17179580.180000] USB Universal Host Controller Interface driver v3.0
[17179580.180000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179580.180000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179580.180000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179580.180000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179580.180000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x00001820
[17179580.180000] usb usb1: configuration #1 chosen from 1 choice
[17179580.180000] hub 1-0:1.0: USB hub found
[17179580.180000] hub 1-0:1.0: 2 ports detected
[17179580.284000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[17179580.284000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179580.284000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179580.284000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179580.284000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x00001840
[17179580.284000] usb usb2: configuration #1 chosen from 1 choice
[17179580.284000] hub 2-0:1.0: USB hub found
[17179580.284000] hub 2-0:1.0: 2 ports detected
[17179580.388000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179580.388000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179580.388000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179580.388000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179580.388000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x00001860
[17179580.388000] usb usb3: configuration #1 chosen from 1 choice
[17179580.388000] hub 3-0:1.0: USB hub found
[17179580.388000] hub 3-0:1.0: 2 ports detected
[17179580.492000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179580.492000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179580.492000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179580.492000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179580.492000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001880
[17179580.492000] usb usb4: configuration #1 chosen from 1 choice
[17179580.492000] hub 4-0:1.0: USB hub found
[17179580.492000] hub 4-0:1.0: 2 ports detected
[17179580.596000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179580.596000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179580.596000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179580.596000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179580.596000] ehci_hcd 0000:00:1d.7: debug port 1
[17179580.596000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179580.596000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xd8444000
[17179580.600000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.600000] usb usb5: configuration #1 chosen from 1 choice
[17179580.600000] hub 5-0:1.0: USB hub found
[17179580.600000] hub 5-0:1.0: 8 ports detected
[17179580.736000] Attempting manual resume
[17179580.752000] kjournald starting.  Commit interval 5 seconds
[17179580.752000] EXT3-fs: mounted filesystem with ordered data mode.
[17179581.008000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[17179581.140000] usb 5-3: configuration #1 chosen from 1 choice
[17179591.004000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.056000] agpgart: Detected an Intel 945GM Chipset.
[17179591.056000] agpgart: Detected 7932K stolen memory.
[17179591.072000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179591.092000] hw_random hardware driver 1.0.0 loaded
[17179591.140000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.644000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179591.644000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179591.644000] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 20 (level, low) -> IRQ 50
[17179591.644000] PCI: Setting latency timer of device 0000:05:08.0 to 64
[17179591.676000] e100: eth0: e100_probe: addr 0xd8000000, irq 50, MAC addr 00:16:36:BC:B7:8E
[17179592.016000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179592.068000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[17179592.156000] usbcore: registered new driver libusual
[17179592.304000] Initializing USB Mass Storage driver...
[17179592.304000] scsi4 : SCSI emulation for USB Mass Storage devices
[17179592.304000] usbcore: registered new driver usb-storage
[17179592.304000] USB Mass Storage support registered.
[17179592.308000] usb-storage: device found at 2
[17179592.308000] usb-storage: waiting for device to settle before scanning
[17179592.308000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 58
[17179592.308000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179592.472000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[17179592.532000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179592.552000] ts: Compaq touchscreen protocol output
[17179593.136000] lp: driver loaded but no devices found
[17179593.156000] Adding 522072k swap on /dev/disk/by-uuid/3e5c7cdb-848a-4698-b62f-00bb8647ca29.  Priority:-1 extents:1 across:522072k
[17179593.164000] NET: Registered protocol family 17
[17179593.212000] EXT3 FS on sda2, internal journal
[17179594.224000] ACPI: AC Adapter [ACAD] (off-line)
[17179594.320000] ACPI: Battery Slot [BAT0] (battery present)
[17179594.332000] ACPI: Power Button (FF) [PWRF]
[17179594.332000] ACPI: Power Button (CM) [PWRB]
[17179594.332000] ACPI: Sleep Button (CM) [SLPB]
[17179594.332000] ACPI: Lid Switch [LID]
[17179594.452000] ibm_acpi: ec object not found
[17179594.484000] pcc_acpi: loading...
[17179594.536000] wmi_add device=df60dc00
[17179594.536000] calling WQBA
[17179594.580000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179594.580000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179597.072000] [drm] Initialized drm 1.0.1 20051102
[17179597.076000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179597.080000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179597.308000] usb-storage: device scan complete
[17179597.312000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17179597.312000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.348000] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[17179597.356000] sdb: Write Protect is off
[17179597.356000] sdb: Mode Sense: 64 00 00 08
[17179597.356000] sdb: assuming drive cache: write through
[17179597.360000] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[17179597.360000] sdb: Write Protect is off
[17179597.360000] sdb: Mode Sense: 64 00 00 08
[17179597.360000] sdb: assuming drive cache: write through
[17179597.360000]  sdb: [mac] sdb1 sdb2 sdb3
[17179597.720000] sd 4:0:0:0: Attached scsi removable disk sdb
[17179597.720000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17179598.428000] apm: BIOS not found.
[17179601.992000] Bluetooth: Core ver 2.8
[17179601.992000] NET: Registered protocol family 31
[17179601.992000] Bluetooth: HCI device and connection manager initialized
[17179601.992000] Bluetooth: HCI socket layer initialized
[17179602.008000] Bluetooth: L2CAP ver 2.8
[17179602.008000] Bluetooth: L2CAP socket layer initialized
[17179602.024000] Bluetooth: RFCOMM socket layer initialized
[17179602.024000] Bluetooth: RFCOMM TTY layer initialized
[17179602.024000] Bluetooth: RFCOMM ver 1.7
[17179606.392000] NET: Registered protocol family 10
[17179606.392000] lo: Disabled Privacy Extensions
[17179606.392000] IPv6 over IPv4 tunneling driver
[17179609.644000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[17179616.688000] eth1: no IPv6 routers present
[17179692.844000] usb 5-3: USB disconnect, address 2
[17179695.352000] usb 5-3: new high speed USB device using ehci_hcd and address 3
[17179695.484000] usb 5-3: configuration #1 chosen from 1 choice
[17179695.484000] scsi5 : SCSI emulation for USB Mass Storage devices
[17179695.484000] usb-storage: device found at 3
[17179695.484000] usb-storage: waiting for device to settle before scanning
[17179700.484000] usb-storage: device scan complete
[17179700.484000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17179700.484000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179700.484000] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[17179700.484000] sdb: Write Protect is off
[17179700.484000] sdb: Mode Sense: 64 00 00 08
[17179700.484000] sdb: assuming drive cache: write through
[17179700.488000] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[17179700.488000] sdb: Write Protect is off
[17179700.488000] sdb: Mode Sense: 64 00 00 08
[17179700.488000] sdb: assuming drive cache: write through
[17179700.488000]  sdb: [mac] sdb1 sdb2 sdb3
[17179700.564000] sd 5:0:0:0: Attached scsi removable disk sdb
[17179700.564000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[17179701.068000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[17180091.592000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180091.788000] ISO 9660 Extensions: RRIP_1991A
[17180404.136000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180404.176000] ISO 9660 Extensions: RRIP_1991A
[17180429.544000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180501.260000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180501.264000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[17180501.264000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17180511.644000] eth1: no IPv6 routers present

Sorry, tried to put it as an attachment but it was an invalid file for some reason.

---

### Post by matt_risi on 2007-01-22
Bump!

---

### Post by Kobalt on 2007-01-25
Hello,

I have a Broadcom 4311 on a HP laptop and I got my wifi to work with Ndiswrapper pretty easily... I described it [here]("http://www.ubuntuforums.org/showthread.php?t=346083"), I hope this will help you out. 

Cheerio !

---

### Post by teaker1s on 2007-01-25
have you blacklisted native driver? as it sounds like you haven't

---

### Post by discord on 2007-01-25
i got it working ages ago...

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

### Post by matt_risi on 2007-01-27
Superbe! Thank you all, working nice. Now all I have to do is figure out how to get the laptop to smoothly transfer from one WEP network to the next without waiting 2 minutes for it to boot. Thanks for all the help!

---

### Post by haiku99 on 2007-01-27
> **matt_risi said:**
> Superbe! Thank you all, working nice. Now all I have to do is figure out how to get the laptop to smoothly transfer from one WEP network to the next without waiting 2 minutes for it to boot. Thanks for all the help!

 I've gone to system>administrtion>networking, entered new id and key under properties,  then unchecked and rechecked the connection, this restarted it  (using Edgy)

---

### Post by teaker1s on 2007-01-28
or use network-manager-gnome

or 

wifi radar

---

### Post by vigyani on 2007-02-06
Try using network manager

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

