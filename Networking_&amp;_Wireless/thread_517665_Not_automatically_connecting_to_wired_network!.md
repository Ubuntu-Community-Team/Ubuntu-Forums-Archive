---
title: "Not automatically connecting to wired network!"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by The-Organist on 2007-08-04
Have read some previous posts on this, but cannot get the "solutions" from it since they keep reverting to WireLESS network problems.  Here's MY problem (didn't have with Ubuntu 6)

When I boot, I have to MANUALLY click on the Network Manager Icon and select Wired Network.  It has no trouble connecting like this, but I don't want to have to ask it to connect!!!

Network card obviously okay, since the only problem is the lack of automaticness of connecting at startup.  Have a DLINK router with DHCP.  Only other possible NW connection is a modem which is not enabled.

Network Administration says DHCP (Automatic) in the IP settings (as it should be I would think).

Assistance greatly appreciated to get this working automatically - and I'm sort of a Linux newbie.

---

### Post by Maischoyu on 2007-08-04
I have same problem too... read my post:
> [http://ubuntuforums.org/showthread.php?t=517624](http://ubuntuforums.org/showthread.php?t=517624)

what is strange is i can connect from live cd.

---

### Post by noob12 on 2007-08-04
Can you show the output of

```

lshw -C network

ifconfig -a

cat /etc/network/interfaces

```

---

### Post by The-Organist on 2007-08-04
-------------------------not working---------------------------------

martin@KANE03:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network               

       description: Ethernet interface

       product: 21x4x DEC-Tulip compatible 10/100 Ethernet

       vendor: Davicom Semiconductor, Inc.

       physical id: b

       bus info: pci@00:0b.0

       logical name: eth0

       version: 40

       serial: 00:08:a1:1d:38:ab

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=32 maxlatency=40 mingnt=20 multicast=yes

       resources: ioport:d800-d8ff iomemory:e6040000-e60400ff irq:5

martin@KANE03:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:08:A1:1D:38:AB  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:9 errors:0 dropped:0 overruns:0 frame:0

          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:1232 (1.2 KiB)  TX bytes:1626 (1.5 KiB)

          Interrupt:5 Base address:0xd800 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



martin@KANE03:~$ cat /etc/network/interfaces

auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp



-------------Once connected-----------------------

martin@KANE03:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network               

       description: Ethernet interface

       product: 21x4x DEC-Tulip compatible 10/100 Ethernet

       vendor: Davicom Semiconductor, Inc.

       physical id: b

       bus info: pci@00:0b.0

       logical name: eth0

       version: 40

       serial: 00:08:a1:1d:38:ab

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.42.2 latency=32 maxlatency=40 mingnt=20 multicast=yes

       resources: ioport:d800-d8ff iomemory:e6040000-e60400ff irq:5

martin@KANE03:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:08:A1:1D:38:AB  

          inet addr:192.168.42.2  Bcast:192.168.42.255  Mask:255.255.255.0

          inet6 addr: fe80::208:a1ff:fe1d:38ab/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:16 errors:0 dropped:0 overruns:0 frame:0

          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2332 (2.2 KiB)  TX bytes:5315 (5.1 KiB)

          Interrupt:5 Base address:0xd800 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



martin@KANE03:~$ cat /etc/network/interfaces

auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp

---

### Post by The-Organist on 2007-08-04
Have found a workaround... Select manual configuration and set up a static IP address.  Then change back to Automatic DHCP.  The Static IP address and gateway details stay fogged in, but I collect a IP address from the DHCP server.

Takes MUCH longer to log in, but I'm used to Windows, so this is not a major problem...  Well, actually I would PREFER to have it work properly.

---

### Post by noob12 on 2007-08-04
I'm assuming the double-spacing is due to the posting process.

It looks like what might behappening is that DHCP is not getting an address assigned before it times out.  The link isn't quite ready at that point, but later it works.  We want to confirm this and then understand why.

After a clean boot, before fixing your connectivity, can you save the output of

```

dmesg

```

and

```

tail -1000 /var/log/syslog | grep dhclient

```

---

### Post by The-Organist on 2007-08-05
martin@KANE03:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 VIAP4X                                ) @ 0x000f62b0
[    0.000000] ACPI: RSDT (v001 VIAP4X AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 VIAP4X AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[    0.000000] ACPI: DSDT (v001 VIAP4X AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Detected 2266.966 MHz processor.
[   31.020908] Built 1 zonelists.  Total pages: 130033
[   31.020917] Kernel command line: root=UUID=eb69afcb-cfc5-4bc7-b9c9-f345ee73fdfa ro quiet splash
[   31.021136] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   31.021153] mapped APIC to ffffd000 (0140a000)
[   31.021160] Enabling fast FPU save and restore... done.
[   31.021166] Enabling unmasked SIMD FPU exception support... done.
[   31.021191] Initializing CPU#0
[   31.021354] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   31.022451] Console: colour VGA+ 80x25
[   31.023264] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.024013] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.044044] Memory: 508728k/524224k available (1992k kernel code, 14980k reserved, 900k data, 328k init, 0k highmem)
[   31.044057] virtual kernel memory layout:
[   31.044058]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   31.044059]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.044061]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   31.044062]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   31.044063]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   31.044064]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   31.044065]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   31.044069] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.121201] Calibrating delay using timer specific routine.. 4538.70 BogoMIPS (lpj=9077410)
[   31.121257] Security Framework v1.0.0 initialized
[   31.121267] SELinux:  Disabled at boot.
[   31.121287] Mount-cache hash table entries: 512
[   31.121483] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   31.121499] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   31.121502] CPU: L2 cache: 512K
[   31.121505] CPU: Hyper-Threading is disabled
[   31.121508] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00003080 00000000 00000000 00000000
[   31.121521] Compat vDSO mapped to ffffe000.
[   31.121526] Remapping vsyscall page to ffffe000
[   31.121542] Checking 'hlt' instruction... OK.
[   31.137332] SMP alternatives: switching to UP code
[   31.137634] Freeing SMP alternatives: 11k freed
[   31.137955] Early unpacking initramfs... done
[   31.502556] ACPI: Core revision 20060707
[   31.509503] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   31.511274] ACPI: setting ELCR to 0200 (from 0a20)
[   31.582259] CPU0: Intel(R) Pentium(R) 4 CPU 2.26GHz stepping 04
[   31.582268] SMP motherboard not detected.
[   31.582273] Local APIC not detected. Using dummy APIC emulation.
[   31.582325] Brought up 1 CPUs
[   31.582678] Booting paravirtualized kernel on bare hardware
[   31.582783] Time: 17:56:38  Date: 07/05/107
[   31.582836] NET: Registered protocol family 16
[   31.582990] EISA bus registered
[   31.582997] ACPI: bus type pci registered
[   31.620981] PCI: PCI BIOS revision 2.10 entry at 0xfb270, last bus=1
[   31.620984] PCI: Using configuration type 1
[   31.620986] Setting up standard PCI resources
[   31.632527] ACPI: Interpreter enabled
[   31.632532] ACPI: Using PIC for interrupt routing
[   31.633238] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.633248] PCI: Probing PCI hardware (bus 00)
[   31.634144] Boot video device is 0000:01:00.0
[   31.634205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.654774] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   31.655132] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   31.655523] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   31.655911] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   31.659667] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.659693] pnp: PnP ACPI init
[   31.664429] pnp: PnP ACPI: found 15 devices
[   31.664437] PnPBIOS: Disabled by ACPI PNP
[   31.664525] PCI: Using ACPI for IRQ routing
[   31.664530] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.670688] NET: Registered protocol family 8
[   31.670691] NET: Registered protocol family 20
[   31.671535] PCI: Bridge: 0000:00:01.0
[   31.671538]   IO window: disabled.
[   31.671544]   MEM window: e4000000-e5ffffff
[   31.671550]   PREFETCH window: d0000000-dfffffff
[   31.671573] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.671622] NET: Registered protocol family 2
[   31.708393] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   31.708537] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   31.708697] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   31.708772] TCP: Hash tables configured (established 16384 bind 8192)
[   31.708776] TCP reno registered
[   31.720417] checking if image is initramfs... it is
[   32.445678] Freeing initrd memory: 6783k freed
[   32.446376] audit: initializing netlink socket (disabled)
[   32.446405] audit(1186336598.540:1): initialized
[   32.446637] VFS: Disk quotas dquot_6.5.1
[   32.446671] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.446760] io scheduler noop registered
[   32.446764] io scheduler anticipatory registered
[   32.446767] io scheduler deadline registered
[   32.446781] io scheduler cfq registered (default)
[   32.447176] isapnp: Scanning for PnP cards...
[   32.800671] isapnp: No Plug & Play device found
[   32.836277] Real Time Clock Driver v1.12ac
[   32.836357] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.836502] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.836757] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   32.837626] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.838021] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   32.838426] mice: PS/2 mouse device common for all mice
[   32.839263] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.839650] input: Macintosh mouse button emulation as /class/input/input0
[   32.839700] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.839707] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.840012] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   32.840410] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.840416] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.840569] EISA: Probing bus 0 at eisa.0
[   32.840610] EISA: Detected 0 cards.
[   32.870863] TCP cubic registered
[   32.870877] NET: Registered protocol family 1
[   32.870913] Using IPI No-Shortcut mode
[   32.871076] ACPI: (supports S0 S1 S4 S5)
[   32.871140]   Magic number: 3:82:946
[   32.871183]   hash matches device ttya1
[   32.871389]   hash matches device tty3
[   32.872143] Freeing unused kernel memory: 328k freed
[   32.874393] Time: tsc clocksource has been installed.
[   32.884245] input: AT Translated Set 2 keyboard as /class/input/input1
[   34.158755] Capability LSM initialized
[   34.205591] ACPI: Fan [FAN] (on)
[   34.210728] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   34.210735] ACPI: Processor [CPU0] (supports 2 throttling states)
[   34.212425] ACPI: Thermal Zone [THRM] (25 C)
[   34.947261] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[   34.947796] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   34.947800] PCI: setting IRQ 5 as level-triggered
[   34.947805] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   34.978842] eth0: Davicom DM9102 at pci0000:00:0b.0, 00:08:a1:1d:38:ab, irq 5.
[   35.000277] SCSI subsystem initialized
[   35.008370] libata version 2.20 loaded.
[   35.011891] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   35.012507] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   35.012511] PCI: setting IRQ 11 as level-triggered
[   35.012516] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   35.012525] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[   35.012553] VP_IDE: chipset revision 6
[   35.012556] VP_IDE: not 100% native mode: will probe irqs later
[   35.012569] VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   35.012580]     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:DMA
[   35.012593]     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
[   35.012602] Probing IDE interface ide0...
[   35.046887] usbcore: registered new interface driver usbfs
[   35.046949] usbcore: registered new interface driver hub
[   35.046981] usbcore: registered new device driver usb
[   35.048384] USB Universal Host Controller Interface driver v3.0
[   35.165862] Floppy drive(s): fd0 is 1.44M
[   35.235387] FDC 0 is a post-1991 82077
[    4.236000] Time: acpi_pm clocksource has been installed.
[    4.384000] hda: WDC WD2500JB-55REA0, ATA DISK drive
[    4.664000] hdb: ST3120026A, ATA DISK drive
[    4.720000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.724000] Probing IDE interface ide1...
[    5.592000] hdc: HL-DT-ST DVDRAM GSA-4081B, ATAPI CD/DVD-ROM drive
[    5.928000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.936000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    5.936000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[    5.936000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[    5.936000] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000e000
[    5.940000] usb usb1: configuration #1 chosen from 1 choice
[    5.940000] hub 1-0:1.0: USB hub found
[    5.940000] hub 1-0:1.0: 2 ports detected
[    5.948000] hda: max request size: 512KiB
[    5.968000] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[    5.972000] hda: cache flushes supported
[    5.972000]  hda: hda1
[    5.976000] hdb: max request size: 512KiB
[    5.976000] hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[    5.976000] hdb: cache flushes supported
[    5.976000]  hdb: hdb1 hdb2 < hdb5 >
[    6.036000] hdc: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.036000] Uniform CD-ROM driver Revision: 3.20
[    6.044000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    6.044000] uhci_hcd 0000:00:11.3: UHCI Host Controller
[    6.044000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[    6.044000] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000e400
[    6.044000] usb usb2: configuration #1 chosen from 1 choice
[    6.044000] hub 2-0:1.0: USB hub found
[    6.044000] hub 2-0:1.0: 2 ports detected
[    6.336000] Attempting manual resume
[    6.336000] swsusp: Resume From Partition 3:69
[    6.336000] PM: Checking swsusp image.
[    6.336000] PM: Resume from disk failed.
[    6.384000] kjournald starting.  Commit interval 5 seconds
[    6.384000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.068000] NET: Registered protocol family 17
[   17.044000] input: GenPS/2 Genius Mouse as /class/input/input2
[   17.144000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.160000] irda_init()
[   17.160000] NET: Registered protocol family 23
[   17.224000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.252000] agpgart: Detected VIA P4X266 chipset
[   17.256000] agpgart: AGP aperture is 64M @ 0xe0000000
[   17.528000] input: PC Speaker as /class/input/input3
[   17.616000] parport: PnPBIOS parport detected.
[   17.616000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   17.616000] parport0: Printer, Brother HL-1230 series
[   18.052000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   18.052000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.052000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   18.728000] fuse init (API version 7.8)
[   18.768000] lp0: using parport0 (interrupt-driven).
[   18.812000] Adding 1510068k swap on /dev/disk/by-uuid/2d31112e-0455-4207-a231-bad5eb5ff86e.  Priority:-1 extents:1 across:1510068k
[   18.964000] EXT3 FS on hdb1, internal journal
[   19.124000] NET: Registered protocol family 10
[   19.124000] lo: Disabled Privacy Extensions
[   24.796000] Using specific hotkey driver
[   24.840000] ibm_acpi: ec object not found
[   24.904000] No dock devices found.
[   24.968000] input: Power Button (FF) as /class/input/input4
[   24.976000] ACPI: Power Button (FF) [PWRF]
[   25.020000] input: Power Button (CM) as /class/input/input5
[   25.028000] ACPI: Power Button (CM) [PWRB]
[   25.076000] input: Sleep Button (CM) as /class/input/input6
[   25.084000] ACPI: Sleep Button (CM) [SLPB]
[   25.224000] pcc_acpi: loading...
[   29.648000] eth0: no IPv6 routers present
[   40.276000] ppdev: user-space parallel port driver
[   41.096000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   41.096000] apm: overridden by ACPI.
[   41.388000] Bluetooth: Core ver 2.11
[   41.388000] NET: Registered protocol family 31
[   41.388000] Bluetooth: HCI device and connection manager initialized
[   41.388000] Bluetooth: HCI socket layer initialized
[   41.440000] Bluetooth: L2CAP ver 2.8
[   41.440000] Bluetooth: L2CAP socket layer initialized
[   41.524000] Bluetooth: RFCOMM socket layer initialized
[   41.524000] Bluetooth: RFCOMM TTY layer initialized
[   41.524000] Bluetooth: RFCOMM ver 1.8
martin@KANE03:~$ tail -1000 /var/log/syslog | grep dhclient
Aug  5 17:54:01 KANE03 dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug  5 17:54:01 KANE03 dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug  5 17:54:01 KANE03 dhclient: All rights reserved.
Aug  5 17:54:01 KANE03 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug  5 17:54:01 KANE03 dhclient: 
Aug  5 17:54:02 KANE03 dhclient: Listening on LPF/eth0/00:08:a1:1d:38:ab
Aug  5 17:54:02 KANE03 dhclient: Sending on   LPF/eth0/00:08:a1:1d:38:ab
Aug  5 17:54:02 KANE03 dhclient: Sending on   Socket/fallback
Aug  5 17:54:06 KANE03 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug  5 17:54:06 KANE03 dhclient: DHCPOFFER from 192.168.42.1
Aug  5 17:54:06 KANE03 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Aug  5 17:54:06 KANE03 dhclient: DHCPACK from 192.168.42.1
Aug  5 17:54:06 KANE03 dhclient: bound to 192.168.42.2 -- renewal in 1663 seconds.

---

### Post by noob12 on 2007-08-05
And ```
ifconfig -a
``` shows no ip v4 address assigned to eth0 now?

---

### Post by noob12 on 2007-08-05
Based on the log we just got an ip address assigned as 192.168.42.2.

Is the net working?

---

### Post by The-Organist on 2007-08-05
Not at the time I collected that log.

---

### Post by noob12 on 2007-08-05
Unfortunately you missed my request to send the ifconfig -a at that time.  It looked like you had been assigned an ip address via DHCP, which implies some working network activity and an assigned address. I wanted to verify that and test pings and see if hostname resolution was still a problem.  The boot log and DHCP log you showed me looked normal.

---

### Post by The-Organist on 2007-08-08
martin@KANE03:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:A1:1D:38:AB  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1226 (1.1 KiB)  TX bytes:1608 (1.5 KiB)
          Interrupt:5 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by noob12 on 2007-08-08
I wanted to see the state right after you had this *successful* DHCP interaction.  
> 
Aug 5 17:54:02 KANE03 dhclient: Listening on LPF/eth0/00:08:a1:1d:38:ab
Aug 5 17:54:02 KANE03 dhclient: Sending on LPF/eth0/00:08:a1:1d:38:ab
Aug 5 17:54:02 KANE03 dhclient: Sending on Socket/fallback
Aug 5 17:54:06 KANE03 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 5 17:54:06 KANE03 dhclient: DHCPOFFER from 192.168.42.1
Aug 5 17:54:06 KANE03 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Aug 5 17:54:06 KANE03 dhclient: DHCPACK from 192.168.42.1
Aug 5 17:54:06 KANE03 dhclient: bound to 192.168.42.2 -- renewal in 1663 seconds.


Two days later it doesn't really say anything.

It'll be hard to diagnose this without some repeated experimentation with more timely interaction.
I can make one stab in the dark guess.

In the case shown above things went very quickly and appear to have succeeded.  Your boot-time experience of not getting an address assigned initially may be caused by a delay in establishing link state.  If this is the case you will tend to see a series of failed DHCP exchanges in your /var/log/syslog at boot time using the command I gave you earlier.

Another sign of this condition is that manually running
```

/sbin/ifdown eth0
/sbin/ifup eth0

```
tends to fix the issue.

If this seems to be consistent with your problem, try raising the timeout.  The timeout is configured in **/etc/dhcp3/dhclient.conf**.  Find the timeout 30 line and increase it.  See if that helps.

If not, then more diagnosis is needed and it will require timely interaction.  Otherwise, you might consider just using a static assignment.

---

### Post by The-Organist on 2007-08-10
Sorry about that untimely interaction!  Was ill as anything on Tuesday and struggled to catch up.  Will go through the ideas and establish a static IP address if not successful.

Thanks VERY much for the help and ideas though!!!

Regards,

Martin

---

### Post by PhilipGanchev on 2007-11-02
Hi, 

I have the same problem.  I would appreciate any help.  My ethernet connection does not come up automatically, and I always have to run "sudo dhclient" or click on the network manager applet icon and select "Wired network".  Even after running dhclient and I am connected, the NM says "No network connection".  

The output of the commands requested above is below.  I think it is quite similar to that of the original poster.  The syslog matches for "dhclient" are probably from the previous time I ran dhclient manually.

----


/% dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 000000000000ec00 end: 000000001fffec00 type: 3
[    0.000000] copy_e820_map() start: 000000001fffec00 size: 0000000000001400 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fffec00 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fffec00 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f71d0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fff5c0b
[    0.000000] ACPI: FADT (v001 IBM    TP-A21m  0x06040000  0x00000000) @ 0x1fffeb65
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fffebd9
[    0.000000] ACPI: DSDT (v001 IBM    TP-A21m  0x06040000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: acpi=force override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] Detected 797.076 MHz processor.
[    4.091827] Built 1 zonelists.  Total pages: 130033
[    4.091837] Kernel command line: root=UUID=9597d631-2a86-4b32-9b00-2c32c1bdfcc1 ro acpi=force quiet splash
[    4.092355] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    4.092374] mapped APIC to ffffd000 (0140a000)
[    4.092383] Enabling fast FPU save and restore... done.
[    4.092391] Enabling unmasked SIMD FPU exception support... done.
[    4.092412] Initializing CPU#0
[    4.092510] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    4.094043] Console: colour VGA+ 80x25
[    4.095207] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    4.096693] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.150247] Memory: 508728k/524224k available (1993k kernel code, 14956k reserved, 900k data, 328k init, 0k highmem)
[    4.150277] virtual kernel memory layout:
[    4.150280]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    4.150284]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    4.150287]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    4.150291]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    4.150294]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    4.150298]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[    4.150301]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[    4.150310] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    4.228443] Calibrating delay using timer specific routine.. 1595.46 BogoMIPS (lpj=3190920)
[    4.228550] Security Framework v1.0.0 initialized
[    4.228570] SELinux:  Disabled at boot.
[    4.228613] Mount-cache hash table entries: 512
[    4.228935] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[    4.228962] CPU: L1 I cache: 16K, L1 D cache: 16K
[    4.228969] CPU: L2 cache: 256K
[    4.228978] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[    4.229009] Compat vDSO mapped to ffffe000.
[    4.229027] Remapping vsyscall page to ffffe000
[    4.229051] Checking 'hlt' instruction... OK.
[    4.244646] SMP alternatives: switching to UP code
[    4.245022] Freeing SMP alternatives: 11k freed
[    4.245481] Early unpacking initramfs... done
[    5.045879] ACPI: Core revision 20060707
[    5.046822] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    5.056058] ACPI: setting ELCR to 0200 (from 0800)
[    5.276197] CPU0: Intel Pentium III (Coppermine) stepping 06
[    5.276212] SMP motherboard not detected.
[    5.276218] Local APIC not detected. Using dummy APIC emulation.
[    5.276317] Brought up 1 CPUs
[    5.276946] Booting paravirtualized kernel on bare hardware
[    5.277090] Time:  3:35:16  Date: 10/03/107
[    5.277171] NET: Registered protocol family 16
[    5.277418] EISA bus registered
[    5.277429] ACPI: bus type pci registered
[    5.277909] PCI: PCI BIOS revision 2.10 entry at 0xfd94f, last bus=7
[    5.277915] PCI: Using configuration type 1
[    5.277920] Setting up standard PCI resources
[    5.567027] ACPI: Interpreter enabled
[    5.567041] ACPI: Using PIC for interrupt routing
[    5.568888] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    5.570183] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    5.571476] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    5.572791] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    5.573648] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    5.573660] PCI: Probing PCI hardware (bus 00)
[    5.574886] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    5.575472] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[    5.575481] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[    5.575492] PIIX4 devres C PIO at 15e8-15ef
[    5.575500] PIIX4 devres I PIO at 03f0-03f7
[    5.575507] PIIX4 devres J PIO at 002e-002f
[    5.575667] Boot video device is 0000:01:00.0
[    5.575926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    5.797518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    5.799260] ACPI: Power Resource [PSER] (on)
[    5.799594] ACPI: Power Resource [PSIO] (on)
[    5.804731] Linux Plug and Play Support v0.97 (c) Adam Belay
[    5.804766] pnp: PnP ACPI init
[    5.917562] pnp: PnP ACPI: found 15 devices
[    5.917575] PnPBIOS: Disabled by ACPI PNP
[    5.917725] PCI: Using ACPI for IRQ routing
[    5.917734] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    5.923093] NET: Registered protocol family 8
[    5.923100] NET: Registered protocol family 20
[    5.924382] pnp: 00:02: ioport range 0x1000-0x103f could not be reserved
[    5.924392] pnp: 00:02: ioport range 0x1040-0x104f has been reserved
[    5.924400] pnp: 00:02: ioport range 0xfe00-0xfe0f has been reserved
[    5.924423] pnp: 00:09: ioport range 0x15e0-0x15ef has been reserved
[    5.925184] PCI: Bridge: 0000:00:01.0
[    5.925191]   IO window: 2000-2fff
[    5.925201]   MEM window: f4200000-f5ffffff
[    5.925209]   PREFETCH window: 40000000-400fffff
[    5.925218] PCI: Bus 2, cardbus bridge: 0000:00:02.0
[    5.925224]   IO window: 00001400-000014ff
[    5.925232]   IO window: 00003000-000030ff
[    5.925240]   PREFETCH window: 30000000-33ffffff
[    5.925248]   MEM window: 34000000-37ffffff
[    5.925255] PCI: Bus 6, cardbus bridge: 0000:00:02.1
[    5.925261]   IO window: 00003400-000034ff
[    5.925268]   IO window: 00003800-000038ff
[    5.925276]   PREFETCH window: 38000000-3bffffff
[    5.925284]   MEM window: 3c000000-3fffffff
[    5.926458] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    5.926466] PCI: setting IRQ 11 as level-triggered
[    5.926473] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    5.927513] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    5.927520] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    5.927623] NET: Registered protocol family 2
[    5.963730] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    5.963952] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    5.964337] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    5.964581] TCP: Hash tables configured (established 16384 bind 8192)
[    5.964589] TCP reno registered
[    5.975911] checking if image is initramfs... it is
[    7.495000] Freeing initrd memory: 6759k freed
[    7.495567] Simple Boot Flag at 0x35 set to 0x1
[    7.496013] audit: initializing netlink socket (disabled)
[    7.496047] audit(1194060918.372:1): initialized
[    7.496392] VFS: Disk quotas dquot_6.5.1
[    7.496446] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.496577] io scheduler noop registered
[    7.496584] io scheduler anticipatory registered
[    7.496590] io scheduler deadline registered
[    7.496618] io scheduler cfq registered (default)
[    7.496640] Limiting direct PCI/PCI transfers.
[    7.497190] isapnp: Scanning for PnP cards...
[    7.850148] isapnp: No Plug & Play device found
[    7.920741] Real Time Clock Driver v1.12ac
[    7.920862] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    7.921065] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    7.921395] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 8250
[    7.922829] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    7.923423] mice: PS/2 mouse device common for all mice
[    7.924888] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    7.925507] input: Macintosh mouse button emulation as /class/input/input0
[    7.925595] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    7.925606] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    7.926045] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    7.941502] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.941518] serio: i8042 AUX port at 0x60,0x64 irq 12
[    7.941873] EISA: Probing bus 0 at eisa.0
[    7.941889] Cannot allocate resource for EISA slot 1
[    7.941897] Cannot allocate resource for EISA slot 2
[    7.941903] Cannot allocate resource for EISA slot 3
[    7.941926] EISA: Detected 0 cards.
[    7.972130] TCP cubic registered
[    7.972151] NET: Registered protocol family 1
[    7.972208] Using IPI No-Shortcut mode
[    7.972359] ACPI: (supports S0 S1 S3 S4 S5)
[    7.972480]   Magic number: 15:598:562
[    7.972591]   hash matches device ptya8
[    7.972682]   hash matches device acpi
[    7.973788] Freeing unused kernel memory: 328k freed
[    7.974494] Time: tsc clocksource has been installed.
[    7.977746] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.647144] Capability LSM initialized
[    9.819462] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    9.819478] ACPI: Processor [CPU] (supports 8 throttling states)
[    9.823574] ACPI: Thermal Zone [THM0] (52 C)
[   11.456153] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   11.456185] PIIX4: chipset revision 1
[   11.456191] PIIX4: not 100% native mode: will probe irqs later
[   11.456207]     ide0: BM-DMA at 0x1c10-0x1c17, BIOS settings: hda:DMA, hdb:pio
[   11.456228]     ide1: BM-DMA at 0x1c18-0x1c1f, BIOS settings: hdc:pio, hdd:DMA
[   11.456244] Probing IDE interface ide0...
[   11.548151] usbcore: registered new interface driver usbfs
[   11.548208] usbcore: registered new interface driver hub
[   11.548266] usbcore: registered new device driver usb
[   11.552167] USB Universal Host Controller Interface driver v3.0
[   11.840642] hda: IC25N020ATDA04-0, ATA DISK drive
[   11.889290] Floppy drive(s): fd0 is 1.44M
[   11.954503] FDC 0 is a National Semiconductor PC87306
[    7.752000] Time: acpi_pm clocksource has been installed.
[    8.208000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    8.224000] Probing IDE interface ide1...
[    8.904000] hdd: MATSHITADVD-RAM UJ-841S, ATAPI CD/DVD-ROM drive
[    8.960000] ide1 at 0x170-0x177,0x376 on irq 15
[    8.988000] SCSI subsystem initialized
[    9.012000] libata version 2.20 loaded.
[    9.020000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    9.020000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.020000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    9.020000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    9.020000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001c20
[    9.020000] usb usb1: configuration #1 chosen from 1 choice
[    9.024000] hub 1-0:1.0: USB hub found
[    9.024000] hub 1-0:1.0: 2 ports detected
[    9.148000] hda: max request size: 128KiB
[    9.176000] hda: 39070080 sectors (20003 MB) w/1806KiB Cache, CHS=38760/16/63, UDMA(33)
[    9.176000] hda: cache flushes not supported
[    9.176000]  hda: hda1 hda2
[    9.240000] hdd: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    9.240000] Uniform CD-ROM driver Revision: 3.20
[    9.576000] Attempting manual resume
[    9.576000] swsusp: Resume From Partition 3:2
[    9.576000] PM: Checking swsusp image.
[    9.576000] PM: Resume from disk failed.
[    9.648000] kjournald starting.  Commit interval 5 seconds
[    9.648000] EXT3-fs: mounted filesystem with ordered data mode.
[   33.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.196000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.216000] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0130]
[   33.216000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   33.216000] Yenta: Routing CardBus interrupts to PCI
[   33.216000] Yenta TI: socket 0000:00:02.0, mfunc 0x00001000, devctl 0x66
[   33.448000] Yenta: ISA IRQ mask 0x04b0, PCI irq 11
[   33.448000] Socket status: 30000006
[   33.448000] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0130]
[   33.448000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   33.448000] Yenta: Routing CardBus interrupts to PCI
[   33.448000] Yenta TI: socket 0000:00:02.1, mfunc 0x00001000, devctl 0x66
[   33.680000] Yenta: ISA IRQ mask 0x04b0, PCI irq 11
[   33.680000] Socket status: 30000020
[   33.764000] Linux agpgart interface v0.102 (c) Dave Jones
[   33.792000] agpgart: Detected an Intel 440BX Chipset.
[   33.796000] agpgart: AGP aperture is 64M @ 0xf8000000
[   33.904000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   33.904000] piix4_smbus 0000:00:07.3: IBM system detected; this module may corrupt your serial eeprom! Refusing to load module!
[   33.904000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[   34.316000] pccard: CardBus card inserted into slot 1
[   34.720000] input: PC Speaker as /class/input/input2
[   35.740000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   35.792000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[   36.476000] parport: PnPBIOS parport detected.
[   36.476000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   36.708000] irda_init()
[   36.708000] NET: Registered protocol family 23
[   36.868000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   36.868000] nsc-ircc, chip->init
[   36.868000] nsc-ircc, Found chip at base=0x02e
[   36.868000] nsc-ircc, driver loaded (Dag Brattli)
[   36.868000] nsc_ircc_open(), can't get iobase of 0x2f8
[   36.868000] nsc-ircc, Found chip at base=0x02e
[   36.868000] nsc-ircc, driver loaded (Dag Brattli)
[   36.868000] nsc_ircc_open(), can't get iobase of 0x2f8
[   36.868000] pnp: Device 00:0e disabled.
[   36.992000] cs: IO port probe 0x100-0x3af: clean.
[   36.992000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   36.992000] cs: IO port probe 0x820-0x8ff: clean.
[   36.992000] cs: IO port probe 0xc00-0xcf7: clean.
[   36.992000] cs: IO port probe 0xa00-0xaff: clean.
[   37.048000] cs: IO port probe 0x100-0x3af: clean.
[   37.048000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   37.048000] cs: IO port probe 0x820-0x8ff: clean.
[   37.048000] cs: IO port probe 0xc00-0xcf7: clean.
[   37.048000] cs: IO port probe 0xa00-0xaff: clean.
[   37.080000] PCI: Enabling device 0000:06:00.0 (0000 -> 0003)
[   37.080000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   37.080000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   37.080000] eth0: Xircom cardbus revision 3 at irq 11
[   37.464000] xircom cardbus adaptor found, registering as eth0, using irq 11
[   37.708000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   37.868000] cs46xx: failure waiting for FIFO command to complete
[   38.272000] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1807kHz
[   38.592000] lp0: using parport0 (interrupt-driven).
[   38.724000] xircom_cb: Link status has changed
[   38.724000] xircom_cb: Link is 100 mbit
[   38.732000] fuse init (API version 7.8)
[   38.784000] NET: Registered protocol family 17
[   38.840000] Adding 979956k swap on /dev/disk/by-uuid/48dcb58a-0e54-48e1-b6f3-270dd3563fc4.  Priority:-1 extents:1 across:979956k
[   39.048000] EXT3 FS on hda1, internal journal
[   39.560000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   40.680000] ttyS1: LSR safety check engaged!
[   40.684000] ttyS1: LSR safety check engaged!
[   40.788000] ACPI: Fatal opcode executed
[   40.788000] pnp: Device 00:0e activated.
[   40.828000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   40.828000] nsc-ircc, chip->init
[   40.828000] nsc-ircc, Found chip at base=0x02e
[   40.828000] nsc-ircc, driver loaded (Dag Brattli)
[   42.240000] NET: Registered protocol family 10
[   42.240000] lo: Disabled Privacy Extensions
[   42.648000] ACPI: Battery Slot [BAT0] (battery present)
[   42.996000] Using specific hotkey driver
[   43.076000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   43.156000] ACPI: ACPI Dock Station Driver
[   43.216000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   43.216000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   43.416000] ACPI: AC Adapter [AC] (on-line)
[   43.520000] input: Power Button (FF) as /class/input/input4
[   43.520000] ACPI: Power Button (FF) [PWRF]
[   43.564000] input: Lid Switch as /class/input/input5
[   43.564000] ACPI: Lid Switch [LID]
[   43.584000] input: Sleep Button (CM) as /class/input/input6
[   43.584000] ACPI: Sleep Button (CM) [SLPB]
[   44.048000] pcc_acpi: loading...
[   54.384000] IBM machine detected. Enabling interrupts during APM calls.
[   54.384000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   54.384000] apm: overridden by ACPI.
[   54.664000] Non-volatile memory driver v1.2
[   54.784000] input: /usr/sbin/thinkpad-keys as /class/input/input7
[   55.360000] ondemand governor failed to load due to too long transition latency
[   56.292000] input: Mouseemu virtual keyboard as /class/input/input8
[   56.292000] input: Mouseemu virtual mouse as /class/input/input9
[   85.956000] ondemand governor failed to load due to too long transition latency
~/%
~/%
~/% tail -1000 /var/log/syslog | grep -i dhclient
Nov  2 22:54:39 krum dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov  2 22:54:39 krum dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov  2 22:54:39 krum dhclient: All rights reserved.
Nov  2 22:54:39 krum dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  2 22:54:39 krum dhclient:
Nov  2 22:54:40 krum dhclient: Listening on LPF/eth0/00:10:a4:aa:d2:9b
Nov  2 22:54:40 krum dhclient: Sending on   LPF/eth0/00:10:a4:aa:d2:9b
Nov  2 22:54:40 krum dhclient: Sending on   Socket/fallback
Nov  2 22:54:44 krum dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  2 22:54:44 krum dhclient: DHCPACK from 192.168.1.1
Nov  2 22:54:44 krum dhclient: bound to 192.168.1.45 -- renewal in 41243 seconds.
~/% 
~/% 
~/% 
~/% date
Fri Nov  2 23:38:30 EDT 2007
~/% 
~/% 
~/% 
~/% ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:A4:AA:D2:9B
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16082 (15.7 KiB)  TX bytes:1390 (1.3 KiB)
          Interrupt:11 Base address:0x3400

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

~/% 
~/% 
~/% 
~/% sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:10:a4:aa:d2:9b
Sending on   LPF/eth0/00:10:a4:aa:d2:9b
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.45 -- renewal in 33837 seconds.
~/% tail -1000 /var/log/syslog | grep -i dhclient
Nov  2 22:54:39 krum dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov  2 22:54:39 krum dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov  2 22:54:39 krum dhclient: All rights reserved.
Nov  2 22:54:39 krum dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  2 22:54:39 krum dhclient:
Nov  2 22:54:40 krum dhclient: Listening on LPF/eth0/00:10:a4:aa:d2:9b
Nov  2 22:54:40 krum dhclient: Sending on   LPF/eth0/00:10:a4:aa:d2:9b
Nov  2 22:54:40 krum dhclient: Sending on   Socket/fallback
Nov  2 22:54:44 krum dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  2 22:54:44 krum dhclient: DHCPACK from 192.168.1.1
Nov  2 22:54:44 krum dhclient: bound to 192.168.1.45 -- renewal in 41243 seconds.
Nov  2 23:39:10 krum dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov  2 23:39:10 krum dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov  2 23:39:10 krum dhclient: All rights reserved.
Nov  2 23:39:10 krum dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  2 23:39:10 krum dhclient:
Nov  2 23:39:11 krum dhclient: Listening on LPF/eth0/00:10:a4:aa:d2:9b
Nov  2 23:39:11 krum dhclient: Sending on   LPF/eth0/00:10:a4:aa:d2:9b
Nov  2 23:39:11 krum dhclient: Sending on   Socket/fallback
Nov  2 23:39:12 krum dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  2 23:39:12 krum dhclient: DHCPACK from 192.168.1.1
Nov  2 23:39:12 krum dhclient: bound to 192.168.1.45 -- renewal in 33837 seconds.
~/% 
~/% 
~/% 
~/% 
~/% ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:A4:AA:D2:9B
          inet addr:192.168.1.45  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20554 (20.0 KiB)  TX bytes:2697 (2.6 KiB)
          Interrupt:11 Base address:0x3400

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by The-Organist on 2007-11-04
I have solved this problem by updating to the latest version of Ubuntu (7.10 I think):popcorn:

---

### Post by PhilipGanchev on 2007-11-05
Thanks.  But this solution is too risky for me.  I need my computer for work, and I don't know what will break when I upgrade (or what will not work if I install afresh).  There are lots of posts complaining about Gutsy, and it may break my system like Edgy did when I upgraded last year.

---

