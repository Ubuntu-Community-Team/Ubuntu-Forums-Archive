---
title: "need help with Intel 3945ABG - connects to my network but can't access the web"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by scott pruett on 2007-08-12
I have an Intel Pro Wireless 3945ABG network adapter trying to connect over wifi - it connects to my network just fine but seemingly can't access the web.  The driver is in the restricted drivers list but active.  Any ideas of what I can do?  I searched but didn't find anything conclusive, but I also don't want to tinker with too much as I'm a Linux newb. :redface:

I'm running 7.04 on an Alienware Sentia m3450.  Dual-booting w/ WinXP, works fine in XP.

Thanks for any ideas!  I need help! :lolflag:

---

### Post by Jamie Jackson on 2007-08-12
What's the output of...

ifconfig eth0

...when you're connected?

---

### Post by scott pruett on 2007-08-12
excuse any typing errors.. couldn't copy/paste :)

thanks for your help...
> Link encap:Ethernet HWaddr 00:90:F5:53:0B:FE
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueue:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16 Base address:0xc00

---

### Post by jsgarvin on 2007-08-12
Ummm. I think Jamie meant ...

ifconfig eth1

---

### Post by scott pruett on 2007-08-12
hmm, okay... trying again:

> Link encap:Ethernet HWaddr 00:18: DE:B1:A8:05
inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::218:deff:feb1:a805/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:73 errors:0 dropped:483 overruns:0 frame:0
TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueue:1000
RX bytes:11330 (11.0 KiB) TX bytes:4102 (4.0 KiB)
Interrupt:17 Base address:0x2000 Memory:d4000000-d4000fff
this implies some data is being sent back/forth, but why can't I load squat from a browser?

okay I tried again... it's pulling data down, but VERY slowly... even Google's homepage is extremely slow (the logo is taking minutes), and there's next to nothing on it to load.

---

### Post by scott pruett on 2007-08-13
update: 15 minutes later, [www.google.com](www.google.com) still hasn't loaded.

this makes no sense to me...

---

### Post by noob12 on 2007-08-13
If you run **ifconfig eth1** again, is the dropped packet count (shown in the last ifconfig) going up from 483?  (That's not good).  Running **iwconfig** will generally show you what kind of signal you are getting and how much noise.

If you ping your router using, for example **ping -c 10 192.168.1.1** (substitute your router's address if it's not 192.168.1.1), do you see lost packets in those 10? 

If you find the situation isn't temporary, you should connect wired and submit more info for diagnostics.  Start with
```

sudo lshw -C network

iwconfig

```

---

### Post by scott pruett on 2007-08-13
> **noob12 said:**
> If you run **ifconfig eth1** again, is the dropped packet count (shown in the last ifconfig) going up from 483?  (That's not good). 
yeah... after sitting on all night:

RX packets:3963 errors:0 dropped:7482 overruns:0 frame:0
TX packets:1347 errors:0 dropped:0 overruns:0 carrier:0

> Running **iwconfig** will generally show you what kind of signal you are getting and how much noise.
lo & eth0: no connections

eth1: tx-power=15dbm, no encryption/etc, link quality=78/100, signal level=-57dbm, noise level=-58dbm

however - this works just fine running windows on the same machine, and on a powermac G5 tower right next to it (which I'm typing this on).  The router is one floor above me.

> If you ping your router using, for example **ping -c 10 192.168.1.1** (substitute your router's address if it's not 192.168.1.1), do you see lost packets in those 10? 
yeah, 40% loss.

> If you find the situation isn't temporary, you should connect wired and submit more info for diagnostics.  Start with
```

sudo lshw -C network

iwconfig

```
I'll do this a little later today.  work priorities are gonna take up a little time.

thanks for your input... I want to figure this out! :)

---

### Post by noob12 on 2007-08-13
OK.  Once you're connected wired, please paste full output from those commands, and also post the output of the command
```

dmesg

```

---

### Post by scott pruett on 2007-08-13
okay, hardwired in.  I have no idea what all this means, but thanks in advance!

ifconfig eth0 output :

> eth0      Link encap:Ethernet  HWaddr 00:90:F5:53:0B:FE  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe53:bfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1779871 (1.6 MiB)  TX bytes:226895 (221.5 KiB)
          Interrupt:16 Base address:0x2c00 


ifconfig eth1 output :

> eth1      Link encap:Ethernet  HWaddr 00:18:DE:B1:A8:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2128 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 Memory:d4000000-d4000fff 


dmesg output :

> [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1662.612 MHz processor.
[   33.274007] Built 1 zonelists.  Total pages: 257683
[   33.274013] Kernel command line: root=UUID=1c5872d5-3110-4b12-841e-6c288696dde3 ro quiet splash
[   33.274247] mapped APIC to ffffd000 (fee00000)
[   33.274251] mapped IOAPIC to ffffc000 (fec00000)
[   33.274255] Enabling fast FPU save and restore... done.
[   33.274259] Enabling unmasked SIMD FPU exception support... done.
[   33.274269] Initializing CPU#0
[   33.274357] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   33.275982] Console: colour VGA+ 80x25
[   33.276288] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   33.276708] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   33.315926] Memory: 1018400k/1038848k available (1992k kernel code, 19652k reserved, 893k data, 328k init, 121344k highmem)
[   33.315940] virtual kernel memory layout:
[   33.315942]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   33.315944]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   33.315945]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   33.315947]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   33.315949]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   33.315951]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   33.315953]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   33.315958] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.316169] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   33.316178] hpet0: 3 64-bit timers, 14318180 Hz
[   33.317184] Using HPET for base-timer
[   33.396051] Calibrating delay using timer specific routine.. 3329.35 BogoMIPS (lpj=6658708)
[   33.396107] Security Framework v1.0.0 initialized
[   33.396113] SELinux:  Disabled at boot.
[   33.396135] Mount-cache hash table entries: 512
[   33.396308] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   33.396321] monitor/mwait feature present.
[   33.396323] using mwait in idle threads.
[   33.396329] CPU: L1 I cache: 32K, L1 D cache: 32K
[   33.396333] CPU: L2 cache: 2048K
[   33.396337] CPU: Physical Processor ID: 0
[   33.396340] CPU: Processor Core ID: 0
[   33.396343] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   33.396356] Compat vDSO mapped to ffffe000.
[   33.396362] Remapping vsyscall page to ffffe000
[   33.396379] Checking 'hlt' instruction... OK.
[   33.412166] SMP alternatives: switching to UP code
[   33.412658] Early unpacking initramfs... done
[   33.959334] ACPI: Core revision 20060707
[   33.959682] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   33.989449] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   33.989475] SMP alternatives: switching to SMP code
[   33.989576] Booting processor 1/1 eip 3000
[   34.000134] Initializing CPU#1
[   34.079008] Calibrating delay using timer specific routine.. 3325.10 BogoMIPS (lpj=6650215)
[   34.079018] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   34.079027] monitor/mwait feature present.
[   34.079032] CPU: L1 I cache: 32K, L1 D cache: 32K
[   34.079035] CPU: L2 cache: 2048K
[   34.079038] CPU: Physical Processor ID: 0
[   34.079040] CPU: Processor Core ID: 1
[   34.079043] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   34.079784] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   34.079816] Total of 2 processors activated (6654.46 BogoMIPS).
[   34.080018] ENABLING IO-APIC IRQs
[   34.080238] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   34.298678] checking TSC synchronization across 2 CPUs: passed.
[    0.003988] Brought up 2 CPUs
[    0.195758] migration_cost=77
[    0.196155] Booting paravirtualized kernel on bare hardware
[    0.196270] Time: 20:30:53  Date: 07/13/107
[    0.196310] NET: Registered protocol family 16
[    0.196427] EISA bus registered
[    0.196434] ACPI: bus type pci registered
[    0.196575] PCI: PCI BIOS revision 2.10 entry at 0xfd7f3, last bus=5
[    0.196578] PCI: Using configuration type 1
[    0.196581] Setting up standard PCI resources
[    0.203510] ACPI: Interpreter enabled
[    0.203514] ACPI: Using IOAPIC for interrupt routing
[    0.204607] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.204615] PCI: Probing PCI hardware (bus 00)
[    0.205949] Boot video device is 0000:00:02.0
[    0.206739] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.206745] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.208085] PCI: Transparent bridge - 0000:00:1e.0
[    0.208185] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#05) (try 'pci=assign-busses')
[    0.208190] Please report the result to linux-kernel to fix this permanently
[    0.208257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.215705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.216126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.218662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.221635] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.222027] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.222420] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.222808] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.223192] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.223575] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.223975] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.224359] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.226399] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.226413] pnp: PnP ACPI init
[    0.229527] pnp: PnP ACPI: found 11 devices
[    0.229536] PnPBIOS: Disabled by ACPI PNP
[    0.229602] PCI: Using ACPI for IRQ routing
[    0.229607] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.253280] NET: Registered protocol family 8
[    0.253284] NET: Registered protocol family 20
[    0.253591] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.253596] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.254037] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.254045] PCI: Bridge: 0000:00:1c.0
[    0.254050]   IO window: 2000-2fff
[    0.254058]   MEM window: d4000000-d5ffffff
[    0.254065]   PREFETCH window: d0000000-d1ffffff
[    0.254073] PCI: Bridge: 0000:00:1c.1
[    0.254077]   IO window: 3000-3fff
[    0.254086]   MEM window: d6000000-d7ffffff
[    0.254092]   PREFETCH window: d2000000-d3ffffff
[    0.254110] PCI: Bus 6, cardbus bridge: 0000:05:07.0
[    0.254114]   IO window: 00004400-000044ff
[    0.254121]   IO window: 00004800-000048ff
[    0.254128]   PREFETCH window: 50000000-53ffffff
[    0.254135]   MEM window: 58000000-5bffffff
[    0.254142] PCI: Bridge: 0000:00:1e.0
[    0.254147]   IO window: 4000-4fff
[    0.254175]   MEM window: d8000000-d80fffff
[    0.254182]   PREFETCH window: 50000000-55ffffff
[    0.254220] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.254230] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.254261] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    0.254270] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.254285] PCI: Enabling device 0000:00:1e.0 (0104 -> 0107)
[    0.254293] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.254316] ACPI: PCI Interrupt 0000:05:07.0[A] -> GSI 16 (level, low) -> IRQ 17
[    0.254325] PCI: Setting latency timer of device 0000:05:07.0 to 64
[    0.254366] NET: Registered protocol family 2
[    0.322916] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.323058] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.323708] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.324048] TCP: Hash tables configured (established 131072 bind 65536)
[    0.324052] TCP reno registered
[    0.343644] checking if image is initramfs... it is
[    1.422498] Freeing initrd memory: 7001k freed
[    1.422741] Simple Boot Flag at 0x36 set to 0x1
[    1.423429] audit: initializing netlink socket (disabled)
[    1.423452] audit(1187037054.396:1): initialized
[    1.423588] highmem bounce pool size: 64 pages
[    1.423706] VFS: Disk quotas dquot_6.5.1
[    1.423733] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.423801] io scheduler noop registered
[    1.423805] io scheduler anticipatory registered
[    1.423808] io scheduler deadline registered
[    1.423826] io scheduler cfq registered (default)
[    1.424162] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.424236] assign_interrupt_mode Found MSI capability
[    1.424240] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.424300] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.424468] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.424540] assign_interrupt_mode Found MSI capability
[    1.424544] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.424599] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.424854] isapnp: Scanning for PnP cards...
[    1.778532] isapnp: No Plug & Play device found
[    1.811457] Real Time Clock Driver v1.12ac
[    1.811761] hpet_resources: 0xfed00000 is busy
[    1.811784] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.812750] mice: PS/2 mouse device common for all mice
[    1.814031] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.814244] input: Macintosh mouse button emulation as /class/input/input0
[    1.814297] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.814302] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.814653] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.816550] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.817779] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.817786] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.817790] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.817794] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.817798] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.817934] EISA: Probing bus 0 at eisa.0
[    1.817943] Cannot allocate resource for EISA slot 1
[    1.817948] Cannot allocate resource for EISA slot 2
[    1.817952] Cannot allocate resource for EISA slot 3
[    1.817955] Cannot allocate resource for EISA slot 4
[    1.817980] EISA: Detected 0 cards.
[    1.845049] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.848062] TCP cubic registered
[    1.848073] NET: Registered protocol family 1
[    1.848103] Starting balanced_irq
[    1.848112] Using IPI No-Shortcut mode
[    1.848246] ACPI: (supports S0 S3 S4 S5)
[    1.848312]   Magic number: 3:588:548
[    1.848601] Freeing unused kernel memory: 328k freed
[    1.849176] Time: tsc clocksource has been installed.
[    3.183709] Capability LSM initialized
[    3.246287] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.246660] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.247461] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.247469] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.248233] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.248545] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.248989] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.248997] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.251309] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[    4.044000] ACPI: Thermal Zone [THRM] (33 C)
[    4.052000] Time: hpet clocksource has been installed.
[    4.580000] usbcore: registered new interface driver usbfs
[    4.580000] usbcore: registered new interface driver hub
[    4.580000] usbcore: registered new device driver usb
[    4.580000] USB Universal Host Controller Interface driver v3.0
[    4.580000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[    4.580000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.580000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.580000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.580000] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820
[    4.580000] usb usb1: configuration #1 chosen from 1 choice
[    4.580000] hub 1-0:1.0: USB hub found
[    4.580000] hub 1-0:1.0: 2 ports detected
[    4.600000] SCSI subsystem initialized
[    4.608000] libata version 2.20 loaded.
[    4.684000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    4.684000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.684000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.684000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.684000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    4.684000] usb usb2: configuration #1 chosen from 1 choice
[    4.684000] hub 2-0:1.0: USB hub found
[    4.684000] hub 2-0:1.0: 2 ports detected
[    4.716000] ieee1394: Initialized config rom entry `ip1394'
[    4.788000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    4.788000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.788000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.788000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.788000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[    4.788000] usb usb3: configuration #1 chosen from 1 choice
[    4.788000] hub 3-0:1.0: USB hub found
[    4.788000] hub 3-0:1.0: 2 ports detected
[    4.892000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    4.892000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.892000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.892000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.892000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    4.892000] usb usb4: configuration #1 chosen from 1 choice
[    4.892000] hub 4-0:1.0: USB hub found
[    4.892000] hub 4-0:1.0: 2 ports detected
[    4.996000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    4.996000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.996000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.996000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.996000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.996000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.996000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd8444000
[    5.000000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.000000] usb usb5: configuration #1 chosen from 1 choice
[    5.000000] hub 5-0:1.0: USB hub found
[    5.000000] hub 5-0:1.0: 8 ports detected
[    5.104000] ata_piix 0000:00:1f.1: version 2.10ac1
[    5.104000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[    5.104000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    5.104000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    5.104000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    5.104000] scsi0 : ata_piix
[    5.396000] usb 5-7: new high speed USB device using ehci_hcd and address 2
[    5.424000] ata1.00: ATAPI, max UDMA/33
[    5.536000] usb 5-7: configuration #1 chosen from 1 choice
[    5.588000] ata1.00: configured for UDMA/33
[    5.588000] scsi1 : ata_piix
[    5.588000] ata2: port disabled. ignoring.
[    5.588000] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-5540A  1.J0 PQ: 0 ANSI: 5
[    5.588000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    5.588000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    5.744000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    5.744000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.744000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 19
[    5.744000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 19
[    5.744000] scsi2 : ata_piix
[    5.908000] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.908000] ata3.00: ATA-7: ST98823AS, 3.03, max UDMA/133
[    5.908000] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.920000] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.920000] ata3.00: configured for UDMA/133
[    5.920000] scsi3 : ata_piix
[    6.084000] ATA: abnormal status 0x7F on port 0x000118cf
[    6.084000] scsi 2:0:0:0: Direct-Access     ATA      ST98823AS        3.03 PQ: 0 ANSI: 5
[    6.088000] ACPI: PCI Interrupt 0000:05:07.1[A] -> GSI 16 (level, low) -> IRQ 17
[    6.136000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d8005000-d80057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.140000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    6.140000] ACPI: PCI Interrupt 0000:05:0b.0[A] -> GSI 17 (level, low) -> IRQ 16
[    6.140000] eth0: RTL8169sb/8110sb at 0xf8862c00, 00:90:f5:53:0b:fe, IRQ 16
[    6.156000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.156000] sda: Write Protect is off
[    6.156000] sda: Mode Sense: 00 3a 00 00
[    6.156000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.156000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.156000] sda: Write Protect is off
[    6.156000] sda: Mode Sense: 00 3a 00 00
[    6.156000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.156000]  sda:sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.156000] Uniform CD-ROM driver Revision: 3.20
[    6.156000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.236000]  sda1 sda2 sda3 < sda5 >
[    6.260000] sd 2:0:0:0: Attached scsi disk sda
[    6.268000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    6.268000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.560000] Attempting manual resume
[    6.560000] swsusp: Resume From Partition 8:5
[    6.560000] PM: Checking swsusp image.
[    6.560000] PM: Resume from disk failed.
[    6.608000] kjournald starting.  Commit interval 5 seconds
[    6.608000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.488000] r8169: eth0: link up
[   18.560000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.564000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.664000] NET: Registered protocol family 17
[   18.976000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.984000] agpgart: Detected an Intel 945GM Chipset.
[   18.984000] agpgart: Detected 7932K stolen memory.
[   19.004000] agpgart: AGP aperture is 256M @ 0xc0000000
[   19.368000] iTCO_vendor_support: vendor-support=0
[   19.368000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   19.384000] Yenta: CardBus bridge found at 0000:05:07.0 [1558:5405]
[   19.384000] Yenta: Enabling burst memory read transactions
[   19.384000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.384000] Yenta: Routing CardBus interrupts to PCI
[   19.384000] Yenta TI: socket 0000:05:07.0, mfunc 0x00081b22, devctl 0x64
[   19.416000] ieee80211_crypt: registered algorithm 'NULL'
[   19.428000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.428000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.496000] sdhci: Secure Digital Host Controller Interface driver
[   19.496000] sdhci: Copyright(c) Pierre Ossman
[   19.524000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   19.524000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.624000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   19.624000] Socket status: 30000006
[   19.624000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   19.624000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   19.624000] cs: IO port probe 0x4000-0x4fff: clean.
[   19.624000] pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xd80fffff
[   19.624000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x55ffffff
[   19.660000] ACPI: PCI Interrupt 0000:05:07.2[A] -> GSI 16 (level, low) -> IRQ 17
[   19.660000] sdhci: SDHCI controller found at 0000:05:07.3 [104c:803c] (rev 0)
[   19.660000] ACPI: PCI Interrupt 0000:05:07.3[A] -> GSI 16 (level, low) -> IRQ 17
[   19.660000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[   19.660000] mmc0: SDHCI at 0xd8005800 irq 17 DMA
[   19.664000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   19.664000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.672000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   19.672000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   19.672000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.828000] intel_rng: FWH not detected
[   19.904000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   19.904000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.960000] cs: IO port probe 0x100-0x3af: clean.
[   19.964000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.964000] cs: IO port probe 0x820-0x8ff: clean.
[   19.964000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.964000] cs: IO port probe 0xa00-0xaff: clean.
[   20.092000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   20.592000] fuse init (API version 7.8)
[   20.660000] lp: driver loaded but no devices found
[   20.728000] Adding 1542200k swap on /dev/disk/by-uuid/1cd8592a-07d9-4326-9f5d-fe375d93bb35.  Priority:-1 extents:1 across:1542200k
[   20.864000] EXT3 FS on sda2, internal journal
[   21.488000] hda_intel: azx_get_response timeout, switching to polling mode...
[   21.644000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   21.684000] NET: Registered protocol family 10
[   21.684000] lo: Disabled Privacy Extensions
[   22.184000] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[   32.604000] eth0: no IPv6 routers present
[   79.020000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   83.692000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   83.756000] ibm_acpi: ec object not found
[   83.800000] Using specific hotkey driver
[   83.852000] No dock devices found.
[   83.868000] ACPI: Battery Slot [BAT0] (battery present)
[   83.892000] input: Power Button (FF) as /class/input/input3
[   83.892000] ACPI: Power Button (FF) [PWRF]
[   83.892000] input: Power Button (CM) as /class/input/input4
[   83.892000] ACPI: Power Button (CM) [PWB]
[   83.892000] input: Sleep Button (CM) as /class/input/input5
[   83.892000] ACPI: Sleep Button (CM) [SLPB]
[   83.892000] input: Lid Switch as /class/input/input6
[   83.892000] ACPI: Lid Switch [LID]
[   84.200000] ACPI: AC Adapter [AC] (on-line)
[   84.280000] pcc_acpi: loading...
[   89.280000] mtrr: no more MTRRs available
[   90.112000] ppdev: user-space parallel port driver
[   90.872000] apm: BIOS not found.
[   91.168000] Bluetooth: Core ver 2.11
[   91.168000] NET: Registered protocol family 31
[   91.168000] Bluetooth: HCI device and connection manager initialized
[   91.168000] Bluetooth: HCI socket layer initialized
[   91.192000] Bluetooth: L2CAP ver 2.8
[   91.192000] Bluetooth: L2CAP socket layer initialized
[   91.332000] Bluetooth: RFCOMM socket layer initialized
[   91.332000] Bluetooth: RFCOMM TTY layer initialized
[   91.332000] Bluetooth: RFCOMM ver 1.8
[   92.184000] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[  105.512000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  105.516000] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  105.728000] NTFS volume version 3.1.
[  106.964000] eth0: no IPv6 routers present


---

### Post by noob12 on 2007-08-13
Need these too
```

lspci -nn

sudo lshw -C network

iwconfig

iwlist scan

```

---

### Post by scott pruett on 2007-08-13
> **noob12 said:**
> 
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
05:07.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
05:07.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
05:07.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
05:07.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
05:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)


> sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:b1:a8:05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:d4000000-d4000fff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@05:0b.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:53:0b:fe
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.102 latency=160 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:4000-40ff iomemory:d8005c00-d8005cff irq:16


> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3309   Missed beacon:0

> iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:06:25:61:03:78
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=99/100  Signal level=-23 dBm  Noise level=-23 dBm
                    Extra: Last beacon: 216ms ago

---

### Post by noob12 on 2007-08-13
I'm seeing some potential PCI issues in the boot, but I'd like to see your **iwconfig** output while you're connected to wireless.

---

### Post by scott pruett on 2007-08-13
thanks... I'll tell you soon, but I've been trying to fix two issues at once & somehow disabled my xserver.  I need to get that fixed first...

[http://ubuntuforums.org/showthread.php?t=524155&page=2](http://ubuntuforums.org/showthread.php?t=524155&page=2)

ugh...

---

### Post by scott pruett on 2007-08-14
> **noob12 said:**
> I'm seeing some potential PCI issues in the boot, but I'd like to see your **iwconfig** output while you're connected to wireless.
thanks!  laptop is within a few feet of access point w/ this output.

---------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:61:03:78   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=99/100  Signal level=-24 dBm  Noise level=-25 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:216   Missed beacon:0

---

### Post by noob12 on 2007-08-14
And is packet loss the same in this ideal condition? or did it go away when you placed it here?

I noticed in your other thread you were mentioning that you were about to reinstall Ubuntu due to your xserver issues.  Did you do that?

If so, can I see a current **dmesg**?  Earlier I had noticed some bus assignment issues, and notes from the kernel about them.   I want to see if they're still there or if this has changed.  If the issues are still there, I'm going to recommend you boot with some boot flags and see if this improves the PCI and IRQ routing, which I am suspecting is connected to your wireless dropping received packets.  I didn't read your xserver posting carefully but If you are having problems at the video device level, they might be related to this (then again might not).

---

### Post by scott pruett on 2007-08-16
Thanks noob.  I've been busy with work stuff, but I'll post up again when I get back into Ubuntu (later tonight?).  I haven't done a reinstall yet, but intend to...

---

### Post by lode on 2007-09-17
I'm bumping this thread because I seam to have the same problem, and I (so far) didn't found another (more recent) thread concerning this issue.

I do have wireless internet, and I am connected to my acces point, but the connection is many times slower than a wired connection (10 kb/s download speed versus 1 mb/s download speed). Furthermore I get many time outs from websites when I'm trying to browse the net. Since everything works when I'm connected on the wired network, I don't think it's an ipv6 or DNS issue (I have followed the usual workarounds for those two -- more common -- issues however). I also resetted my router to factory defaults (ssid: linksys, no security whatsoever).

I currently am connected to my acces point, typing this post. I immedeatly incorporated some of the terminal answers (see below) that noob12 requested for scot pruett. I must admit that I'm currently running a (fully patched) Gutsy Gibbon install (because I've got a fairly new laptop, and the [internet]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61") recommended to do so. The wireless network card is the same as scott pruett's (IPW 3945).

Feedback for sudo lshw -C network:

```
 *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:ce:7c:60
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:8f:9d:cd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.105 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b

```

Feedback for iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:41:BF:B0:19   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-41 dBm  Noise level=-42 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9495   Missed beacon:0

```

For iwlist scan (I'm located about 10 meters away from the router):

```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:BF:B0:19
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=87/100  Signal level=-46 dBm  Noise level=-46 dBm
                    Extra: Last beacon: 88ms ago

```

For lspci -nn:

```

00:00.0 Host bridge [0600]: Intel Corporation Mobile Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile Integrated Graphics Controller [8086:2a03] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile LPC Interface Controller [8086:2811] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation Mobile IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation Mobile SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832] (rev 04)
15:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
15:00.3 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 11)
15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)
15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)

```

For ifconfig (don't know why eth1 (my wireless device) is supposed to be an ethernet interface... I was browsing the net via the wired network a few minutes ago, so maybe that has something to do with it...):

```

eth0      Link encap:Ethernet  HWaddr 00:1A:6B:CE:7C:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1312737 (1.2 MB)  TX bytes:261771 (255.6 KB)
          Base address:0x1840 Memory:fe000000-fe020000 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:8F:9D:CD  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9888 errors:0 dropped:9832 overruns:0 frame:0
          TX packets:11122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8049537 (7.6 MB)  TX bytes:1317268 (1.2 MB)
          Interrupt:21 Base address:0x2000 Memory:df3ff000-df3fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1168 (1.1 KB)  TX bytes:1168 (1.1 KB)

```

For dmesg (that's a whole lot of text/code :)):

```

[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.644000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[    0.644000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: Power Resource [PUBS] (on)
[    0.644000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.644000] pnp: PnP ACPI init
[    0.644000] ACPI: bus type pnp registered
[    0.648000] pnp: PnP ACPI: found 11 devices
[    0.648000] ACPI: ACPI bus type pnp unregistered
[    0.648000] PnPBIOS: Disabled by ACPI PNP
[    0.648000] PCI: Using ACPI for IRQ routing
[    0.648000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.804000] NET: Registered protocol family 8
[    0.804000] NET: Registered protocol family 20
[    0.804000] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.804000] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.804000] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.804000] pnp: 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.804000] pnp: 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.804000] pnp: 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.804000] pnp: 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.804000] pnp: 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.808000] Time: hpet clocksource has been installed.
[    0.808000] Switched to high resolution mode on CPU 0
[    0.808000] Switched to high resolution mode on CPU 1
[    0.836000] PCI: Bridge: 0000:00:1c.0
[    0.836000]   IO window: 2000-2fff
[    0.836000]   MEM window: fc000000-fdffffff
[    0.836000]   PREFETCH window: f8000000-f80fffff
[    0.836000] PCI: Bridge: 0000:00:1c.1
[    0.836000]   IO window: 3000-3fff
[    0.836000]   MEM window: dc000000-df3fffff
[    0.836000]   PREFETCH window: dfe00000-dfefffff
[    0.836000] PCI: Bridge: 0000:00:1c.2
[    0.836000]   IO window: 4000-4fff
[    0.836000]   MEM window: d8000000-d9ffffff
[    0.836000]   PREFETCH window: dfb00000-dfbfffff
[    0.836000] PCI: Bridge: 0000:00:1c.3
[    0.836000]   IO window: 5000-5fff
[    0.836000]   MEM window: d4000000-d5ffffff
[    0.836000]   PREFETCH window: df800000-df8fffff
[    0.836000] PCI: Bridge: 0000:00:1c.4
[    0.836000]   IO window: 6000-6fff
[    0.836000]   MEM window: d0000000-d1ffffff
[    0.836000]   PREFETCH window: df500000-df5fffff
[    0.836000] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[    0.836000]   IO window: 00007000-000070ff
[    0.836000]   IO window: 00007400-000074ff
[    0.836000]   PREFETCH window: f4000000-f7ffffff
[    0.836000]   MEM window: 80000000-83ffffff
[    0.836000] PCI: Bridge: 0000:00:1e.0
[    0.836000]   IO window: 7000-afff
[    0.836000]   MEM window: f8300000-fbffffff
[    0.836000]   PREFETCH window: f4000000-f7ffffff
[    0.836000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[    0.836000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.836000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[    0.836000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.836000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[    0.836000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.836000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 19
[    0.836000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.836000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 20 (level, low) -> IRQ 16
[    0.836000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.836000] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    0.836000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.836000] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[    0.836000] PCI: Setting latency timer of device 0000:15:00.0 to 64
[    0.836000] NET: Registered protocol family 2
[    0.884000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.884000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.884000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.884000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.884000] TCP reno registered
[    0.900000] checking if image is initramfs... it is
[    1.392000] Freeing initrd memory: 7021k freed
[    1.392000] Simple Boot Flag at 0x35 set to 0x1
[    1.392000] audit: initializing netlink socket (disabled)
[    1.392000] audit(1190044674.308:1): initialized
[    1.392000] highmem bounce pool size: 64 pages
[    1.392000] VFS: Disk quotas dquot_6.5.1
[    1.392000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.392000] io scheduler noop registered
[    1.392000] io scheduler anticipatory registered
[    1.392000] io scheduler deadline registered
[    1.392000] io scheduler cfq registered (default)
[    1.392000] Boot video device is 0000:00:02.0
[    1.392000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.392000] assign_interrupt_mode Found MSI capability
[    1.392000] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.392000] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.392000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.392000] assign_interrupt_mode Found MSI capability
[    1.392000] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.392000] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.392000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.392000] assign_interrupt_mode Found MSI capability
[    1.396000] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.396000] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.396000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    1.396000] assign_interrupt_mode Found MSI capability
[    1.396000] Allocate Port Service[0000:00:1c.3:pcie00]
[    1.396000] Allocate Port Service[0000:00:1c.3:pcie02]
[    1.396000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    1.396000] assign_interrupt_mode Found MSI capability
[    1.396000] Allocate Port Service[0000:00:1c.4:pcie00]
[    1.396000] Allocate Port Service[0000:00:1c.4:pcie02]
[    1.396000] isapnp: Scanning for PnP cards...
[    1.752000] isapnp: No Plug & Play device found
[    1.768000] Real Time Clock Driver v1.12ac
[    1.768000] hpet_resources: 0xfed00000 is busy
[    1.768000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.772000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.772000] input: Macintosh mouse button emulation as /class/input/input0
[    1.772000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.780000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.780000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.780000] mice: PS/2 mouse device common for all mice
[    1.780000] EISA: Probing bus 0 at eisa.0
[    1.780000] Cannot allocate resource for EISA slot 1
[    1.780000] Cannot allocate resource for EISA slot 2
[    1.780000] Cannot allocate resource for EISA slot 3
[    1.780000] Cannot allocate resource for EISA slot 4
[    1.780000] Cannot allocate resource for EISA slot 5
[    1.780000] Cannot allocate resource for EISA slot 6
[    1.780000] Cannot allocate resource for EISA slot 7
[    1.780000] Cannot allocate resource for EISA slot 8
[    1.780000] EISA: Detected 0 cards.
[    1.780000] TCP cubic registered
[    1.780000] NET: Registered protocol family 1
[    1.780000] Using IPI No-Shortcut mode
[    1.780000]   Magic number: 7:329:993
[    1.780000]   hash matches device ttyd6
[    1.780000] Freeing unused kernel memory: 364k freed
[    1.792000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.940000] AppArmor: AppArmor initialized<5>audit(1190044675.808:2):  info="AppArmor initialized" pid=1253
[    2.948000] fuse init (API version 7.8)
[    2.952000] Failure registering capabilities with primary security module.
[    2.984000] ACPI: SSDT 7D6E1D72, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[    2.984000] ACPI: SSDT 7D6E20BB, 061E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[    2.988000] Monitor-Mwait will be used to enter C-1 state
[    2.988000] Monitor-Mwait will be used to enter C-2 state
[    2.988000] Monitor-Mwait will be used to enter C-3 state
[    2.988000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.988000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.988000] ACPI: SSDT 7D6E1CAA, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[    2.988000] ACPI: SSDT 7D6E2036, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[    2.988000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.988000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.988000] ACPI: Thermal Zone [THM0] (58 C)
[    2.992000] ACPI: Thermal Zone [THM1] (54 C)
[    3.320000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    3.320000] Copyright (c) 1999-2006 Intel Corporation.
[    3.320000] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 16
[    3.320000] PCI: Setting latency timer of device 0000:00:19.0 to 64
[    3.328000] usbcore: registered new interface driver usbfs
[    3.328000] usbcore: registered new interface driver hub
[    3.328000] usbcore: registered new device driver usb
[    3.328000] USB Universal Host Controller Interface driver v3.0
[    3.384000] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:6b:ce:7c:60
[    3.408000] SCSI subsystem initialized
[    3.412000] libata version 2.21 loaded.
[    3.508000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.508000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 16
[    3.508000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.508000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.508000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.508000] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001860
[    3.508000] usb usb1: configuration #1 chosen from 1 choice
[    3.508000] hub 1-0:1.0: USB hub found
[    3.508000] hub 1-0:1.0: 2 ports detected
[    3.612000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 17
[    3.612000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.612000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.612000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.612000] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00001880
[    3.612000] usb usb2: configuration #1 chosen from 1 choice
[    3.612000] hub 2-0:1.0: USB hub found
[    3.612000] hub 2-0:1.0: 2 ports detected
[    3.716000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 20
[    3.716000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.716000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.716000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.716000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000018a0
[    3.716000] usb usb3: configuration #1 chosen from 1 choice
[    3.716000] hub 3-0:1.0: USB hub found
[    3.716000] hub 3-0:1.0: 2 ports detected
[    3.820000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[    3.820000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.820000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.820000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.820000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000018c0
[    3.820000] usb usb4: configuration #1 chosen from 1 choice
[    3.820000] hub 4-0:1.0: USB hub found
[    3.820000] hub 4-0:1.0: 2 ports detected
[    3.852000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.924000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[    3.924000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.924000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.924000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.924000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018e0
[    3.924000] usb usb5: configuration #1 chosen from 1 choice
[    3.924000] hub 5-0:1.0: USB hub found
[    3.924000] hub 5-0:1.0: 2 ports detected
[    4.000000] Clocksource tsc unstable (delta = -465965034 ns)
[    4.028000] usb 1-2: configuration #1 chosen from 1 choice
[    4.028000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 18
[    4.028000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    4.028000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.028000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    4.028000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    4.028000] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe226c00
[    4.032000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.032000] usb usb6: configuration #1 chosen from 1 choice
[    4.032000] hub 6-0:1.0: USB hub found
[    4.032000] hub 6-0:1.0: 4 ports detected
[    4.116000] usb 1-2: USB disconnect, address 2
[    4.140000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[    4.140000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.140000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.140000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    4.140000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.140000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.140000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe227000
[    4.144000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.144000] usb usb7: configuration #1 chosen from 1 choice
[    4.144000] hub 7-0:1.0: USB hub found
[    4.144000] hub 7-0:1.0: 6 ports detected
[    4.248000] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[    4.248000] PCI: Setting latency timer of device 0000:15:00.1 to 64
[    4.300000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.304000] ata_piix 0000:00:1f.1: version 2.11
[    4.304000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 20
[    4.304000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.304000] scsi0 : ata_piix
[    4.304000] scsi1 : ata_piix
[    4.304000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011c00 irq 14
[    4.304000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011c08 irq 15
[    4.624000] ata1.00: ATAPI: MATSHITADVD-RAM UJ-852, RB01, max UDMA/33
[    4.796000] ata1.00: configured for UDMA/33
[    4.796000] ata2: port disabled. ignoring.
[    4.796000] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-852   RB01 PQ: 0 ANSI: 5
[    4.796000] ahci 0000:00:1f.2: version 2.2
[    4.796000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 20
[    4.796000] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match
[    4.808000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.808000] Uniform CD-ROM driver Revision: 3.20
[    4.808000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.812000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.864000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    5.040000] usb 1-2: configuration #1 chosen from 1 choice
[    5.576000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a133afc]
[    7.736000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
[    7.736000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    7.736000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    7.736000] scsi2 : ahci
[    7.740000] ata3: SATA max UDMA/133 cmd 0xf88a6100 ctl 0x00000000 bmdma 0x00000000 irq 218
[    8.228000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.228000] ata3.00: ATA-7: HTS721060G9SA00, MC3IC14V, max UDMA/100
[    8.228000] ata3.00: 117210240 sectors, multi 16: LBA48 
[    8.228000] ata3.00: configured for UDMA/100
[    8.228000] scsi 2:0:0:0: Direct-Access     ATA      HTS721060G9SA00  MC3I PQ: 0 ANSI: 5
[    8.228000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    8.232000] sd 2:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    8.232000] sd 2:0:0:0: [sda] Write Protect is off
[    8.232000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.232000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.232000] sd 2:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    8.232000] sd 2:0:0:0: [sda] Write Protect is off
[    8.232000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.232000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.232000]  sda: sda1 sda2 sda3
[    8.592000] sd 2:0:0:0: [sda] Attached SCSI disk
[    8.812000] Attempting manual resume
[    8.812000] swsusp: Resume From Partition 8:3
[    8.812000] PM: Checking swsusp image.
[    8.812000] PM: Resume from disk failed.
[   17.364000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.384000] Netfilter messages via NETLINK v0.30.
[   17.388000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   18.188000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.252000] agpgart: Detected an Intel 965GM Chipset.
[   18.252000] agpgart: Detected 7676K stolen memory.
[   18.264000] agpgart: AGP aperture is 256M @ 0xe0000000
[   18.348000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.368000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.660000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   18.724000] input: PC Speaker as /class/input/input2
[   18.748000] sdhci: Secure Digital Host Controller Interface driver
[   18.748000] sdhci: Copyright(c) Pierre Ossman
[   18.768000] ieee80211_crypt: registered algorithm 'NULL'
[   18.768000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.768000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.788000] Yenta: ISA IRQ mask 0x04b8, PCI irq 20
[   18.788000] Socket status: 30000006
[   18.788000] pcmcia: parent PCI bridge I/O window: 0x7000 - 0xafff
[   18.788000] cs: IO port probe 0x7000-0xafff: clean.
[   18.788000] pcmcia: parent PCI bridge Memory window: 0xf8300000 - 0xfbffffff
[   18.788000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   18.788000] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
[   18.788000] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   18.788000] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   18.788000] mmc0: SDHCI at 0xf8301800 irq 22 DMA
[   18.836000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   18.836000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   18.836000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   18.836000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   18.836000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.020000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   19.020000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.184000] cs: IO port probe 0x100-0x3af: clean.
[   19.188000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.188000] cs: IO port probe 0x820-0x8ff: clean.
[   19.188000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.188000] cs: IO port probe 0xa00-0xaff: clean.
[   19.284000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   19.284000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   19.328000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   19.584000] lp: driver loaded but no devices found
[   19.656000] Adding 522104k swap on /dev/sda3.  Priority:-1 extents:1 across:522104k
[   20.712000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   24.704000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   24.924000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   24.972000] ACPI: AC Adapter [AC] (on-line)
[   25.008000] ACPI: Battery Slot [BAT0] (battery present)
[   25.028000] ACPI: ACPI Dock Station Driver 
[   25.028000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   25.028000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   25.028000] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   25.040000] input: Power Button (FF) as /class/input/input5
[   25.040000] ACPI: Power Button (FF) [PWRF]
[   25.040000] input: Lid Switch as /class/input/input6
[   25.040000] ACPI: Lid Switch [LID]
[   25.040000] input: Sleep Button (CM) as /class/input/input7
[   25.040000] ACPI: Sleep Button (CM) [SLPB]
[   25.140000] set_level status: 0
[   25.140000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.140000] set_level status: 0
[   25.140000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   26.472000] ppdev: user-space parallel port driver
[   26.924000] audit(1190037500.360:3): operation="file_mmap" requested_mask="mr" denied_mask="m" name="/etc/passwd" pid=5127 profile="/usr/sbin/cupsd"
[   26.924000] audit(1190037500.360:4): operation="file_mmap" requested_mask="mr" denied_mask="m" name="/etc/group" pid=5127 profile="/usr/sbin/cupsd"
[   26.924000] audit(1190037500.360:5): operation="file_mmap" requested_mask="mr" denied_mask="m" name="/etc/group" pid=5127 profile="/usr/sbin/cupsd"
[   27.048000] audit(1190037500.360:6): operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5127 profile="/usr/sbin/cupsd"
[   27.144000] apm: BIOS not found.
[   27.276000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   27.276000] thinkpad_acpi: http://ibm-acpi.sf.net/
[   27.276000] thinkpad_acpi: ThinkPad EC firmware 7KHT22WW-1.06
[   27.320000] Non-volatile memory driver v1.2
[   27.336000] input: thinkpad-keys as /class/input/input8
[   27.596000] Failure registering capabilities with primary security module.
[   27.852000] Bluetooth: Core ver 2.11
[   27.852000] NET: Registered protocol family 31
[   27.852000] Bluetooth: HCI device and connection manager initialized
[   27.852000] Bluetooth: HCI socket layer initialized
[   27.896000] Bluetooth: L2CAP ver 2.8
[   27.896000] Bluetooth: L2CAP socket layer initialized
[   28.160000] Bluetooth: RFCOMM socket layer initialized
[   28.160000] Bluetooth: RFCOMM TTY layer initialized
[   28.160000] Bluetooth: RFCOMM ver 1.8
[   32.584000] [drm] Initialized drm 1.1.0 20060810
[   32.588000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   32.588000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   77.932000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   77.932000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   80.512000] NET: Registered protocol family 17
[   86.104000] e1000: eth0: e1000_watchdog: NIC Link is Down
[  238.184000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  238.184000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  250.824000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[  273.132000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  273.132000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  276.788000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  276.788000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  279.472000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  279.472000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  317.172000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  317.172000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  321.832000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  321.832000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  333.732000] audit(1190037806.877:7): operation="file_mmap" requested_mask="mr" denied_mask="m" name="/etc/passwd" pid=5127 profile="/usr/sbin/cupsd"
[  333.732000] audit(1190037806.877:8): operation="file_mmap" requested_mask="mr" denied_mask="m" name="/etc/group" pid=5127 profile="/usr/sbin/cupsd"
[  333.732000] audit(1190037806.877:9): operation="file_mmap" requested_mask="mr" denied_mask="m" name="/etc/group" pid=5127 profile="/usr/sbin/cupsd"
[  666.588000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  666.588000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  666.588000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 1909.528000] e1000: eth0: e1000_watchdog: NIC Link is Down
[ 2369.052000] Inbound IN=eth1 OUT= MAC=00:1b:77:8f:9d:cd:00:0c:41:bf:b0:19:08:00 SRC=134.184.129.2 DST=192.168.1.105 LEN=1500 TOS=0x00 PREC=0x00 TTL=53 ID=1418 DF PROTO=TCP SPT=80 DPT=60204 WINDOW=49640 RES=0x00 ACK URGP=0 
[ 2429.040000] Inbound IN=eth1 OUT= MAC=00:1b:77:8f:9d:cd:00:0c:41:bf:b0:19:08:00 SRC=134.184.129.2 DST=192.168.1.105 LEN=1500 TOS=0x00 PREC=0x00 TTL=53 ID=49763 DF PROTO=TCP SPT=80 DPT=60204 WINDOW=49640 RES=0x00 ACK URGP=0 
[ 2489.052000] Inbound IN=eth1 OUT= MAC=00:1b:77:8f:9d:cd:00:0c:41:bf:b0:19:08:00 SRC=134.184.129.2 DST=192.168.1.105 LEN=1500 TOS=0x00 PREC=0x00 TTL=53 ID=50326 DF PROTO=TCP SPT=80 DPT=60204 WINDOW=49640 RES=0x00 ACK URGP=0 
[ 2549.040000] Inbound IN=eth1 OUT= MAC=00:1b:77:8f:9d:cd:00:0c:41:bf:b0:19:08:00 SRC=134.184.129.2 DST=192.168.1.105 LEN=1500 TOS=0x00 PREC=0x00 TTL=53 ID=50327 DF PROTO=TCP SPT=80 DPT=60204 WINDOW=49640 RES=0x00 ACK URGP=0 
[ 2669.048000] Inbound IN=eth1 OUT= MAC=00:1b:77:8f:9d:cd:00:0c:41:bf:b0:19:08:00 SRC=134.184.129.2 DST=192.168.1.105 LEN=1500 TOS=0x00 PREC=0x00 TTL=53 ID=50329 DF PROTO=TCP SPT=80 DPT=60204 WINDOW=49640 RES=0x00 ACK URGP=0 
[ 2729.084000] Inbound IN=eth1 OUT= MAC=00:1b:77:8f:9d:cd:00:0c:41:bf:b0:19:08:00 SRC=134.184.129.2 DST=192.168.1.105 LEN=1500 TOS=0x00 PREC=0x00 TTL=53 ID=50330 DF PROTO=TCP SPT=80 DPT=60204 WINDOW=49640 RES=0x00 ACK URGP=0 
[ 2789.060000] Inbound IN=eth1 OUT= MAC=00:1b:77:8f:9d:cd:00:0c:41:bf:b0:19:08:00 SRC=134.184.129.2 DST=192.168.1.105 LEN=1500 TOS=0x00 PREC=0x00 TTL=53 ID=50331 DF PROTO=TCP SPT=80 DPT=60204 WINDOW=49640 RES=0x00 ACK URGP=0 

```

When I ping to my route I lose about 16% of the packets. When I ping to Google packet loss is mostly between 10 and 40%. Average ping times (to Google) are 25 to 30 ms.

And I think that about covers it. Thanks all!

---

