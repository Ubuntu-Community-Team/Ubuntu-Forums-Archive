---
title: "Network transmit slow"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by Trellmor on 2006-12-23
Hello!

I'm using Ubuntu 6.06 server on a Dell GX110 box. The nic is a 3COM  3c905C-TX/TX-M [Tornado].

Receiving speed seems ok, but sending is somewhere around 1 or 2% of the 100MB.

I have no idea how to speed it up, I tried forcing 100MBit Full duplex mode, autonegotiation on/off etc, no help :/

---

### Post by rlozano on 2006-12-23
are you talking of wired speed over your LAN or speed over the internet? to start with, you may want to diable ipv6. there have been alot of post about disabling it and get improved performance.

---

### Post by Trellmor on 2006-12-23
Over lan, tried to disable ipv6 already, no help

---

### Post by netztier on 2006-12-23
> **Trellmor said:**
>  I have no idea how to speed it up, I tried forcing 100MBit Full duplex mode, autonegotiation on/off etc, no help :/

What does [FONT="Courier New"]**dmesg | grep eth**[/FONT] tell you about the speed/link settings that the driver has reported?

Don't set anything to fixed duplex setting (half or full) unless you can do the same ting to the device at the other end of your cable. Most combinations of configuring only one of the involved devices will result in a duplex mismatch. A duplex mismatch typically has the symptoms you describe.

If you have a "normal" unmanaged switch (or a typical 4-port switch intgrated in your broadband/wireless router), it most probably won't allow for duplex mode configuration. So you'll then be forced to use "auto" anyway.


best regards

Marc


[COLOR="Red"][B]Ceterum censeo: leave your Ethernet NIC's speed and duplex settings on "auto", unless you know exactly what you are doing!
[/B][/COLOR]

---

### Post by Trellmor on 2006-12-23
IF I do dmsg | grep eth0 i get no output at all.

only relevant output seems to be
> 42949390.920000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[42949390.920000] 0000:01:0c.0: 3Com PCI 3c905C Tornado at d091cc00. Vers LK1.1.19


Full dmsg output
> [42949372.960000] Linux version 2.6.15-27-server (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Fri Dec 8 18:43:54 UTC 2006
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[42949372.960000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 000000000feac000 (usable)
[42949372.960000]  BIOS-e820: 000000000feac000 - 0000000010000000 (reserved)
[42949372.960000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[42949372.960000] 0MB HIGHMEM available.
[42949372.960000] 254MB LOWMEM available.
[42949372.960000] On node 0 totalpages: 65196
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   DMA32 zone: 0 pages, LIFO batch:0
[42949372.960000]   Normal zone: 61100 pages, LIFO batch:15
[42949372.960000]   HighMem zone: 0 pages, LIFO batch:0
[42949372.960000] DMI 2.3 present.
[42949372.960000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd790
[42949372.960000] ACPI: RSDT (v001 DELL    GX110   0x00000007 ASL  0x00000061) @ 0x000fd7a4
[42949372.960000] ACPI: FADT (v001 DELL    GX110   0x00000007 ASL  0x00000061) @ 0x000fd7cc
[42949372.960000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000b) @ 0x00000000
[42949372.960000] ACPI: PM-Timer IO Port: 0x808
[42949372.960000] Allocating PCI resources starting at 20000000 (gap: 10000000:efb00000)
[42949372.960000] Built 1 zonelists
[42949372.960000] Kernel command line: root=/dev/hda1 ro quiet splash
[42949372.960000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[42949372.960000] mapped APIC to ffffd000 (0123f000)
[42949372.960000] Initializing CPU#0
[42949372.960000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[42949372.960000] Detected 498.496 MHz processor.
[42949372.960000] Using pmtmr for high-res timesource
[42949372.960000] Console: colour VGA+ 80x25
[42949372.970000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[42949372.970000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[42949373.010000] Memory: 247396k/260784k available (2087k kernel code, 12796k reserved, 620k data, 332k init, 0k highmem)
[42949373.010000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[42949373.160000] Calibrating delay using timer specific routine.. 997.99 BogoMIPS (lpj=4989954)
[42949373.160000] Security Framework v1.0.0 initialized
[42949373.160000] SELinux:  Disabled at boot.
[42949373.160000] Mount-cache hash table entries: 512
[42949373.160000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[42949373.160000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[42949373.160000] CPU: L1 I cache: 16K, L1 D cache: 16K
[42949373.160000] CPU: L2 cache: 512K
[42949373.160000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[42949373.160000] mtrr: v2.0 (20020519)
[42949373.160000] Enabling fast FPU save and restore... done.
[42949373.160000] Enabling unmasked SIMD FPU exception support... done.
[42949373.160000] Checking 'hlt' instruction... OK.
[42949373.200000] checking if image is initramfs... it is
[42949375.390000] Freeing initrd memory: 6789k freed
[42949375.430000] ACPI: Looking for DSDT ... not found!
[42949375.450000] ACPI: setting ELCR to 0200 (from 0e20)
[42949375.450000] CPU0: Intel Pentium III (Katmai) stepping 03
[42949375.450000] SMP motherboard not detected.
[42949375.450000] Local APIC not detected. Using dummy APIC emulation.
[42949375.450000] Brought up 1 CPUs
[42949375.450000] NET: Registered protocol family 16
[42949375.450000] EISA bus registered
[42949375.450000] ACPI: bus type pci registered
[42949375.470000] PCI: PCI BIOS revision 2.10 entry at 0xfc0be, last bus=1
[42949375.470000] PCI: Using configuration type 1
[42949375.470000] ACPI: Subsystem revision 20051216
[42949375.480000] ACPI: Interpreter enabled
[42949375.480000] ACPI: Using PIC for interrupt routing
[42949375.480000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949375.480000] PCI: Probing PCI hardware (bus 00)
[42949375.480000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[42949375.490000] Boot video device is 0000:00:01.0
[42949375.490000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[42949375.490000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[42949375.490000] PCI: Transparent bridge - 0000:00:1e.0
[42949375.490000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949375.490000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[42949375.510000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[42949375.510000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[42949375.510000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[42949375.510000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[42949375.510000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949375.510000] pnp: PnP ACPI init
[42949375.530000] pnp: PnP ACPI: found 12 devices
[42949375.530000] PnPBIOS: Disabled by ACPI PNP
[42949375.530000] PCI: Using ACPI for IRQ routing
[42949375.530000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[42949375.540000] pnp: 00:0b: ioport range 0x800-0x85f could not be reserved
[42949375.540000] pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
[42949375.540000] pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
[42949375.540000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[42949375.540000] PCI: Bridge: 0000:00:1e.0
[42949375.540000]   IO window: e000-efff
[42949375.540000]   MEM window: fd000000-feffffff
[42949375.540000]   PREFETCH window: 20000000-200fffff
[42949375.540000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[42949375.550000] audit: initializing netlink socket (disabled)
[42949375.550000] audit(1166881664.540:1): initialized
[42949375.550000] VFS: Disk quotas dquot_6.5.1
[42949375.550000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949375.550000] Initializing Cryptographic API
[42949375.550000] io scheduler noop registered
[42949375.550000] io scheduler anticipatory registered
[42949375.550000] io scheduler deadline registered
[42949375.550000] io scheduler cfq registered
[42949375.550000] isapnp: Scanning for PnP cards...
[42949375.910000] isapnp: No Plug & Play device found
[42949376.000000] Real Time Clock Driver v1.12
[42949376.000000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[42949377.020000] serio: i8042 KBD port at 0x60,0x64 irq 1
[42949377.020000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[42949377.040000] **** SET: Misaligned resource pointer: cfdc4222 Type 00 Len 42
[42949377.040000] pnp: Device 00:08 activated.
[42949377.040000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949377.040000] **** SET: Misaligned resource pointer: cfdc4222 Type 00 Len 42
[42949377.050000] pnp: Device 00:09 activated.
[42949377.050000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[42949377.050000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[42949377.050000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949377.050000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[42949377.050000] mice: PS/2 mouse device common for all mice
[42949377.050000] EISA: Probing bus 0 at eisa.0
[42949377.050000] EISA: Detected 0 cards.
[42949377.050000] NET: Registered protocol family 2
[42949377.140000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[42949377.140000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[42949377.140000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[42949377.140000] TCP: Hash tables configured (established 8192 bind 8192)
[42949377.140000] TCP reno registered
[42949377.140000] TCP bic registered
[42949377.140000] NET: Registered protocol family 1
[42949377.140000] NET: Registered protocol family 8
[42949377.140000] NET: Registered protocol family 20
[42949377.140000] Using IPI No-Shortcut mode
[42949377.140000] ACPI wakeup devices: 
[42949377.140000] PCI0 USB0 PCI1  KBD 
[42949377.140000] ACPI: (supports S0 S1 S4 S5)
[42949377.140000] Freeing unused kernel memory: 332k freed
[42949377.340000] vga16fb: initializing
[42949377.340000] vga16fb: mapped to 0xc00a0000
[42949377.450000] Console: switching to colour frame buffer device 80x25
[42949377.450000] fb0: VGA16 VGA frame buffer device
[42949377.490000] Capability LSM initialized
[42949379.460000] ICH: IDE controller at PCI slot 0000:00:1f.1
[42949379.460000] ICH: chipset revision 2
[42949379.460000] ICH: not 100% native mode: will probe irqs later
[42949379.460000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[42949379.460000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[42949379.460000] Probing IDE interface ide0...
[42949379.770000] hda: WDC WD800BB-00JHC0, ATA DISK drive
[42949380.490000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949380.490000] Probing IDE interface ide1...
[42949380.910000] hdc: SAMSUNG CD-ROM SN-124, ATAPI CD/DVD-ROM drive
[42949381.630000] ide1 at 0x170-0x177,0x376 on irq 15
[42949381.670000] hda: max request size: 128KiB
[42949381.680000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(66)
[42949381.690000] hda: cache flushes supported
[42949381.690000]  hda: hda1 hda2 < hda5 >
[42949381.730000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
[42949381.730000] Uniform CD-ROM driver Revision: 3.20
[42949382.110000] usbcore: registered new driver usbfs
[42949382.110000] usbcore: registered new driver hub
[42949382.130000] USB Universal Host Controller Interface driver v2.3
[42949382.130000] **** SET: Misaligned resource pointer: cf9aa6e2 Type 07 Len 0
[42949382.130000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[42949382.130000] PCI: setting IRQ 11 as level-triggered
[42949382.130000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[42949382.130000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[42949382.130000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[42949382.130000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[42949382.130000] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[42949382.130000] hub 1-0:1.0: USB hub found
[42949382.130000] hub 1-0:1.0: 2 ports detected
[42949382.390000] Attempting manual resume
[42949382.440000] kjournald starting.  Commit interval 5 seconds
[42949382.440000] EXT3-fs: mounted filesystem with ordered data mode.
[42949388.320000] Linux agpgart interface v0.101 (c) Dave Jones
[42949388.340000] agpgart: Detected an Intel i810 E Chipset.
[42949388.340000] agpgart: detected 4MB dedicated video ram.
[42949388.350000] agpgart: AGP aperture is 64M @ 0xf8000000
[42949389.710000] input: PC Speaker as /class/input/input0
[42949389.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949389.730000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949389.810000] Floppy drive(s): fd0 is 1.44M
[42949389.830000] FDC 0 is a National Semiconductor PC87306
[42949389.830000] hw_random hardware driver 1.0.0 loaded
[42949390.050000] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[42949390.470000] parport: PnPBIOS parport detected.
[42949390.470000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[42949390.920000] **** SET: Misaligned resource pointer: cecddf22 Type 07 Len 0
[42949390.920000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[42949390.920000] PCI: setting IRQ 5 as level-triggered
[42949390.920000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[42949390.920000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[42949390.920000] 0000:01:0c.0: 3Com PCI 3c905C Tornado at d091cc00. Vers LK1.1.19
[42949391.210000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[42949391.800000] lp0: using parport0 (interrupt-driven).
[42949392.100000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[42949392.210000] EXT3 FS on hda1, internal journal
[42949392.720000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949392.720000] md: bitmap version 4.39
[42949393.520000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[42949394.460000] cdrom: open failed.
[42950486.960000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[42951545.020000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[42951818.150000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[42952567.970000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[42953266.440000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5


It's a umanaged switch inbetween (Cheap 5 port D-Link).

---

### Post by netztier on 2006-12-23
> **Trellmor said:**
> 
It's a umanaged switch inbetween (Cheap 5 port D-Link).

Ok,  so you won't be able to change duplex settings on it. That makes it "all autoduplex" then.

Sorry for my error in assuming that this driver would output to dmesg. I have the same one on my system (Dapper),  too:

```
marc@blaze:~$ **dmesg | grep 3c**
[42949397.410000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[42949397.410000] 0000:00:0a.0: 3Com PCI 3c905C Tornado at e09b6000. Vers LK1.1.19
marc@blaze:~$ **uname -a**
Linux blaze 2.6.15-27-server #1 SMP Sat Sep 16 02:57:21 UTC 2006 i686 GNU/Linux
marc@blaze:~$ **uptime**
 16:21:51 up 75 days,  4:37,  1 user,  load average: 0.00, 0.00, 0.00

```


Install [FONT="Courier New"]**ethtool**[/FONT] and/or [FONT="Courier New"]**mii-diag**[/FONT] with [FONT="Courier New"]**mii-tool**[/FONT]. They have to be run from console with **sudo**.:

```
marc@blaze:~$ **sudo mii-diag**
Using the default interface 'eth0'.
Basic registers of MII PHY #24:  3000 782d 0041 6800 05e1 45e1 0007 2801.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

```


```
marc@blaze:~$ **sudo ethtool eth0**
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes
```


I left everyting to "auto", it's connected to a cheap Linksys SD205 5-Port 10/100Mbps switch - full duplex and everything ok.

best regards

Marc

---

### Post by Trellmor on 2006-12-23
As soon as i turn autoneg on, the speed goes to 10MBit Half Duplex, since for some reason my switch don't send autoneg info. So my recive speed drops to 10MBbit.

But my send speed is still to low, even too low for a 10Mbit connection.

> daniel@seron:~$ sudo mii-diag
Using the default interface 'eth0'.
Basic registers of MII PHY #24:  3000 780d 0040 6177 0501 0000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner does not do autonegotiation, and this transceiver type
  does not report the sensed link speed.
   End of basic transceiver information.


> daniel@seron:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes


---

### Post by netztier on 2006-12-23
> **Trellmor said:**
> As soon as i turn autoneg on, the speed goes to 10MBit Half Duplex, since for some reason my switch don't send autoneg info. So my recive speed drops to 10MBbit.

Since 10Mbit and 100Mbit use different electrical encoding (10Mbit uses Manchester Code, 100Mbit uses MLT-3), 10/100 detection is much less of a problem that half/full-duplex autonegotiation.

Looking at the output of the commands, I see that your device advertises 100-Full as it's only capability. How did you achieve that? Is that done by module parameters? I suggest letting it advertise all four modes - making it completely "auto".

If a device does not hear any autonegotiation signal from it's link partner, it has to default to half duplex. According to the output of mii-diag and ethtool, it is doing exactly that.
On the other hand, if the switch at the other end of the cable misses your 100baseT-full advertisment, it will fall back to half duplex, and the mismatch is there again.


> **Trellmor said:**
> But my send speed is still to low, even too low for a 10Mbit connection.

Then you'll have to check the cabling: 
[LIST]
[*]Are other systems connected to the same switch suffering from the same? 
[*]Have you tried swapping cables around to see if the problem migrates with the cable?
[*]Is the cable itself ok? 
[*]All wires needed (1+2, 3+6) connected and twisted as the proper pairs? 
[*]Does the twisting of the wire pairs stop only at very short distance from the plug? (this distance being too long occurs quite often on self-made cables)
[*]How long is the cable? Is it unshielded and runs through electrically noisy environment, such as large electric motors or the like?
[/LIST]

best regards

Marc

---

### Post by Trellmor on 2006-12-23
> **netztier said:**
> Looking at the output of the commands, I see that your device advertises 100-Full as it's only capability. How did you achieve that? Is that done by module parameters? I suggest letting it advertise all four modes - making it completely "auto".
Tried that, no change, still on 10baseT-HD :/

> 
Then you'll have to check the cabling: 
[LIST]
[*]Are other systems connected to the same switch suffering from the same? 
[/LIST]

Nope, every other device i have or had connected worked fine.
> 
[LIST]
[*]Have you tried swapping cables around to see if the problem migrates with the cable?
[/LIST]

I used different cables, I had the same prolbem with all cables.
> 
[LIST]
[*]Is the cable itself ok? 
[/LIST]

Yeah, I used that cables for other devices, and it worked fine.
> 
[LIST]
[*]All wires needed (1+2, 3+6) connected and twisted as the proper pairs? 
[/LIST]

Guess so, the cables are from different vendors.
> 
[LIST]
[*]Does the twisting of the wire pairs stop only at very short distance from the plug? (this distance being too long occurs quite often on self-made cables)
[/LIST]

They are not self made.
> 
[LIST]
[*]How long is the cable? Is it unshielded and runs through electrically noisy environment, such as large electric motors or the like?
[/LIST]

About 1.5m, I'm sitting right next to the linux box


Edit: Oh yeah: Incoming rate is about 5Mbits/s at the moment, but outgoing is only about 1 MBits/s at the moment

---

### Post by Trellmor on 2006-12-23
Bit longer output from mii-diag

> daniel@seron:~$ sudo mii-diag -v
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 24 (BMCR 0x3000).
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x7809 ... 780d.
   Link status: previously broken, but now reestablished.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Your link partner does not do autonegotiation, and this transceiver type
  does not report the sensed link speed.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #24 transceiver registers:
   3000 780d 0040 6177 05e1 0000 0000 0000
   0000 0000 0000 0000 0000 0000 0000 0000
   1000 4321 0000 0004 0000 0126 0200 0000
   0037 000c 0f00 ff40 0027 0000 0000 000b.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x780d ... 780d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Vendor ID is 00:10:18:--:--:--, model 23 rev. 7.
   No specific information is known about this transceiver type.
 I'm advertising 05e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 0000:.
   Negotiation did not complete.


---

### Post by Trellmor on 2006-12-24
/bump

---

### Post by netztier on 2006-12-25
> **Trellmor said:**
> 
```
Your link partner does not do autonegotiation, and this transceiver type
does not report the sensed link speed.
[...]
**[COLOR="Red"]Link partner capability is 0000:[/COLOR]**.
Negotiation did not complete.

```

Ouh - there we have it. 
If mii-diag's assumptions are correct, then the switch port this system is connected to does not advertise it's capabilites, and therefore, autonegotiation fails. The NIC then has to default to half duplex - and who knows what state the switchport actually is in...

[LIST]
[*]What happens if you connect this system to another port on the same switch?
[*]It might also help to change/swap the entire switch altogether?
[/LIST]

This reminds me of the days when the 4-port switch in my Linksys DSL router (WAG-54G) died. My system (workstation) was connected to a Linksys switch i still have today, while the file server **blaze** (see below) was connected to a switchport on the Linksys DSL router, next to the downlink to the switch. 

Although all links were operating at 100Mbps full duplex, transfer rates dropped to less than 50kBytes/s when they went through the router's integrated switch. As soon as all systems were connected to the separate switch, high transfer rates came back instantly. It took quite a while to find the culprit...

I suggest you take a closer look on that switch.

Here's the detailed output of mii-diag -v:
```

marc@blaze:~$ **sudo mii-diag -v**
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 24 (BMCR 0x3000).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
[COLOR="DarkGreen"] Your link partner advertised 45e1[/COLOR]: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
 MII PHY #24 transceiver registers:
   3000 782d 0041 6800 05e1 45e1 0007 2801
   0000 0000 0000 0000 0000 0000 0000 0000
   0618 c7b1 0030 4001 40c8 a000 0000 0000
   d300 0220 8084 9119 0065 1aab 7fff 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x782d ... 782d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Vendor ID is 00:10:5a:--:--:--, model 0 rev. 0.
   No specific information is known about this transceiver type.
[COLOR="DarkGreen"]** I'm advertising 05e1:**[/COLOR] Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
[COLOR="DarkGreen"]** Link partner capability is 45e1:**[/COLOR] Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation  completed.
```

best regards

Marc

---

### Post by Trellmor on 2006-12-25
Both my laptop and my desktop work fine with that switch, both on full transfer rate. Guess I'll try to use another switch to figure out if it helps.

Thanks for the help so far, I'll let you know if changing switches helped.

Yours truly
Daniel

---

### Post by Trellmor on 2007-01-05
I finally got time to connect the box to another switch, but the problem remains. I don't get a autoneg signal.

Since I'm tired of trying to get this onboard chip to work I decided to just use another NIC. It's a via-rhine III chipset on that NIC and it's working fine.

Thanks for the help

---

