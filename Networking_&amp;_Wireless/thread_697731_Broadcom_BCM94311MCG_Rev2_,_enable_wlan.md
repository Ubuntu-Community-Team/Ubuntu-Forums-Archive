---
title: "Broadcom BCM94311MCG Rev2 , enable wlan?"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by °Spitfire on 2008-02-15
Hi, Boys and Girls

Hopefully i may get some help.

I have a *HP Pavilion 6610em Notebook *(for more Specs please click on this  [Link]("http://www.sysprofile.de/id46885"))
with a  **"Broadcom Corporation BCM94311MCG wlan mini-PCI ([COLOR="Red"]rev 02[/COLOR])" **Chip.

Since days i tried getting it to work with Ubuntu 7.10 i386, followed several How to's about ndiswrapper and fwcutter nothing works, even with patching the kernel to 2.6.27-7 it did not work.


*Here u get some infos:*

[COLOR="red"]uname -a[/COLOR]
```
Linux laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
```

[COLOR="red"]lspci | grep -i net[/COLOR]
```
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```


[COLOR="red"]iwconfig[/COLOR]
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

[COLOR="red"]ifconfig[/COLOR]
```
eth0      Link encap:Ethernet  HWaddr DE:65:96:24:1B:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1600 (1.5 KB)  TX bytes:1600 (1.5 KB)
```

Additionally i have an Usb 2 Wifi-Stick from SMC-Networks Model Number: **SMCWUSBS-N** with **Ralink RT2720** Chip. Maybe someone knows how to install it.

[B]So lets sum up:
Option A: Get the Broadcom 4311 (Rev2) to work
Option B: Get the SMCWUSBS-N USB2 Wlan Stick to work.[/B]

If i could get some help from a elder Linux User i would be very happy.:) :popcorn:


Thx, Spitfire aka Yves

---

### Post by rustybronco on 2008-02-15
> **°Spitfire said:**
> 
If i could get some help from a elder Linux User i would be very happy.:) :popcorn:


Thx, Spitfire aka YvesBecause you asked for someone old...
[http://ubuntuforums.org/showpost.php?p=4333594&postcount=5](http://ubuntuforums.org/showpost.php?p=4333594&postcount=5)

"just because i'm old doesn't mean I know what i'm doing"

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by °Spitfire on 2008-02-15
Thank you for your quick reply. :D

I just went trough installing the restricted Driver "http://xeve.de/down/wl_apsta.o" like many times before, but still cant connect to my unsecured wlan.

What Driver/Firmware do i have to download from [http://linuxwireless.org/en/users/Drivers/b43?](http://linuxwireless.org/en/users/Drivers/b43?)

For the Hardy Heron i had to use  4.80.53.0, right?
So i have to use 4.150.10.5? And is this the driver/firmware for the REV2 version of the chip?

Edit: I asked for some one with experience  cause i got none, and i am about to give it up cause trying to enable it since many days. But im not new to PC's, i googled and read enough Tutorials without success.

Thx,

---

### Post by rustybronco on 2008-02-15
first of all you are using 7.10 not hardy, have you tried the links provided such as enabling the restricted drivers in 7.10 (the first method in the first link) or this [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
there are three methods given to try in the above links. :)
let me know if you need help. Dale

---

### Post by °Spitfire on 2008-02-15
Yes i know i am using Gusty Gibson, just to clear it up. I was using Hardy before, cause i read some there that Hardy has better support fore the chip, especially for the Rev2 version.

I will reply later on.

Well i enable the restricted driver before, as described in your link. Did not  work, but the wlan led goes blue, inverse to red. But cant find a Wlan  nor  connect to my.

And now im trying the method linked in your last Post, (but i guess it wont work, cause i tried it last time yesterday)

---

### Post by °Spitfire on 2008-02-15
> **rustybronco said:**
>  or this [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
there are three methods given to try in the above links. :)
let me know if you need help. Dale

Hi Dave, it's me again.

I followed this Guide, (its a really good one) but couldn't install the ndiswrapper version they mentioned, so i used an newer one. Every step worked without errors, but i still does not work.

(Reading trough the comments it should work with my Chip revision, but i ain't have luck)

Even i disabled apic like the guy told in the comment number #55.

:confused:
[B][COLOR=Red]  dmesg

[/COLOR][/B] ```
 [    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 520034
[    0.000000] Kernel command line: root=UUID=951bdcc0-ddae-42e4-b2b8-651ed65463b5 ro quiet splash noapic
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1808.383 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 2066824k/2096512k available (2015k kernel code, 28468k reserved, 916k data, 364k init, 1179008k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.000000] hpet0: 3 32-bit timers, 25000000 Hz
[    0.080000] Calibrating delay using timer specific routine.. 3620.06 BogoMIPS (lpj=7240129)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.428000] ACPI: Core revision 20070126
[    0.428000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.428000] ACPI: setting ELCR to 0200 (from 8ca0)
[    0.432000] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 stepping 01
[    0.432000] SMP alternatives: switching to SMP code
[    0.432000] Booting processor 1/1 eip 3000
[    0.440000] Initializing CPU#1
[    0.524000] Calibrating delay using timer specific routine.. 3616.41 BogoMIPS (lpj=7232828)
[    0.524000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.524000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.524000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.524000] CPU 1(2) -> Core 1
[    0.524000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.524000] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 stepping 01
[    0.524000] Total of 2 processors activated (7236.47 BogoMIPS).
[    0.524000] Brought up 2 CPUs
[    0.556000] migration_cost=4000
[    0.556000] Booting paravirtualized kernel on bare hardware
[    0.556000] Time:  0:05:59  Date: 01/16/108
[    0.556000] NET: Registered protocol family 16
[    0.560000] EISA bus registered
[    0.560000] ACPI: bus type pci registered
[    0.580000] PCI: PCI BIOS revision 3.00 entry at 0xfde1b, last bus=9
[    0.580000] PCI: Using configuration type 1
[    0.580000] Setting up standard PCI resources
[    0.580000] ACPI: EC: Look up EC in DSDT
[    0.580000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.584000] ACPI: System BIOS is requesting _OSI(Linux)
[    0.584000] ACPI: Please test with "acpi_osi=!Linux"
[    0.584000] Please send dmidecode to linux-acpi@vger.kernel.org
[    0.584000] ACPI: Interpreter enabled
[    0.584000] ACPI: (supports S0 S3 S4 S5)
[    0.584000] ACPI: Using PIC for interrupt routing
[    0.592000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.592000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.592000] PCI: Probing PCI hardware (bus 00)
[    0.592000] PCI: Transparent bridge - 0000:00:08.0
[    0.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR3._PRT]
[    0.616000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 *15)
[    0.616000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 *11 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 *15)
[    0.616000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.620000] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[    0.620000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.620000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.620000] pnp: PnP ACPI init
[    0.620000] ACPI: bus type pnp registered
[    0.620000] ACPI Error (dsopcode-0548): Field [I9MN] at 544 exceeds Buffer [IORT] size 464 (bits) [20070126]
[    0.620000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node df822900), AE_AML_BUFFER_LIMIT
[    0.620000] ACPI Error (uteval-0236): Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node df822900), AE_AML_BUFFER_LIMIT
[    0.620000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02
[    0.620000] pnp: PnP ACPI: found 11 devices
[    0.620000] ACPI: ACPI bus type pnp unregistered
[    0.620000] PnPBIOS: Disabled by ACPI PNP
[    0.620000] PCI: Using ACPI for IRQ routing
[    0.620000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.648000] NET: Registered protocol family 8
[    0.648000] NET: Registered protocol family 20
[    0.648000] pnp: 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.648000] pnp: 00:0a: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.648000] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.648000] pnp: 00:0a: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.648000] pnp: 00:0a: iomem range 0xfec80000-0xfec80fff has been reserved
[    0.652000] Time: hpet clocksource has been installed.
[    0.676000] PCI: Bridge: 0000:00:08.0
[    0.676000]   IO window: disabled.
[    0.676000]   MEM window: f2100000-f21fffff
[    0.676000]   PREFETCH window: disabled.
[    0.676000] PCI: Bridge: 0000:00:0b.0
[    0.676000]   IO window: disabled.
[    0.676000]   MEM window: disabled.
[    0.676000]   PREFETCH window: disabled.
[    0.676000] PCI: Bridge: 0000:00:0c.0
[    0.676000]   IO window: disabled.
[    0.676000]   MEM window: f2000000-f20fffff
[    0.676000]   PREFETCH window: disabled.
[    0.676000] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0
[    0.676000] PCI: Bridge: 0000:00:0d.0
[    0.676000]   IO window: 4000-4fff
[    0.676000]   MEM window: cc000000-ceffffff
[    0.676000]   PREFETCH window: d0000000-dfffffff
[    0.676000] PCI: Bridge: 0000:00:0e.0
[    0.676000]   IO window: 5000-5fff
[    0.676000]   MEM window: f0000000-f1ffffff
[    0.676000]   PREFETCH window: f2600000-f27fffff
[    0.676000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    0.676000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.676000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.676000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.676000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.676000] NET: Registered protocol family 2
[    0.724000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.724000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.724000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.724000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.724000] TCP reno registered
[    0.740000] checking if image is initramfs... it is
[    1.392000] Freeing initrd memory: 7347k freed
[    1.392000] Simple Boot Flag at 0x36 set to 0x1
[    1.392000] audit: initializing netlink socket (disabled)
[    1.392000] audit(1203120359.152:1): initialized
[    1.392000] highmem bounce pool size: 64 pages
[    1.392000] VFS: Disk quotas dquot_6.5.1
[    1.392000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.392000] io scheduler noop registered
[    1.392000] io scheduler anticipatory registered
[    1.392000] io scheduler deadline registered
[    1.392000] io scheduler cfq registered (default)
[    1.392000] Boot video device is 0000:05:00.0
[    1.392000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.392000] assign_interrupt_mode Found MSI capability
[    1.392000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.392000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.392000] assign_interrupt_mode Found MSI capability
[    1.392000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.392000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    1.392000] assign_interrupt_mode Found MSI capability
[    1.392000] Allocate Port Service[0000:00:0d.0:pcie00]
[    1.392000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    1.392000] assign_interrupt_mode Found MSI capability
[    1.392000] Allocate Port Service[0000:00:0e.0:pcie00]
[    1.392000] isapnp: Scanning for PnP cards...
[    1.748000] isapnp: No Plug & Play device found
[    1.772000] Real Time Clock Driver v1.12ac
[    1.772000] hpet_resources: 0xfed00000 is busy
[    1.772000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.772000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.772000] input: Macintosh mouse button emulation as /class/input/input0
[    1.772000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.800000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.800000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.800000] mice: PS/2 mouse device common for all mice
[    1.804000] EISA: Probing bus 0 at eisa.0
[    1.804000] Cannot allocate resource for EISA slot 1
[    1.804000] Cannot allocate resource for EISA slot 3
[    1.804000] Cannot allocate resource for EISA slot 4
[    1.804000] Cannot allocate resource for EISA slot 5
[    1.804000] EISA: Detected 0 cards.
[    1.804000] TCP cubic registered
[    1.804000] NET: Registered protocol family 1
[    1.804000] Using IPI No-Shortcut mode
[    1.804000]   Magic number: 12:684:51
[    1.804000] Freeing unused kernel memory: 364k freed
[    1.820000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.908000] AppArmor: AppArmor initialized<5>audit(1203120360.652:2):  type=1505 info="AppArmor initialized" pid=1263
[    2.924000] fuse init (API version 7.8)
[    2.936000] Failure registering capabilities with primary security module.
[    2.968000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.968000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.968000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.968000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.968000] ACPI Exception (thermal-0311): AE_BAD_DATA, No critical threshold [20070126]
[    3.544000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.544000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[    3.544000] PCI: setting IRQ 10 as level-triggered
[    3.544000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[    3.544000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    3.544000] forcedeth: using HIGHDMA
[    3.556000] usbcore: registered new interface driver usbfs
[    3.556000] usbcore: registered new interface driver hub
[    3.556000] usbcore: registered new device driver usb
[    3.556000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.584000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.584000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.640000] SCSI subsystem initialized
[    3.700000] libata version 2.21 loaded.
[    4.064000] eth0: forcedeth.c: subsystem: 0103c:30cf bound to 0000:00:06.0
[    4.064000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[    4.064000] PCI: setting IRQ 11 as level-triggered
[    4.064000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[    4.064000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    4.064000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.064000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    4.064000] ohci_hcd 0000:00:02.0: irq 11, io mem 0xf2486000
[    4.120000] usb usb1: configuration #1 chosen from 1 choice
[    4.120000] hub 1-0:1.0: USB hub found
[    4.120000] hub 1-0:1.0: 10 ports detected
[    4.224000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[    4.224000] PCI: setting IRQ 7 as level-triggered
[    4.224000] ACPI: PCI Interrupt 0000:00:02.1[b] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[    4.224000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    4.224000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.224000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    4.224000] ehci_hcd 0000:00:02.1: debug port 1
[    4.224000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    4.224000] ehci_hcd 0000:00:02.1: irq 7, io mem 0xf2488000
[    4.224000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.224000] usb usb2: configuration #1 chosen from 1 choice
[    4.224000] hub 2-0:1.0: USB hub found
[    4.224000] hub 2-0:1.0: 10 ports detected
[    4.328000] NFORCE-MCP65: IDE controller at PCI slot 0000:00:09.0
[    4.328000] NFORCE-MCP65: chipset revision 161
[    4.328000] NFORCE-MCP65: not 100% native mode: will probe irqs later
[    4.328000] NFORCE-MCP65: BIOS didn't set cable bits correctly. Enabling workaround.
[    4.328000] NFORCE-MCP65: 0000:00:09.0 (rev a1) UDMA133 controller
[    4.328000]     ide0: BM-DMA at 0x30c0-0x30c7, BIOS settings: hda:DMA, hdb:pio
[    4.328000] Probing IDE interface ide0...
[    4.936000] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    5.064000] hda: Slimtype DVD A DS8A1H, ATAPI CD/DVD-ROM drive
[    5.080000] usb 2-4: configuration #1 chosen from 1 choice
[    5.384000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    5.596000] usb 1-2: configuration #1 chosen from 1 choice
[    5.616000] usbcore: registered new interface driver hiddev
[    5.620000] input: Logitech USB Receiver as /class/input/input2
[    5.620000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-2
[    5.636000] input: Logitech USB Receiver as /class/input/input3
[    5.636000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-2
[    5.636000] usbcore: registered new interface driver usbhid
[    5.636000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.736000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.752000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 15
[    5.752000] PCI: setting IRQ 15 as level-triggered
[    5.752000] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 15 (level, low) -> IRQ 15
[    5.760000] ahci 0000:00:0a.0: version 2.2
[    5.760000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[    5.760000] PCI: setting IRQ 5 as level-triggered
[    5.760000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[    5.800000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[15]  MMIO=[f2100000-f21007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.764000] ahci 0000:00:0a.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    6.764000] ahci 0000:00:0a.0: flags: 64bit ncq pm led clo pmp pio 
[    6.764000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    6.764000] scsi0 : ahci
[    6.764000] scsi1 : ahci
[    6.764000] scsi2 : ahci
[    6.764000] scsi3 : ahci
[    6.764000] ata1: SATA max UDMA/133 cmd 0xf8898100 ctl 0x00000000 bmdma 0x00000000 irq 5
[    6.764000] ata2: SATA max UDMA/133 cmd 0xf8898180 ctl 0x00000000 bmdma 0x00000000 irq 5
[    6.764000] ata3: SATA max UDMA/133 cmd 0xf8898200 ctl 0x00000000 bmdma 0x00000000 irq 5
[    6.764000] ata4: SATA max UDMA/133 cmd 0xf8898280 ctl 0x00000000 bmdma 0x00000000 irq 5
[    7.076000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b008e6c5400]
[    7.248000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.248000] ata1.00: ATA-7: FUJITSU MHW2120BH, 8918, max UDMA/100
[    7.248000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    7.248000] ata1.00: configured for UDMA/100
[    7.560000] ata2: SATA link down (SStatus 0 SControl 300)
[    7.872000] ata3: SATA link down (SStatus 0 SControl 300)
[    8.184000] ata4: SATA link down (SStatus 0 SControl 300)
[    8.184000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2120B 8918 PQ: 0 ANSI: 5
[    8.192000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[    8.192000] Uniform CD-ROM driver Revision: 3.20
[    8.196000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    8.196000] sd 0:0:0:0: [sda] Write Protect is off
[    8.196000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.196000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.196000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    8.196000] sd 0:0:0:0: [sda] Write Protect is off
[    8.196000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.196000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.196000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    8.324000] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.328000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.896000] kjournald starting.  Commit interval 5 seconds
[    8.896000] EXT3-fs: mounted filesystem with ordered data mode.
[   15.892000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.896000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.196000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   16.196000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   16.256000] ieee80211_crypt: registered algorithm 'NULL'
[   16.260000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.260000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.376000] bcm43xx driver
[   16.376000] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 11
[   16.376000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 11 (level, low) -> IRQ 11
[   16.376000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   16.384000] bcm43xx: Unsupported 80211 core revision 13
[   16.384000] bcm43xx: Invalid PHY Revision 9
[   16.452000] sdhci: Secure Digital Host Controller Interface driver
[   16.452000] sdhci: Copyright(c) Pierre Ossman
[   16.452000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 22)
[   16.452000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[   16.452000] ACPI: PCI Interrupt 0000:07:05.1[b] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[   16.452000] mmc0: SDHCI at 0xf2100800 irq 10 DMA
[   16.500000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.516000] input: PC Speaker as /class/input/input4
[   16.544000] Linux video capture interface: v2.00
[   16.552000] usbcore: registered new interface driver xpad
[   16.552000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   16.576000] nvidia: module license 'NVIDIA' taints kernel.
[   16.832000] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 15
[   16.832000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK4E] -> GSI 15 (level, low) -> IRQ 15
[   16.832000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   16.832000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   16.944000] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   16.944000] usbcore: registered new interface driver uvcvideo
[   16.944000] USB Video Class driver (v0.1.0)
[   17.096000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[   17.096000] ACPI: PCI Interrupt 0000:00:07.0[b] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[   17.096000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   17.520000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   17.596000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   19.440000] ndiswrapper version 1.45 loaded (smp=yes)
[   19.492000] usbcore: registered new interface driver ndiswrapper
[   19.584000] lp: driver loaded but no devices found
[   20.212000] EXT3 FS on sda5, internal journal
[   21.568000] kjournald starting.  Commit interval 5 seconds
[   21.572000] EXT3 FS on sda6, internal journal
[   21.572000] EXT3-fs: mounted filesystem with ordered data mode.
[   22.440000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   22.444000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.456000] No dock devices found.
[   22.512000] input: Power Button (FF) as /class/input/input6
[   22.512000] ACPI: Power Button (FF) [PWRF]
[   22.512000] input: Lid Switch as /class/input/input7
[   22.512000] ACPI: Lid Switch [LID]
[   22.512000] input: Power Button (CM) as /class/input/input8
[   22.512000] ACPI: Power Button (CM) [PWRB]
[   22.512000] input: Sleep Button (CM) as /class/input/input9
[   22.512000] ACPI: Sleep Button (CM) [SLPB]
[   22.600000] ACPI: Battery Slot [BAT0] (battery present)
[   22.692000] ACPI: AC Adapter [ACAD] (on-line)
[   22.868000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 processors (version 2.00.00)
[   22.872000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   22.872000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x13
[   22.872000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[   23.744000] ppdev: user-space parallel port driver
[   23.880000] audit(1203116782.161:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5244 profile="/usr/sbin/cupsd"
[   23.928000] apm: BIOS not found.
[   24.148000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   24.224000] Failure registering capabilities with primary security module.
[   24.724000] Bluetooth: Core ver 2.11
[   24.724000] NET: Registered protocol family 31
[   24.724000] Bluetooth: HCI device and connection manager initialized
[   24.724000] Bluetooth: HCI socket layer initialized
[   24.760000] Bluetooth: L2CAP ver 2.8
[   24.760000] Bluetooth: L2CAP socket layer initialized
[   24.768000] Bluetooth: RFCOMM socket layer initialized
[   24.768000] Bluetooth: RFCOMM TTY layer initialized
[   24.768000] Bluetooth: RFCOMM ver 1.8
[   25.000000] Clocksource tsc unstable (delta = -277828029 ns)
[COLOR=Red] [   27.396000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   29.828000] NET: Registered protocol family 17
[   32.164000] NET: Registered protocol family 10
[   32.164000] lo: Disabled Privacy Extensions
[   42.480000] eth0: no IPv6 routers present
[   44.432000] UDF-fs: No VRS found
[   44.504000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.576000] ISO 9660 Extensions: RRIP_1991A
[   50.624000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   73.836000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   89.792000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   89.916000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   91.044000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  157.032000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  168.148000] eth0: no IPv6 routers present[/COLOR]
[COLOR=Red] [  180.248000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  203.504000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  326.680000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  449.848000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  573.016000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  696.196000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  819.400000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  942.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1065.852000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.[/COLOR]
yves@laptop:~$ 

```PS: Nice Biography: => old :p

Yves

---

### Post by rustybronco on 2008-02-15
If you don't have any success would you post  the output of
 lshw -C network
iwlist scan
cat /etc/modprobe.d/blacklist
Thank you, Dale

---

### Post by rustybronco on 2008-02-15
Guess we were posting at the same time.... 
You'll have to  give me a while I've got to go outside and freeze while changing the battery on my wifes car and it will take a while to get one but I will be looking at your dmesg.

---

### Post by °Spitfire on 2008-02-15
No problem Sir, i'm young and got time.
Well i guess your wife's car starts again. :)

And here are the results of the commands you asked me for.

[COLOR=SeaGreen] sudo lswh -C network[/COLOR]

```
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: de:65:96:24:1b:00
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:00:00:1a:73:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```[COLOR=SeaGreen]iwlist scan[/COLOR]
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
``` [COLOR=SeaGreen]

cat /etc/modprobe.d/blacklist[/COLOR]
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx[COLOR=Red]”[/COLOR] 
```Okey, i see i have to edit the blacklist, the red marked is wrong.

So i will edit my post back then i changed it and i got the results of it.

[SIZE=3]Edit:** Big Thank You Dale,**[SIZE=2] you made my day.

Finally my Wifi works, well i will Bookmark and save the How to.  You gave me the right links and commands to find the mistakes myself.

yves@laptop:~$ [COLOR=SeaGreen]iwlist scan[/COLOR]
[/SIZE][/SIZE]```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:28:FC:1A
                    ESSID:"wlan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```[SIZE=3][SIZE=2]

[I]Merci Beaucoup :KS
[/I][/SIZE][/SIZE]
*[SIZE=5]@Everybody [/SIZE]who's reading this threat to find a solution to install the* **Broadcom BCM94311MCG (Rev2)** *wlan chip, here you find the solution that worked for me and many others *[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

[I]Thx, Dale
[/I]

---

### Post by rustybronco on 2008-02-15
Well I just got in from finishing  the car (batt was 10 years old so I guess its due for one)  and find that you have fixed it, so glad to hear it!

---

### Post by sir4taye on 2008-02-15
I have a fix, step by step, to geting a bcm94311mcg card to work!!!

I struggled trying to get clear noob directions from this or any other ubuntu forum. Most linux users lost the ability to communicate with the pre-me. So, I took the instructions I got and tried to simplify the process for any who really want to make this work. Ubuntu is the best alternative to MSspyware mothership beacon caller OS.

Usually you need to stop conflicting device software first. So we do that, then install the ndiswrapper which uses the original driver with a linux translator wrapper around it for the kernal to understand and what not. 

All of the commands between the # signs (enter without the # signs) need to be entered into a terminal session, which you can access by clicking Applications/Accessories/Terminal. When the screen opens start entering these commands one by one and pressing enter after each. Read onscreen instructions that come up and make sure you have a hardline for internet working as some packages will need to be downloaded.
 
1)you must uninstall ndiswrapper & bcm43xx-fwcutter

#sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9#
#sudo apt-get remove bcm43xx-fwcutter#

2)Add bcm43xx to the /etc/modprobe.d/blacklist file

#sudo vi /etc/modprobe.d/blacklist#
a text editor will activate add this line "blacklist bcm43xx" (without "") by hitting i once and moving to the bottom and typing the new line then hit escape then enter ":wq" (without the "")

3)Reboot
#sudo reboot#

Download driver for BCM94311MCG wlan mini-PCI here:
[http://www.stosha.net/WLANBroadcom.tar.gz](http://www.stosha.net/WLANBroadcom.tar.gz) or
[http://stosha.stylet-software.com/WLANBroadcom.tar.gz](http://stosha.stylet-software.com/WLANBroadcom.tar.gz)

#cd ~/home/(yourusername)/Desktop#

#tar -xzvf WLANBroadcom.tar.gz#

4)move the folder WLANBroadcom to your home directory

#mv WLANBroadcom/ /home/(yourusername)/#

5)Install ndiswrapper from source :

#sudo apt-get update#
#sudo apt-get install build-essential#
#sudo apt-get install linux-headers-`uname -r`#
#sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build#
#mkdir -p ~/bcm43xx/ndiswrapper#
#cd ~/bcm43xx/ndiswrapper#
#sudo wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0#](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0#)
#tar -xvzf ndiswrapper-1.49.tar.gz#
#cd ndiswrapper-1.49#
#make distclean#
#make#
#sudo make install#

6)Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper

#cd /home/yourname/WLANBroadcom/#

#sudo ndiswrapper -i bcmwl5.inf#

#ndiswrapper -l#

#sudo vim /etc/modules#
an editor will activate add this line "ndiswrapper" (without "")

#sudo modprobe ndiswrapper#

#sudo ndiswrapper -m#

7)Reboot
#sudo reboot#

___________________________________________________________
amd64 tk-55 (1.6Ghz), nVidia chipset, 1G ram,
broadcom 4311 mini-pci wlan, compaq presario f700 
\\:D/

---

### Post by sir4taye on 2008-02-15
that url for step 5) is = "http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0"

---

### Post by °Spitfire on 2008-02-16
This is  to, a good beginners guide. Thank you for your work. :)

---

### Post by Victormd on 2008-02-23
This is the how-to that did it for me, but I had to compile ndiswrapper from source...
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by pat5star on 2008-02-27
Thanks you so much sir4taye, that did it for me! :)

-Pat

---

### Post by gschaden on 2008-03-25
Hi,

I'm still having a problme with this chip. I use the 2.6.22-14-386 kernel, on a HP 8510p with ndiswrapper ndiswrapper-1.47, and the drivers from WLANBroadcom.tar.gz. 

I don't have the option to switch to the latest kernel, so how can I make my device work.

And here the problem

```

<6>[ 2701.473460] ndiswrapper version 1.47 loaded (smp=no)
<3>[ 2701.477808] ndiswrapper (check_nt_hdr:156): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
<3>[ 2701.477811] ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl5'
<3>[ 2701.478053] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
<6>[ 2701.480440] usbcore: registered new interface driver ndiswrapper

```

I also tried the bcm43xx driver, which just gives me
```

<4>[ 1397.923623] bcm43xx: Unsupported 80211 core revision 13
<4>[ 1397.925474] bcm43xx: Invalid PHY Revision 9
<3>[ 1426.078118] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

```

I also recompiled the compat-wireless kit, and tried with the b43 driver but, this driver does not detect the device at all.

---

