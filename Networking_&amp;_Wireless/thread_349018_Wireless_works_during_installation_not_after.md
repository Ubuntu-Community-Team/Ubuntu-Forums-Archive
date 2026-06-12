---
title: "Wireless works during installation not after"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by job2600 on 2007-01-29
Installed Ubuntu 6.10 on a FUJITSU LifeBook B Series.

During installation the wireless card was detected and I was able to configure it with WEP and get an ip address via DHCP. However, once the install finished I cannot get it to work for the life of me.

The LifeBook has built-in wireless using the Prism 2.5 Wavelan chipset.

Here's what I am getting when trying to interact with the device:

#iwconfig wlan0
```
wlan0     no wireless extensions.
```

#iwconfig wlan0 ESSID "LIEBE"
```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.

```

#ifconfig wlan0 up
```
SIOCSIFFLAGS: No such device
```

For some reason the output of lshw shows the device is disabled
```
*-network DISABLED
             description: Ethernet interface
             product: Prism 2.5 Wavelan chipset
             vendor: Intersil Corporation
             physical id: 12
             bus info: pci@00:12.0
             logical name: wlan0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list ethernet physical
             configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 link=no multicast=yes
             resources: iomemory:e8010000-e8010fff irq:9
```

Output of dmesg:

```
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ffe0000 (usable)
[17179569.184000]  BIOS-e820: 000000000ffe0000 - 000000000ffefc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ffefc00 - 000000000fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fff2000 (reserved)
[17179569.184000]  BIOS-e820: 000000000fff2000 - 0000000010000000 (usable)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 256MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65536
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61440 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 FUJ                                   ) @ 0x000f6350
[17179569.184000] ACPI: RSDT (v001 FUJ    QUILT6   0x01060000 FUJ  0x00001000) @ 0x0ffec377
[17179569.184000] ACPI: FADT (v001 FUJ    QUILT6   0x01060000 FUJ  0x00001000) @ 0x0ffefb8c
[17179569.184000] ACPI: DSDT (v001 FUJ    QUILT6   0x01060000 MSFT 0x01000007) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xff08
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0120a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 895.697 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.108000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.108000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.132000] Memory: 250088k/262144k available (1910k kernel code, 11364k reserved, 1069k data, 308k init, 0k highmem)
[17179571.132000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.212000] Calibrating delay using timer specific routine.. 1792.81 BogoMIPS (lpj=3585639)
[17179571.212000] Security Framework v1.0.0 initialized
[17179571.212000] SELinux:  Disabled at boot.
[17179571.212000] Mount-cache hash table entries: 512
[17179571.212000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.212000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.212000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179571.212000] CPU: L2 cache: 512K
[17179571.212000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179571.212000] Checking 'hlt' instruction... OK.
[17179571.228000] SMP alternatives: switching to UP code
[17179571.228000] Freeing SMP alternatives: 16k freed
[17179571.228000] checking if image is initramfs... it is
[17179572.284000] Freeing initrd memory: 5325k freed
[17179572.284000] ACPI: Core revision 20060707
[17179572.284000] ACPI: Looking for DSDT ... not found!
[17179572.288000] ACPI: setting ELCR to 0200 (from 8200)
[17179572.296000] CPU0: Intel Mobile Intel(R) Pentium(R) III CPU - M   900MHz stepping 04
[17179572.296000] SMP motherboard not detected.
[17179572.296000] Local APIC not detected. Using dummy APIC emulation.
[17179572.296000] Brought up 1 CPUs
[17179572.296000] migration_cost=0
[17179572.296000] NET: Registered protocol family 16
[17179572.296000] EISA bus registered
[17179572.296000] ACPI: bus type pci registered
[17179572.296000] PCI: PCI BIOS revision 2.10 entry at 0xfd9de, last bus=2
[17179572.296000] PCI: Using configuration type 1
[17179572.296000] Setting up standard PCI resources
[17179572.312000] ACPI: Interpreter enabled
[17179572.312000] ACPI: Using PIC for interrupt routing
[17179572.312000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.312000] PCI: Probing PCI hardware (bus 00)
[17179572.312000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.316000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179572.316000] PCI quirk: region ff00-ff3f claimed by PIIX4 ACPI
[17179572.316000] PCI quirk: region ff80-ff8f claimed by PIIX4 SMB
[17179572.316000] PIIX4 devres C PIO at fd60-fd67
[17179572.316000] PIIX4 devres G PIO at 0118-011f
[17179572.316000] Boot video device is 0000:00:14.0
[17179572.316000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.320000] ACPI: Embedded Controller [EC] (gpe 44) interrupt mode.
[17179572.328000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[17179572.328000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11)
[17179572.332000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11)
[17179572.332000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 *15)
[17179572.332000] ACPI: Power Resource [USBP] (on)
[17179572.332000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.332000] pnp: PnP ACPI init
[17179572.340000] pnp: PnP ACPI: found 11 devices
[17179572.340000] PnPBIOS: Disabled by ACPI PNP
[17179572.340000] PCI: Using ACPI for IRQ routing
[17179572.340000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.344000] PCI: Bus 1, cardbus bridge: 0000:00:13.0
[17179572.344000]   IO window: 00002000-000020ff
[17179572.344000]   IO window: 00002400-000024ff
[17179572.344000]   PREFETCH window: 20000000-21ffffff
[17179572.344000]   MEM window: 22000000-23ffffff
[17179572.344000] PCI: Bus 5, cardbus bridge: 0000:00:13.1
[17179572.344000]   IO window: 00002800-000028ff
[17179572.344000]   IO window: 00002c00-00002cff
[17179572.344000]   PREFETCH window: 24000000-25ffffff
[17179572.344000]   MEM window: 26000000-27ffffff
[17179572.344000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[17179572.344000] PCI: setting IRQ 9 as level-triggered
[17179572.344000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179572.344000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[17179572.344000] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179572.344000] NET: Registered protocol family 2
[17179572.384000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179572.384000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.384000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179572.384000] TCP: Hash tables configured (established 8192 bind 4096)
[17179572.384000] TCP reno registered
[17179572.384000] audit: initializing netlink socket (disabled)
[17179572.384000] audit(1170081595.384:1): initialized
[17179572.384000] VFS: Disk quotas dquot_6.5.1
[17179572.384000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.384000] Initializing Cryptographic API
[17179572.384000] io scheduler noop registered
[17179572.384000] io scheduler anticipatory registered
[17179572.384000] io scheduler deadline registered
[17179572.384000] io scheduler cfq registered (default)
[17179572.384000] isapnp: Scanning for PnP cards...
[17179572.740000] isapnp: No Plug & Play device found
[17179572.792000] Real Time Clock Driver v1.12ac
[17179572.792000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.792000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.796000] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[17179572.796000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.796000] ACPI: PCI Interrupt 0000:00:00.2[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179572.796000] ACPI: PCI interrupt for device 0000:00:00.2 disabled
[17179572.796000] mice: PS/2 mouse device common for all mice
[17179572.796000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.796000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.796000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.796000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.800000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.800000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.800000] EISA: Probing bus 0 at eisa.0
[17179572.800000] Cannot allocate resource for EISA slot 1
[17179572.800000] Cannot allocate resource for EISA slot 2
[17179572.800000] EISA: Detected 0 cards.
[17179572.804000] TCP bic registered
[17179572.804000] NET: Registered protocol family 1
[17179572.804000] NET: Registered protocol family 8
[17179572.804000] NET: Registered protocol family 20
[17179572.804000] Using IPI No-Shortcut mode
[17179572.804000] ACPI: (supports S0 S3 S4 S5)
[17179572.804000] Freeing unused kernel memory: 308k freed
[17179572.844000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.064000] Capability LSM initialized
[17179574.204000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179574.204000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.960000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179574.960000] PIIX4: chipset revision 0
[17179574.960000] PIIX4: not 100% native mode: will probe irqs later
[17179574.960000]     ide0: BM-DMA at 0x1c90-0x1c97, BIOS settings: hda:DMA, hdb:pio
[17179574.960000] Probing IDE interface ide0...
[17179575.248000] hda: FUJITSU MHT2030AT, ATA DISK drive
[17179575.920000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.012000] hda: max request size: 128KiB
[17179576.012000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(33)
[17179576.016000] hda: cache flushes supported
[17179576.016000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179576.548000] Probing IDE interface ide1...
[17179576.640000] usbcore: registered new driver usbfs
[17179576.640000] usbcore: registered new driver hub
[17179576.644000] USB Universal Host Controller Interface driver v3.0
[17179576.648000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 15
[17179576.648000] PCI: setting IRQ 15 as level-triggered
[17179576.648000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 15 (level, low) -> IRQ 15
[17179576.648000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179576.648000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179576.648000] uhci_hcd 0000:00:07.2: irq 15, io base 0x00001ca0
[17179576.648000] usb usb1: configuration #1 chosen from 1 choice
[17179576.648000] hub 1-0:1.0: USB hub found
[17179576.648000] hub 1-0:1.0: 2 ports detected
[17179577.184000] Attempting manual resume
[17179577.256000] kjournald starting.  Commit interval 5 seconds
[17179577.256000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.352000] input: PC Speaker as /class/input/input1
[17179591.440000] parport: PnPBIOS parport detected.
[17179591.440000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179591.468000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179591.720000] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[17179591.720000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[17179591.720000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179591.720000] A Prism2.5 PCI device found, phymem:0xe8010000, irq:9, mem:0xd085c000
[17179592.840000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179592.844000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[17179593.004000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179593.004000] Yenta: CardBus bridge found at 0000:00:13.0 [10cf:10e6]
[17179593.004000] Yenta O2: res at 0x94/0xD4: ea/00
[17179593.004000] Yenta O2: enabling read prefetch/write burst
[17179593.156000] Yenta: ISA IRQ mask 0x0c38, PCI irq 9
[17179593.156000] Socket status: 30000006
[17179593.156000] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179593.156000] Yenta: CardBus bridge found at 0000:00:13.1 [10cf:10e6]
[17179593.348000] Yenta: ISA IRQ mask 0x0c38, PCI irq 9
[17179593.348000] Socket status: 30000820
[17179593.608000] irda_init()
[17179593.608000] NET: Registered protocol family 23
[17179593.652000] ieee80211_crypt: registered algorithm 'NULL'
[17179594.076000] pccard: CardBus card inserted into slot 1
[17179594.080000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179594.088000] input: LBPS/2 Fujitsu Lifebook TouchScreen as /class/input/input2
[17179594.096000] found SMC SuperIO Chip (devid=0x28 rev=01 base=0x03f0): FDC37N769
[17179594.096000] smsc_superio_flat(): fir: 0x118, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
[17179594.096000] smsc_ircc_present: can't get sir_base of 0x2e8
[17179594.168000] ACPI: PCI Interrupt 0000:00:00.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179594.168000] PCI: Setting latency timer of device 0000:00:00.1 to 64
[17179594.420000] ts: Compaq touchscreen protocol output
[17179594.508000] cs: IO port probe 0x100-0x3af: excluding 0x118-0x11f
[17179594.512000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179594.512000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.512000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.512000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.532000] cs: IO port probe 0x100-0x3af: excluding 0x118-0x11f
[17179594.532000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179594.532000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.532000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.532000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.572000] Linux Tulip driver version 1.1.14 (May 6, 2006)
[17179594.740000] intel8x0_measure_ac97_clock: measured 55386 usecs
[17179594.740000] intel8x0: clocking to 48000
[17179594.768000] PCI: Enabling device 0000:05:00.0 (0000 -> 0003)
[17179594.768000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179594.768000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179594.768000] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[17179594.780000] eth0: ADMtek Comet rev 17 at Port 0x2800, 00:04:5A:A4:47:14, IRQ 9.
[17179595.292000] lp0: using parport0 (interrupt-driven).
[17179595.348000] Adding 746948k swap on /dev/disk/by-uuid/94292ecc-5971-475f-9ab6-50af14c70af1.  Priority:-1 extents:1 across:746948k
[17179595.428000] EXT3 FS on hda3, internal journal
[17179596.248000] NET: Registered protocol family 17
[17179597.812000] ACPI: AC Adapter [AC] (on-line)
[17179597.900000] ACPI: Battery Slot [CMB1] (battery absent)
[17179597.940000] ACPI: Power Button (FF) [PWRF]
[17179597.940000] ACPI: Power Button (CM) [PWRB]
[17179597.940000] ACPI: Lid Switch [LID]
[17179598.168000] ibm_acpi: ec object not found
[17179598.176000] 0000:05:00.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[17179598.176000] eth1: Setting full-duplex based on MII#1 link partner capability of c5e1.
[17179598.220000] pcc_acpi: loading...
[17179598.564000] NET: Registered protocol family 10
[17179598.564000] lo: Disabled Privacy Extensions
[17179598.568000] IPv6 over IPv4 tunneling driver
[17179598.620000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179599.204000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179602.948000] Linux agpgart interface v0.101 (c) Dave Jones
[17179603.012000] [drm] Initialized drm 1.0.1 20051102
[17179603.040000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179603.040000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179604.688000] apm: BIOS not found.
[17179609.444000] eth1: no IPv6 routers present
[17179611.012000] Bluetooth: Core ver 2.8
[17179611.012000] NET: Registered protocol family 31
[17179611.012000] Bluetooth: HCI device and connection manager initialized
[17179611.012000] Bluetooth: HCI socket layer initialized
[17179611.064000] Bluetooth: L2CAP ver 2.8
[17179611.064000] Bluetooth: L2CAP socket layer initialized
[17179611.088000] Bluetooth: RFCOMM socket layer initialized
[17179611.088000] Bluetooth: RFCOMM TTY layer initialized
[17179611.088000] Bluetooth: RFCOMM ver 1.7
[17179947.436000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[17179947.436000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17179947.436000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[17179947.788000] SCSI subsystem initialized

```

Could there be an irq conflict?

---

### Post by hggdh on 2007-01-29
I see an eth0 and eth1, but no references to wlan0. Please run 'sudo lshw -C Network' & post the output.

---

### Post by job2600 on 2007-01-29
> **hggdh said:**
> I see an eth0 and eth1, but no references to wlan0. Please run 'sudo lshw -C Network' & post the output.

#sudo lshw -C Network

```
 *-network DISABLED      
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 link=no multicast=yes
       resources: iomemory:e8010000-e8010fff irq:9
  *-network
       description: Ethernet interface
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet
       vendor: Linksys
       physical id: 1
       bus info: pci@05:00.0
       logical name: eth1
       version: 11
       serial: 00:04:5a:a4:47:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 ip=192.168.0.10 multicast=yes
       resources: ioport:2800-28ff iomemory:26000000-260003ff irq:9

```

---

### Post by job2600 on 2007-01-29
Any ideas what would cause lshw to show the wireless interface as disabled?

---

### Post by job2600 on 2007-01-29
I got it working by blacklisting the prism modules. Thanks to:

[http://www.ubuntuforums.org/showthread.php?t=288649]("http://www.ubuntuforums.org/showthread.php?t=288649")


Oddly enough my wireless is now working as eth0 instead of wlan0, although lshw still shows it as disabled

```

 *-network DISABLED      
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 01
       serial: 00:e0:00:d3:b9:df
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.4.1 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:e8010000-e8010fff irq:9


```

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

### Post by wimedel on 2007-11-05
I am new on Ubuntu and I am trying Gutsy64 on a AM64 motherboard with a SMC2802 V2 wireless card.
During installation the card worked fine. My own network and the networks in my neighbourhood were recognised and there was no problem to make connection to my own network (the others not ....).
After installation there are no networks recognised.
iwconfig gives:

```
eth1      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
What may be the problem and what the solution?
Wim

---

