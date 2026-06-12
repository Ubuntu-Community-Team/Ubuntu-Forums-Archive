---
title: "WIFI randomly crashes on my lappy"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by eimor on 2007-12-08
I need help, im a total noob, my problem is that i have ubuntu in my laptop, and every now and then my wifi dies on me, im browsing and surfing the web happly but suddenly the thing stops workin, i have to reboot to solve this, but its getting to my nerves having to do so. Dont know wich wificard i have on the pc, heard that depending on the brand of it you could get some trouble. Also read somewhere that the best thing is to have an atheros card, but i don think that this is my case. Think its realtek or even worse (broadcom). But stangely the thing got recognized on the livecd boot. Anyone can help me with this? Thanks in advance, and excuse my english but my mothertongue is spanish cause im from argentina.

---

### Post by xeth_delta on 2007-12-08
Please post between code tags (the # button in the editing frame) the output of the commands:
```
lscpi
lsusb
dmesg
```

To do this go to a terminal and run them from there.

Xeth

---

### Post by eimor on 2007-12-09
Here is what i got in terminal

lspci output
#00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
#00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
#00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
#00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
#00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
#00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
#00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
#00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
#00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
#00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
#00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
#00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
#00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
#00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
#00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
#00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
#00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
#06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
#06:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
#06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
#06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lsusb output
#Bus 005 Device 002: ID 0db0:6877 Micro Star International 
#Bus 005 Device 001: ID 0000:0000  
#Bus 004 Device 001: ID 0000:0000  
#Bus 003 Device 001: ID 0000:0000  
#Bus 002 Device 001: ID 0000:0000  
#Bus 001 Device 001: ID 0000:0000  

dmesg output
#[    0.000000] ACPI: PM-Timer IO Port: 0x1008
#[    0.000000] ACPI: Local APIC address 0xfee00000
#[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
#[    0.000000] Processor #0 6:14 APIC version 20
#[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
#[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
#[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
#[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
#[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
#[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
#[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
#[    0.000000] ACPI: IRQ0 used by override.
#[    0.000000] ACPI: IRQ2 used by override.
#[    0.000000] ACPI: IRQ9 used by override.
#[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
#[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
#[    0.000000] Using ACPI (MADT) for SMP configuration information
#[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
#[    0.000000] Built 1 zonelists.  Total pages: 127651
#[    0.000000] Kernel command line: root=UUID=a525a323-7bd6-4e61-9c5e-b80807a10af4 ro quiet splash
#[    0.000000] mapped APIC to ffffd000 (fee00000)
#[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
#[    0.000000] Enabling fast FPU save and restore... done.
#[    0.000000] Enabling unmasked SIMD FPU exception support... done.
#[    0.000000] Initializing CPU#0
#[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
#[    0.000000] Detected 1866.950 MHz processor.
#[   14.099071] Console: colour VGA+ 80x25
#[   14.099230] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
#[   14.099415] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
#[   14.110990] Memory: 498316k/514624k available (2015k kernel code, 15660k reserved, 916k data, 364k init, 0k highmem)
#[   14.110999] virtual kernel memory layout:
#[   14.111000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
#[   14.111001]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
#[   14.111003]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
#[   14.111004]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
#[   14.111005]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
#[   14.111006]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
#[   14.111007]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
#[   14.111011] Checking if this processor honours the WP bit even in supervisor mode... Ok.
#[   14.111047] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
#[   14.111180] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
#[   14.111186] hpet0: 3 64-bit timers, 14318180 Hz
#[   14.192124] Calibrating delay using timer specific routine.. 3737.61 BogoMIPS (lpj=7475234)
#[   14.192144] Security Framework v1.0.0 initialized
#[   14.192152] SELinux:  Disabled at boot.
#[   14.192164] Mount-cache hash table entries: 512
#[   14.192278] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
#[   14.192286] monitor/mwait feature present.
#[   14.192288] using mwait in idle threads.
#[   14.192291] CPU: L1 I cache: 32K, L1 D cache: 32K
#[   14.192294] CPU: L2 cache: 1024K
#[   14.192296] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
#[   14.192304] Compat vDSO mapped to ffffe000.
#[   14.192317] Checking 'hlt' instruction... OK.
#[   14.208210] SMP alternatives: switching to UP code
#[   14.208386] Freeing SMP alternatives: 11k freed
#[   14.208632] Early unpacking initramfs... done
#[   14.531193] ACPI: Core revision 20070126
#[   14.531251] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
#[   14.555865] CPU0: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz stepping 0c
#[   14.555891] Total of 1 processors activated (3737.61 BogoMIPS).
#[   14.556087] ENABLING IO-APIC IRQs
#[   14.556291] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
#[   14.839465] APIC calibration not consistent with PM Timer: 96ms instead of 100ms
#[   14.839467] APIC delta adjusted to PM-Timer: 833362 (801933)
#[   14.839509] Brought up 1 CPUs
#[   14.839608] Booting paravirtualized kernel on bare hardware
#[   14.839694] Time: 14:16:53  Date: 11/09/107
#[   14.839715] NET: Registered protocol family 16
#[   14.839791] EISA bus registered
#[   14.839798] ACPI: bus type pci registered
#[   14.878619] PCI: PCI BIOS revision 2.10 entry at 0xfd843, last bus=6
#[   14.878621] PCI: Using configuration type 1
#[   14.878623] Setting up standard PCI resources
#[   14.882267] ACPI: EC: Look up EC in DSDT
#[   14.882781] ACPI: EC: GPE=0x19, ports=0x66, 0x62
#[   15.379643] ACPI: System BIOS is requesting _OSI(Linux)
#[   15.379645] ACPI: Please test with "acpi_osi=!Linux"
#[   15.379647] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
#[   15.380143] ACPI: Interpreter enabled
#[   15.380146] ACPI: (supports S0 S3 S4 S5)
#[   15.380161] ACPI: Using IOAPIC for interrupt routing
#[   15.385309] ACPI: EC: GPE=0x19, ports=0x66, 0x62
#[   15.385356] ACPI: PCI Root Bridge [PCI0] (0000:00)
#[   15.385365] PCI: Probing PCI hardware (bus 00)
#[   15.386092] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
#[   15.386097] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
#[   15.386960] PCI: Transparent bridge - 0000:00:1e.0
#[   15.387034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
#[   15.387322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
#[   15.387439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
#[   15.387554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
#[   15.387684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
#[   15.390283] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
#[   15.390373] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
#[   15.390459] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
#[   15.390544] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
#[   15.390629] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
#[   15.390715] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
#[   15.390801] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
#[   15.390886] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
#[   15.391014] Linux Plug and Play Support v0.97 (c) Adam Belay
#[   15.391023] pnp: PnP ACPI init
#[   15.391030] ACPI: bus type pnp registered
#[   15.392606] pnp: PnP ACPI: found 11 devices
#[   15.392608] ACPI: ACPI bus type pnp unregistered
#[   15.392612] PnPBIOS: Disabled by ACPI PNP
#[   15.392657] PCI: Using ACPI for IRQ routing
#[   15.392659] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
#[   15.411631] NET: Registered protocol family 8
#[   15.411633] NET: Registered protocol family 20
#[   15.411705] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
#[   15.411708] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
#[   15.411711] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
#[   15.411714] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
#[   15.411720] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
#[   15.411727] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
#[   15.411730] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
#[   15.414889] Time: tsc clocksource has been installed.
#[   15.414904] Switched to high resolution mode on CPU 0
#[   15.441969] PCI: Bridge: 0000:00:1c.0
#[   15.441972]   IO window: f000-ffff
#[   15.441979]   MEM window: fac00000-febfffff
#[   15.441983]   PREFETCH window: disabled.
#[   15.441989] PCI: Bridge: 0000:00:1c.1
#[   15.441990]   IO window: disabled.
#[   15.441995]   MEM window: disabled.
#[   15.442000]   PREFETCH window: disabled.
#[   15.442005] PCI: Bridge: 0000:00:1c.2
#[   15.442006]   IO window: disabled.
#[   15.442012]   MEM window: f7000000-f70fffff
#[   15.442016]   PREFETCH window: disabled.
#[   15.442027] PCI: Bridge: 0000:00:1e.0
#[   15.442030]   IO window: 2000-2fff
#[   15.442036]   MEM window: f0200000-f02fffff
#[   15.442040]   PREFETCH window: disabled.
#[   15.442068] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
#[   15.442076] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
#[   15.442085] PCI: Setting latency timer of device 0000:00:1c.0 to 64
#[   15.442108] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
#[   15.442115] PCI: Setting latency timer of device 0000:00:1c.1 to 64
#[   15.442137] PCI: Enabling device 0000:00:1c.2 (0000 -> 0002)
#[   15.442142] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
#[   15.442149] PCI: Setting latency timer of device 0000:00:1c.2 to 64
#[   15.442162] PCI: Setting latency timer of device 0000:00:1e.0 to 64
#[   15.442174] NET: Registered protocol family 2
#[   15.478808] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
#[   15.478847] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
#[   15.478981] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
#[   15.479072] TCP: Hash tables configured (established 16384 bind 16384)
#[   15.479074] TCP reno registered
#[   15.490878] checking if image is initramfs... it is
#[   16.128490] Freeing initrd memory: 7348k freed
#[   16.128736] Simple Boot Flag at 0x35 set to 0x1
#[   16.129066] audit: initializing netlink socket (disabled)
#[   16.129079] audit(1197209813.540:1): initialized
#[   16.130789] VFS: Disk quotas dquot_6.5.1
#[   16.130831] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
#[   16.130915] io scheduler noop registered
#[   16.130917] io scheduler anticipatory registered
#[   16.130919] io scheduler deadline registered
#[   16.130932] io scheduler cfq registered (default)
#[   16.130946] Boot video device is 0000:00:02.0
#[   16.131102] PCI: Setting latency timer of device 0000:00:1c.0 to 64
#[   16.131158] assign_interrupt_mode Found MSI capability
#[   16.131161] Allocate Port Service[0000:00:1c.0:pcie00]
#[   16.131192] Allocate Port Service[0000:00:1c.0:pcie02]
#[   16.131287] PCI: Setting latency timer of device 0000:00:1c.1 to 64
#[   16.131343] assign_interrupt_mode Found MSI capability
#[   16.131345] Allocate Port Service[0000:00:1c.1:pcie00]
#[   16.131371] Allocate Port Service[0000:00:1c.1:pcie02]
#[   16.131461] PCI: Setting latency timer of device 0000:00:1c.2 to 64
#[   16.131517] assign_interrupt_mode Found MSI capability
#[   16.131519] Allocate Port Service[0000:00:1c.2:pcie00]
#[   16.131546] Allocate Port Service[0000:00:1c.2:pcie02]
#[   16.131688] isapnp: Scanning for PnP cards...
#[   16.485752] isapnp: No Plug & Play device found
#[   16.509090] Real Time Clock Driver v1.12ac
#[   16.509315] hpet_resources: 0xfed00000 is busy
#[   16.509341] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
#[   16.510487] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
#[   16.510670] input: Macintosh mouse button emulation as /class/input/input0
#[   16.510736] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
#[   16.513589] i8042.c: Detected active multiplexing controller, rev 1.1.
#[   16.514662] serio: i8042 KBD port at 0x60,0x64 irq 1
#[   16.514668] serio: i8042 AUX0 port at 0x60,0x64 irq 12
#[   16.514671] serio: i8042 AUX1 port at 0x60,0x64 irq 12
#[   16.514673] serio: i8042 AUX2 port at 0x60,0x64 irq 12
#[   16.514675] serio: i8042 AUX3 port at 0x60,0x64 irq 12
#[   16.514869] mice: PS/2 mouse device common for all mice
#[   16.515055] EISA: Probing bus 0 at eisa.0
#[   16.515063] Cannot allocate resource for EISA slot 1
#[   16.515066] Cannot allocate resource for EISA slot 2
#[   16.515092] EISA: Detected 0 cards.
#[   16.515185] TCP cubic registered
#[   16.515199] NET: Registered protocol family 1
#[   16.515222] Using IPI No-Shortcut mode
#[   16.515374]   Magic number: 3:915:282
#[   16.515418]   hash matches device ttyvd
#[   16.515535]   hash matches device tty19
#[   16.515732] Freeing unused kernel memory: 364k freed
#[   16.621328] input: AT Translated Set 2 keyboard as /class/input/input1
#[   17.698397] AppArmor: AppArmor initialized<5>audit(1197209815.040:2):  type=1505 info="AppArmor initialized" pid=1252
#[   17.703426] fuse init (API version 7.8)
#[   17.707060] Failure registering capabilities with primary security module.
#[   17.715620] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
#[   17.715626] ACPI: Processor [CPU0] (supports 8 throttling states)
#[   17.715637] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
#[   17.716884] ACPI: Thermal Zone [THRM] (30 C)
#[   18.162487] usbcore: registered new interface driver usbfs
#[   18.162507] usbcore: registered new interface driver hub
#[   18.162525] usbcore: registered new device driver usb
#[   18.163245] USB Universal Host Controller Interface driver v3.0
#[   18.163308] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
#[   18.163320] PCI: Setting latency timer of device 0000:00:1d.0 to 64
#[   18.163324] uhci_hcd 0000:00:1d.0: UHCI Host Controller
#[   18.163522] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
#[   18.163555] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
#[   18.163661] usb usb1: configuration #1 chosen from 1 choice
#[   18.163684] hub 1-0:1.0: USB hub found
#[   18.163689] hub 1-0:1.0: 2 ports detected
#[   18.217810] SCSI subsystem initialized
#[   18.222640] libata version 2.21 loaded.
#[   18.264300] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
#[   18.264313] PCI: Setting latency timer of device 0000:00:1d.1 to 64
#[   18.264317] uhci_hcd 0000:00:1d.1: UHCI Host Controller
#[   18.264338] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
#[   18.264373] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
#[   18.264461] usb usb2: configuration #1 chosen from 1 choice
#[   18.264484] hub 2-0:1.0: USB hub found
#[   18.264490] hub 2-0:1.0: 2 ports detected
#[   18.287313] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
#[   18.368233] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
#[   18.368245] PCI: Setting latency timer of device 0000:00:1d.2 to 64
#[   18.368249] uhci_hcd 0000:00:1d.2: UHCI Host Controller
#[   18.368271] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
#[   18.368307] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
#[   18.368393] usb usb3: configuration #1 chosen from 1 choice
#[   18.368417] hub 3-0:1.0: USB hub found
#[   18.368422] hub 3-0:1.0: 2 ports detected
#[    4.080000] Marking TSC unstable due to: possible TSC halt in C2.
#[    4.084000] Time: hpet clocksource has been installed.
#[    4.100000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
#[    4.100000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
#[    4.100000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
#[    4.100000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
#[    4.100000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
#[    4.100000] usb usb4: configuration #1 chosen from 1 choice
#[    4.100000] hub 4-0:1.0: USB hub found
#[    4.100000] hub 4-0:1.0: 2 ports detected
#[    4.204000] ata_piix 0000:00:1f.1: version 2.11
#[    4.204000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
#[    4.204000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
#[    4.204000] scsi0 : ata_piix
#[    4.204000] scsi1 : ata_piix
#[    4.204000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
#[    4.204000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
#[    4.236000] usb 2-1: new full speed USB device using uhci_hcd and address 2
#[    4.500000] Clocksource tsc unstable (delta = -246777754 ns)
#[    4.532000] usb 2-1: configuration #1 chosen from 1 choice
#[    4.540000] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, TI03, max UDMA/33
#[    4.728000] ata1.00: configured for UDMA/33
#[    4.728000] ata2: port disabled. ignoring.
#[    4.736000] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D TI03 PQ: 0 ANSI: 5
#[    4.736000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
#[    4.736000] ata_piix 0000:00:1f.2: invalid MAP value 0
#[    4.892000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
#[    4.892000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
#[    4.892000] scsi2 : ata_piix
#[    4.892000] scsi3 : ata_piix
#[    4.892000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 20
#[    4.892000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 20
#[    5.056000] ata3.00: ATA-8: FUJITSU MHW2080BH PL, 0000001C, max UDMA/100
#[    5.056000] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
#[    5.072000] ata3.00: configured for UDMA/100
#[    5.236000] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
#[    5.240000] PCI: Enabling device 0000:06:04.0 (0195 -> 0197)
#[    5.240000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 18 (level, low) -> IRQ 18
#[    5.292000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f0200000-f02007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
#[    5.296000] 8139cp 0000:06:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
#[    5.296000] 8139cp 0000:06:05.0: Try the "8139too" driver instead.
#[    5.296000] 8139too Fast Ethernet driver 0.9.28
#[    5.296000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 16 (level, low) -> IRQ 17
#[    5.296000] eth0: RealTek RTL8139 at 0xe005ec00, 00:03:0d:6b:c7:3e, IRQ 17
#[    5.296000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
#[    5.300000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
#[    5.300000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
#[    5.300000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
#[    5.300000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
#[    5.300000] ehci_hcd 0000:00:1d.7: debug port 1
#[    5.300000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
#[    5.300000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0004000
#[    5.304000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
#[    5.304000] usb usb5: configuration #1 chosen from 1 choice
#[    5.304000] hub 5-0:1.0: USB hub found
#[    5.304000] hub 5-0:1.0: 8 ports detected
#[    5.368000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
#[    5.368000] Uniform CD-ROM driver Revision: 3.20
#[    5.368000] sr 0:0:0:0: Attached scsi CD-ROM sr0
#[    5.372000] sr 0:0:0:0: Attached scsi generic sg0 type 5
#[    5.372000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
#[    5.384000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
#[    5.384000] sd 2:0:0:0: [sda] Write Protect is off
#[    5.384000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
#[    5.384000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
#[    5.384000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
#[    5.384000] sd 2:0:0:0: [sda] Write Protect is off
#[    5.384000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
#[    5.384000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
#[    5.384000]  sda: sda1 sda2 sda3 < sda5 >
#[    5.444000] sd 2:0:0:0: [sda] Attached SCSI disk
#[    5.648000] usb 5-3: new high speed USB device using ehci_hcd and address 2
#[    5.648000] Attempting manual resume
#[    5.648000] swsusp: Resume From Partition 8:5
#[    5.648000] PM: Checking swsusp image.
#[    5.648000] PM: Resume from disk failed.
#[    5.664000] kjournald starting.  Commit interval 5 seconds
#[    5.664000] EXT3-fs: mounted filesystem with ordered data mode.
#[    5.916000] usb 5-3: configuration #1 chosen from 1 choice
#[    5.916000] usb 2-1: USB disconnect, address 2
#[    6.568000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d0041087192]
#[   11.712000] eth0: link down
#[   12.524000] NET: Registered protocol family 10
#[   12.524000] lo: Disabled Privacy Extensions
#[   12.524000] ADDRCONF(NETDEV_UP): eth0: link is not ready
#[   12.972000] Linux agpgart interface v0.102 (c) Dave Jones
#[   12.988000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
#[   12.992000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
#[   13.072000] agpgart: Detected an Intel 945GM Chipset.
#[   13.072000] agpgart: Detected 7932K stolen memory.
#[   13.088000] agpgart: AGP aperture is 256M @ 0xc0000000
#[   13.628000] intel_rng: FWH not detected
#[   13.680000] iTCO_vendor_support: vendor-support=0
#[   13.684000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
#[   13.684000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
#[   13.684000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
#[   14.636000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
#[   14.636000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
#[   14.656000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
#[   14.688000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
#[   14.740000] sdhci: Secure Digital Host Controller Interface driver
#[   14.740000] sdhci: Copyright(c) Pierre Ossman
#[   15.016000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
#[   15.180000] sdhci: SDHCI controller found at 0000:06:04.2 [1217:7120] (rev 1)
#[   15.180000] ACPI: PCI Interrupt 0000:06:04.2[A] -> GSI 18 (level, low) -> IRQ 18
#[   15.180000] sdhci:slot0: Unknown controller version (16). You may experience problems.
#[   15.180000] mmc0: SDHCI at 0xb0200800 irq 18 PIO
#[   15.284000] ieee80211_init: failed to initialize WME (err=-17)
#[   15.296000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
#[   15.296000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
#[   15.296000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
#[   15.296000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
#[   15.308000] wmaster0: Selected rate control algorithm 'simple'
#[   15.388000] usbcore: registered new interface driver rt73usb
#[   15.600000] lp: driver loaded but no devices found
#[   15.696000] Adding 899600k swap on /dev/sda5.  Priority:-1 extents:1 across:899600k
#[   16.008000] EXT3 FS on sda2, internal journal
#[   17.128000] input: Power Button (FF) as /class/input/input3
#[   17.132000] ACPI: Power Button (FF) [PWRF]
#[   17.168000] input: Lid Switch as /class/input/input4
#[   17.172000] ACPI: Lid Switch [LID0]
#[   17.204000] input: Power Button (CM) as /class/input/input5
#[   17.204000] ACPI: Power Button (CM) [PWRB]
#[   17.220000] input: Sleep Button (CM) as /class/input/input6
#[   17.220000] ACPI: Sleep Button (CM) [SLPB]
#[   17.296000] ACPI: Battery Slot [BAT0] (battery present)
#[   17.332000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
#[   17.332000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
#[   17.348000] No dock devices found.
#[   17.412000] ACPI: AC Adapter [AC0] (off-line)
#[   18.568000] ppdev: user-space parallel port driver
#[   18.872000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
#[   18.984000] audit(1197220631.165:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4967 profile="/usr/sbin/cupsd"
#[   19.016000] apm: BIOS not found.
#[   19.288000] Failure registering capabilities with primary security module.
#[   19.432000] Bluetooth: Core ver 2.11
#[   19.432000] NET: Registered protocol family 31
#[   19.432000] Bluetooth: HCI device and connection manager initialized
#[   19.432000] Bluetooth: HCI socket layer initialized
#[   19.452000] Bluetooth: L2CAP ver 2.8
#[   19.452000] Bluetooth: L2CAP socket layer initialized
#[   19.596000] Bluetooth: RFCOMM socket layer initialized
#[   19.596000] Bluetooth: RFCOMM TTY layer initialized
#[   19.596000] Bluetooth: RFCOMM ver 1.8
#[   23.072000] [drm] Initialized drm 1.1.0 20060810
#[   23.076000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
#[   23.080000] [drm] Initialized i915 1.6.0 20060119 on minor 0
#[   57.040000] NET: Registered protocol family 17
#[   57.948000] wlan0: Initial auth_alg=0
#[   57.948000] wlan0: authenticate with AP 00:13:64:3d:b3:39
#[   57.952000] wlan0: RX authentication from 00:13:64:3d:b3:39 (alg=0 transaction=2 status=0)
#[   57.952000] wlan0: authenticated
#[   57.952000] wlan0: associate with AP 00:13:64:3d:b3:39
#[   57.952000] wlan0: RX AssocResp from 00:13:64:3d:b3:39 (capab=0x401 status=0 aid=1)
#[   57.952000] wlan0: associated
#[   57.952000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
#[   58.352000] wlan0: duplicate address detected!
#[   66.172000] wlan0: duplicate address detected!
#[   89.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   89.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
#[   90.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   90.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   90.260000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
#[   91.360000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   91.460000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
#[   91.560000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   91.660000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -110.
#[   91.760000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   91.860000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   91.960000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   92.060000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   92.160000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
#[   92.160000] phy0 -> rt73usb_bbp_write: Error - PHY_CSR3 register busy. Write failed.

Thanks for ansewering, i just cant get why wificard crashes and  why it does so randomly.:confused:

---

### Post by xeth_delta on 2007-12-09
This is funny, I cannot find your card in the lspci or lsusb output you posted. I can see the wlan0 interface being activated through dmesg, though. Is it an internal card?

Please post also the output of **lsmod**. Please do use the code tags when you do it. in the edit window, when you post, there is a button with a # on it.
Also, please the output of dmesg after a network crash.

Xeth

---

### Post by eimor on 2007-12-09
This is what i get from lsmod

```
Module                  Size  Used by
af_packet              24840  4 
i915                   25856  2 
drm                    83348  3 i915
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
video                  18060  0 
container               5504  0 
battery                11012  0 
button                  8976  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
rt73usb                25344  0 
rt2x00usb              12032  1 rt73usb
rt2x00lib              19584  2 rt73usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
joydev                 11328  0 
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
cfg80211                7304  1 mac80211
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
sdhci                  18828  0 
mmc_core               28420  1 sdhci
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
psmouse                39952  0 
serio_raw               8068  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25620  1 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
agpgart                35016  3 drm,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ipv6                  273892  8 
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
8139too                27776  0 
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_generic             8452  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0 
usbcore               138632  5 rt73usb,rt2x00usb,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

The wificard is internall, i have a dedicated button to switch it on/off. And thanks again your quick reply.

---

### Post by eimor on 2007-12-10
Still having problems with wifi card
Dont know wich chipset this laptop has.

---

### Post by xeth_delta on 2007-12-11
> **eimor said:**
> Still having problems with wifi card
Dont know wich chipset this laptop has.

Sorry, for taking so long to reply again.Jjust looked one more time at your dmesg and lsmod output and noticed that indeed you do have a realtek card. If I am not mistaken, the card is placed on the USB instead of PCI bus. As far as I know this is not a very usual setup for an integrated wireless card.

How did you configure the card? Did you do it yourself or was it out of the box? Do you know if Ndiswrapper is being used?

Here you have a very good **how to** for your card. Hope it helps, let us know if you have any problems following it: [http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236").

Xeth

---

### Post by eimor on 2007-12-12
The card was like that out of the box. And when i installed ubuntu it got reconigzed instantly, but ive noticed something else, its me just guessing cause i havent been able to try on another router brand, but the two routers that i tested where Kozumi, maybe its a problem with that brand. As soon as i get home (hope my brother didnt take the laptop) ill try with another routers (edimax, linksys, netgear) and also try the guide you sent me. Thanks a lot for your help. This is why i like ubuntu, a comunity with users like you make this os more user friendly than other linux distros. Thanks again.

---

### Post by xeth_delta on 2007-12-12
You're welcome, write us again and let us know how it goes.

---

### Post by eimor on 2007-12-22
I gave the laptop to my gf cause a got a new one, but still now i have two laptops with the wifi problem. The thing is that in windows both seem to work flawlessly, What is that thing about ndiswrapper? I heard that a lot of people used something like that to make their wifi work. Hope to hear from all of you soon and i if i dont merry xmas ta all and happy holidays.

---

### Post by A + on 2007-12-22
Can you help me too please?  My connection also drops intermittently and it looks like I have the same Realtek hardware as eimor.  It seems to go if the computer is idle for a short period although I could be wrong there (I'm wondering if it's a timeout thing).  
 
```
james@james-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8 
isofs                  36412  0 
udf                    87204  1 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
sbs                    19592  0 
ac                      6148  0 
container               5504  0 
button                  8976  0 
asus_acpi              17308  0 
dock                   10656  0 
battery                11012  0 
ndiswrapper           193436  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         293792  1 
snd_pcm_oss            43008  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                80644  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_oss            35328  0 
pcmcia                 41388  0 
snd_seq_midi_event      8704  1 snd_seq_oss
snd_seq                54256  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24580  2 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  4224  0 
serio_raw               8068  0 
psmouse                39952  0 
snd                    56708  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
af_packet              24840  8 
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
8139too                27776  0 
ata_generic             8452  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ata_piix               17540  4 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

```


The wifi card is Atheros AR5007EG which was not working until I followed a guide involving downloading ndiswrapper and a new driver, compiling and running the program and blacklisting an old driver.  It'd be stretching it to say I knew what I was doing 100% of the time!  The Atheros card is getting recognised as AR5006EG when it's AR5007EG.  A problem?  The wireless works in general though.

lspci:

```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Thanks

---

### Post by xeth_delta on 2007-12-22
A +, your hardware is different to the one eimor had, as far as I can see. Yor card seems to be an Atheros, the same brand I have, I use the mad-wifi drivers for it. Have you tried those? HEre is a link to the project download page: [http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=547876]("http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=547876")

Can you also post the 20 last lines from the output of dmesg after a crash?

Xeth

---

### Post by eimor on 2007-12-23
Reading about the issue of the idle time i realized that this happens to me too. If i keep using the wifi connection the card works great but after a short period unused, i get no connection. What could be causing this? Oh, on the next post i will paste the terminal output so you guys know wich card im using, under xp is shown as a usb card.

---

### Post by A + on 2007-12-23
> **xeth_delta said:**
> Can you also post the 20 last lines from the output of dmesg after a crash? 

Again the laptop was idle for a spell before the wifi went to sleep:

```
[   19.292000]   send /proc/acpi/dsdt to the developers
[   19.344000] input: Power Button (FF) as /class/input/input4
[   19.348000] ACPI: Power Button (FF) [PWRF]
[   19.388000] input: Lid Switch as /class/input/input5
[   19.392000] ACPI: Lid Switch [LID]
[   19.432000] input: Power Button (CM) as /class/input/input6
[   19.432000] ACPI: Power Button (CM) [PWRB]
[   19.488000] ACPI: AC Adapter [AC0] (on-line)
[   19.516000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.008000] ppdev: user-space parallel port driver
[   21.372000] audit(1198413227.175:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5882 profile="/usr/sbin/cupsd"
[   21.444000] apm: BIOS not found.
[   21.696000] Failure registering capabilities with primary security module.
[   21.864000] Bluetooth: Core ver 2.11
[   21.864000] NET: Registered protocol family 31
[   21.868000] Bluetooth: HCI device and connection manager initialized
[   21.868000] Bluetooth: HCI socket layer initialized
[   21.876000] Bluetooth: L2CAP ver 2.8
[   21.876000] Bluetooth: L2CAP socket layer initialized
[   21.964000] Bluetooth: RFCOMM socket layer initialized
[   21.964000] Bluetooth: RFCOMM TTY layer initialized
[   21.964000] Bluetooth: RFCOMM ver 1.8
[   25.388000] [drm] Initialized drm 1.1.0 20060810
[   25.392000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.392000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   57.748000] NET: Registered protocol family 10
[   57.748000] lo: Disabled Privacy Extensions
[   57.748000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.748000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.328000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   78.320000] wlan0: no IPv6 routers present
[12856.804000] ndiswrapper (mp_reset:62): wlan0 is being reset
[12860.804000] ndiswrapper (mp_reset:62): wlan0 is being reset
[12864.804000] ndiswrapper (mp_reset:62): wlan0 is being reset
[12868.804000] ndiswrapper (mp_reset:62): wlan0 is being reset
[12872.804000] ndiswrapper (mp_reset:62): wlan0 is being reset

```

Any ideas?  Could be a bug in ndiswrapper or a hardware event which is disturbing the driver.  Could ndiswrapper be fixable for this card?  I read on a link that it isn't compatible and madwifi is your best bet.  I'll give the madwifi drivers a shot next time anyway, thanks.

james

---

### Post by xeth_delta on 2007-12-23
A+, my first suggestion would be to try using the madwifi drivers.
Uninstall the drivers from ndiswrapper, download the package (from the link I provided in a previous post) and then compile. It won't take long. You will need the development packages.

If you need any help compiling, let us know. We'd be glad to help.

Xeth

---

### Post by A + on 2007-12-23
Xeth

I downloaded a copy of the madwifi drivers (madwifi-0.9.3.3.tar.gz) from the link you gave me  [http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=547876](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=547876) and followed the instructions on compiling it at madwifi.org [_here_](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo).  I compiled and loaded the module succesfully but after that, nada.  Madwifi creates an "ath0" device, whereas Ndiswrapper creates a "wlan0" device, is that correct?  When i run the wlanconfig cmd with the ath0 devicename i get errors saying no such device.  I can't configure the interface thus wireless doesn't exist on my laptop now.

```
:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

nothing except eth0 and lo yet my card is recognised with lshw -C network but without a logical name (I'm expecting "ath0", aren't I?)

```
:~/Desktop$ lshw -C network
       WARNING: you should run this program as super-user.
       *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:fb:43:0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

I'm probably making some very simple mistake which involves the previous install of ndiswrapper.  If you know of a good guide for installing madwifi please let me know.

---

### Post by xeth_delta on 2007-12-23
You are right, madwifi should give you an ath0 device. Can you check dmesg after loading the modules? The madwifi drivers come with a utility found in the scripts directory called madwifi-unload. Use it to unload the modules and then **sudo modprobe ath_pci** again.

Did you also uninstall ndiswrapper from your system?

---

### Post by A + on 2007-12-23
Thanks for your help and the prompt reply!

It's late now but I got lonely for my wifi and re-installed ndiswrapper (updated a few days ago!) which I did fairly fast, I must be getting good at this linux thing even if I haven't a clue what I'm doing half the time.

I will try again soon with madwifi and would ideally like another partition where I can mess around because I'd get a clean install.  Is there a disk defragmenter in linux?  I could re-size this partition and put another copy of ubuntu at the end on 5GB. 

Without a new partition would you suggest deleting everything I search for and find of ndiswrapper?  I also blacklisted a (packaged?) driver or something - would that be a problem?  Should I undo that?  Actually I can't remember if I entered some information in Interfaces either - you know how it is.  

I will try again over Christmas with your instructions above and I hope you might help if you can.  I'm doing this out of interest in linux more than anything.  Take care and Happy Christmas from Ireland  :mrgreen:

james

---

### Post by xeth_delta on 2007-12-24
> Thanks for your help and the prompt reply!

It's late now but I got lonely for my wifi and re-installed ndiswrapper (updated a few days ago!) which I did fairly fast, I must be getting good at this linux thing even if I haven't a clue what I'm doing half the time.

The practice makes the master :D Step by step you'll understand better what you are doing. Anyway, it is always a good idea to make a back-up of any configuration file you modify, so if something goes terribly wrong, you can just replace it.

> 
I will try again soon with madwifi and would ideally like another partition where I can mess around because I'd get a clean install.  Is there a disk defragmenter in linux?  I could re-size this partition and put another copy of ubuntu at the end on 5GB.

I don't know much about this subject. As far as I know, ext2/3 does not have the issues FAT32 or NTFS have, doesn't get as fragmented as M$ filesystems do. Of course, I might be wrong, so it would be a good idea to perform a more detailed search in the forum or the Ubuntu documetation pages.
For the moment I would tell you to have a look at [http://ubuntuforums.org/showthread.php?t=383100&highlight=defragmenter]("http://ubuntuforums.org/showthread.php?t=383100&highlight=defragmenter")

I guess you could create a new partition to experiment with, it might be a good idea. In any case, please do make back-up of your important data, accidents can happen.[/QUOTE]

> 
Without a new partition would you suggest deleting everything I search for and find of ndiswrapper?

I am not sure I understand your question. To uninstall ndiswrapper, I think it should be enough to **sudo aptitude remove ndiswrapper-utils-1.9**, perhaps the same with ndiswrapper-common, too. To completely remove also the ndiswrapper configuration files use purge instead of remove. Be careful and always read what packages aptitude / apt-get is about to remove, so that it does not take away some other important packages and ruins your system.

> I also blacklisted a (packaged?) driver or something - would that be a problem?  Should I undo that?

You might have blacklisted a driver / module, so that it is not loaded, The file you might have modified is **/etc/modprobe.d/blacklist**. It might be a problem if you blacklisted the madwifi module. Have a look at that file, them place a # in front of the line with the module, to un-blacklist it.

> Actually I can't remember if I entered some information in Interfaces either - you know how it is.

Sorry, I don't understand, what interfaces? And yeah, I do know how it is from when I was just a linux beginner, too :)

> 
I will try again over Christmas with your instructions above and I hope you might help if you can.  I'm doing this out of interest in linux more than anything.  Take care and Happy Christmas from Ireland  :mrgreen:
james

Sure, just ask, we will be happy to help! Nice to know that, after all, that is why we all are here, to share what we know and learn more about our favourite operating system.

Have a nice Christmas, too!

Xeth

---

