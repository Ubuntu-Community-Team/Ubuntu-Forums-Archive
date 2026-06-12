---
title: "Internet connection woes"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by marbig on 2006-11-08
Another newbie to Ubuntu 6.06 [dapper]. Downloaded CD and have installed it for dual boot. My computer [dual boot] and my children's, Windows XP(only) are networked.
My original problem was when my computer was in Windows both computers had ICS. Modem was a Alcatel Speedtouch Home with "Always on" (bridged) connection. Yet when my computer was in Ubuntu, I could get connection in Ubuntu. But not my children's.
I was advised that I had to change Modem to PPPoE or get a new one. First option could not be done. So took second. Got a modem router.
Set it up as per instructions and now we have ICS from both computers. Problem now is can get internet from both computers in Windows. I can't connect in Ubuntu. In Ubuntu connection shows as enabled. But can't load web pages in FF.
Have looked at lots of threads...still ](*,) Even disabled IPv6 (I don't think this is my problem)
One poster suggested to another newbie to post 3 items. I have done so also in the hope someone can help me.
Thank you for any assistance offered.
> **_Brand and model of modem router_**
	Netgear ADSL Modem Router DG632

**_Result of Windows XP ipconfig /all_**
Microsoft(R) Windows DOS
(C)Copyright Microsoft Corp 1990-2001.
C:\DOCUME~1\*****>ipconfig /all
Windows IP Configuration
        Host Name . . . . . . . . . . . . : OFFICE
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : vic.bigpond.net.au
Ethernet adapter Ethernet motherboard:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-0B-6A-D0-39-8D
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.11
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Wednesday, 8 November 2006 1:58:08 PM
        Lease Expires . . . . . . . . . . : Thursday, 9 November 2006 1:58:08 PM
C:\DOCUME~1\*****>

**_Contents of Linux /etc/network/interface file_**
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
	auto dsl-provider
	iface dsl-provider inet ppp
	provider dsl-provider
	pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
	


---

### Post by skunkydog on 2006-11-08
what does ```
ifconfig -a
``` on ubuntu tell you?  That's the ipconfig /all on ubuntu

---

### Post by marbig on 2006-11-08
Thanks skunkydog for your reply.

ifconfig -a gives me

@OFFICE:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:6A: D0 :39:8D
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fed0:398d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2783 (2.7 KiB)  TX bytes:4858 (4.7 KiB)
          Interrupt:201 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by marbig on 2006-11-08
With my current set up is reinstalling Ubuntu an option at all and hopefully letting it sort the connections out itself?
Nothing to lose at the moment.  :(

---

### Post by handy on 2006-11-08
So, if I understand correctly you have only one ethernet port on your modem/router?

If that is so, you can get a small network hub for approx' $20- aus'.

That would save you all this hassle!

---

### Post by marbig on 2006-11-08
Hello handy, correct; modem router only has one ethernet connection. But, do use an ethernet switch arranged thus[IMG]http://img.photobucket.com/albums/v61/marbig/arrangement.jpg[/IMG]And still having the hassles.

---

### Post by marbig on 2006-11-08
Subtle *bump*  :roll:

---

### Post by handy on 2006-11-09
you are getting errors according to **ifconfig**?

You should not be.

Be patient, someone  with skill (not me) will sort you out before long.

---

### Post by jonocorp on 2006-11-09
I'm having the exact same problem.

---

### Post by trubblemaker on 2006-11-09
man that sux, k your getting an ip address, so your half way there are you useing dhcp or static routing? 
can you ping the router/switch? 
can you ping the other computer?
getting anything with the command 'route'?
can you please post 'dmesg' in a code block. (post output of command in a code block so I can scroll through it)

---

### Post by marbig on 2006-11-09
> **trubblemaker said:**
> man that sux, k your getting an ip address, so your half way there are you useing dhcp or static routing? 
can you ping the router/switch? 
can you ping the other computer?
getting anything with the command 'route'?
can you please post 'dmesg' in a code block. (post output of command in a code block so I can scroll through it)Thanks trubblemaker for your reply.[LIST]
[*]Using DHCP
[*]Ping router/switch okay - ave .73 ms
[*]Ping other computer okay - ave  .8 ms
[*]Oddly can ping google.com - ave 145.3 ms and can get google webpage. Can do a search and find pages. But will not allow me to open them.[/LIST] ```
tekko@OFFICE:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         mygateway.ar7   0.0.0.0         UG    0      0        0 eth0
tekko@OFFICE:~$
``````
 tekko@OFFICE:~$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fbc70
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000faa60
[17179569.184000] ACPI: RSDT (v001 AMIINT SiS740XX 0x00001000 MSFT 0x0100000b) @ 0x3fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT SiS740XX 0x00000011 MSFT 0x0100000b) @ 0x3fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT SiS740XX 0x00001000 MSFT 0x0100000b) @ 0x3fff00c0
[17179569.184000] ACPI: DSDT (v001    SiS      746 0x00000100 INTL 0x02002024) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1756.236 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.148000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.152000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179571.188000] Memory: 1028688k/1048512k available (1976k kernel code, 19160k reserved, 606k data, 288k init, 131008k highmem)
[17179571.188000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.268000] Calibrating delay using timer specific routine.. 3514.76 BogoMIPS (lpj=7029524)
[17179571.268000] Security Framework v1.0.0 initialized
[17179571.268000] SELinux:  Disabled at boot.
[17179571.268000] Mount-cache hash table entries: 512
[17179571.268000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179571.268000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179571.268000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.268000] CPU: L2 Cache: 256K (64 bytes/line)
[17179571.268000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[17179571.268000] mtrr: v2.0 (20020519)
[17179571.268000] CPU: AMD Sempron(tm) 2500+ stepping 01
[17179571.268000] Enabling fast FPU save and restore... done.
[17179571.268000] Enabling unmasked SIMD FPU exception support... done.
[17179571.268000] Checking 'hlt' instruction... OK.
[17179571.284000] checking if image is initramfs... it is
[17179571.900000] Freeing initrd memory: 6841k freed
[17179571.916000] ACPI: Looking for DSDT ... not found!
[17179571.916000] ENABLING IO-APIC IRQs
[17179571.916000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.060000] NET: Registered protocol family 16
[17179572.060000] EISA bus registered
[17179572.060000] ACPI: bus type pci registered
[17179572.060000] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[17179572.060000] PCI: Using configuration type 1
[17179572.060000] ACPI: Subsystem revision 20051216
[17179572.064000] ACPI: Interpreter enabled
[17179572.064000] ACPI: Using IOAPIC for interrupt routing
[17179572.064000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.064000] PCI: Probing PCI hardware (bus 00)
[17179572.068000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[17179572.068000] Enabling SiS 96x SMBus.
[17179572.068000] Boot video device is 0000:01:00.0
[17179572.068000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.084000] ACPI: Power Resource [URP1] (off)
[17179572.084000] ACPI: Power Resource [URP2] (off)
[17179572.084000] ACPI: Power Resource [FDDP] (off)
[17179572.084000] ACPI: Power Resource [LPTP] (off)
[17179572.084000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.084000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.084000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.084000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.084000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.088000] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179572.088000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.088000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.088000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.088000] pnp: PnP ACPI init
[17179572.088000] pnp: PnP ACPI: found 11 devices
[17179572.088000] PnPBIOS: Disabled by ACPI PNP
[17179572.088000] PCI: Using ACPI for IRQ routing
[17179572.088000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.092000] PCI: Bridge: 0000:00:01.0
[17179572.092000]   IO window: disabled.
[17179572.092000]   MEM window: cdd00000-cfefffff
[17179572.092000]   PREFETCH window: c5a00000-cdbfffff
[17179572.092000] audit: initializing netlink socket (disabled)
[17179572.092000] audit(1163063518.092:1): initialized
[17179572.096000] highmem bounce pool size: 64 pages
[17179572.096000] VFS: Disk quotas dquot_6.5.1
[17179572.096000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.096000] Initializing Cryptographic API
[17179572.096000] io scheduler noop registered
[17179572.096000] io scheduler anticipatory registered
[17179572.096000] io scheduler deadline registered
[17179572.096000] io scheduler cfq registered
[17179572.096000] isapnp: Scanning for PnP cards...
[17179572.448000] isapnp: No Plug & Play device found
[17179572.464000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179572.464000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.464000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.464000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.464000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.464000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.464000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.464000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.464000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.464000] mice: PS/2 mouse device common for all mice
[17179572.464000] EISA: Probing bus 0 at eisa.0
[17179572.464000] EISA: Detected 0 cards.
[17179572.464000] NET: Registered protocol family 2
[17179572.488000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.500000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.500000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179572.500000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.500000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.500000] TCP reno registered
[17179572.500000] TCP bic registered
[17179572.500000] NET: Registered protocol family 1
[17179572.500000] NET: Registered protocol family 8
[17179572.500000] NET: Registered protocol family 20
[17179572.500000] Using IPI Shortcut mode
[17179572.504000] ACPI wakeup devices:
[17179572.504000] PCI0 PS2M PS2K UAR1 USB1 USB2 EHCI  LAN  MDM  AUD
[17179572.504000] ACPI: (supports S0 S1 S4 S5)
[17179572.504000] Freeing unused kernel memory: 288k freed
[17179572.556000] vga16fb: initializing
[17179572.556000] vga16fb: mapped to 0xc00a0000
[17179572.692000] Console: switching to colour frame buffer device 80x25
[17179572.692000] fb0: VGA16 VGA frame buffer device
[17179573.820000] Capability LSM initialized
[17179574.468000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179574.468000] SIS5513: chipset revision 0
[17179574.468000] SIS5513: not 100% native mode: will probe irqs later
[17179574.468000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179574.468000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179574.468000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179574.468000] Probing IDE interface ide0...
[17179574.760000] hda: WDC WD400BB-00DEA0, ATA DISK drive
[17179575.432000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.440000] Probing IDE interface ide1...
[17179576.180000] hdc: LITE-ON DVDRW SOHW-1673S, ATAPI CD/DVD-ROM drive
[17179576.852000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.856000] hda: max request size: 128KiB
[17179576.868000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.868000] hda: cache flushes not supported
[17179576.868000]  hda: hda1 hda2 hda3 < hda5 hda6 >
[17179576.904000] hdc: ATAPI 8X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.904000] Uniform CD-ROM driver Revision: 3.20
[17179577.252000] usbcore: registered new driver usbfs
[17179577.256000] usbcore: registered new driver hub
[17179577.256000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.256000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 169
[17179577.256000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179577.256000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179577.256000] ohci_hcd 0000:00:03.0: irq 169, io mem 0xcfffd000
[17179577.292000] ieee1394: Initialized config rom entry `ip1394'
[17179577.312000] hub 1-0:1.0: USB hub found
[17179577.312000] hub 1-0:1.0: 3 ports detected
[17179577.416000] ACPI: PCI Interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 177
[17179577.416000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179577.416000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179577.416000] ohci_hcd 0000:00:03.1: irq 177, io mem 0xcfffe000
[17179577.472000] hub 2-0:1.0: USB hub found
[17179577.472000] hub 2-0:1.0: 3 ports detected
[17179577.576000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 185
[17179577.576000] ehci_hcd 0000:00:03.2: EHCI Host Controller
[17179577.576000] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[17179577.576000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179577.576000] ehci_hcd 0000:00:03.2: irq 185, io mem 0xcffff000
[17179577.576000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.576000] hub 3-0:1.0: USB hub found
[17179577.576000] hub 3-0:1.0: 6 ports detected
[17179577.680000] ohci1394: $Rev: 1313 $ Ben Collins <[EMAIL="bcollins@debian.org"]bcollins@debian.org[/EMAIL]>
[17179577.680000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179577.732000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[193]  MMIO=[cfffb800-cfffbfff]  Max Packet=[2]
[17179577.740000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
[17179577.808000] Attempting manual resume
[17179577.844000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.860000] kjournald starting.  Commit interval 5 seconds
[17179578.384000] usb 2-1: new low speed USB device using ohci_hcd and address 2[17179579.012000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195]
[17179591.216000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.248000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.252000] i2c-sis96x version 1.0.0
[17179591.252000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[17179591.336000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.348000] agpgart: Detected SiS 741 chipset
[17179591.356000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179591.460000] sis900.c: v1.08.09 Sep. 19 2005
[17179591.464000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179591.464000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[17179591.476000] 0000:00:04.0: Using transceiver found at address 1 as default
[17179591.476000] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 201, 00:0b:6a:d0:39:8d.
[17179591.588000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 209
[17179591.720000] parport: PnPBIOS parport detected.
[17179591.720000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179591.804000] Real Time Clock Driver v1.12
[17179591.904000] intel8x0_measure_ac97_clock: measured 55997 usecs
[17179591.904000] intel8x0: clocking to 48000
[17179591.908000] usbcore: registered new driver hiddev
[17179591.928000] Floppy drive(s): fd0 is 1.44M
[17179591.944000] FDC 0 is a post-1991 82077
[17179591.996000] nvidia: module license 'NVIDIA' taints kernel.
[17179592.000000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[17179592.000000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179592.376000] input: PC Speaker as /class/input/input1
[17179592.664000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179592.720000] ts: Compaq touchscreen protocol output
[17179593.792000] NET: Registered protocol family 17
[17179594.712000] eth0: Media Link On 100mbps full-duplex
[17179597.328000] NET: Registered protocol family 10
[17179597.328000] lo: Disabled Privacy Extensions
[17179597.328000] IPv6 over IPv4 tunneling driver
[17179601.932000] drivers/usb/input/hid-core.c: timeout initializing reports
[17179601.932000]
[17179601.932000] input: Logitech Inc. WingMan Force 3D as /class/input/input3
[17179601.932000] input: USB HID v1.00 Joystick [Logitech Inc. WingMan Force 3D] on usb-0000:00:03.1-1
[17179601.932000] usbcore: registered new driver usbhid
[17179601.932000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179602.400000] lp0: using parport0 (interrupt-driven).
[17179602.468000] SCSI subsystem initialized
[17179602.480000] sbp2: $Rev: 1306 $ Ben Collins <[EMAIL="bcollins@debian.org"]bcollins@debian.org[/EMAIL]>
[17179602.480000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179602.480000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179602.552000] Adding 337292k swap on /dev/hda6.  Priority:-1 extents:1 across:337292k
[17179602.696000] EXT3 FS on hda2, internal journal
[17179602.884000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179602.884000] md: bitmap version 4.39
[17179603.464000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[17179608.152000] eth0: no IPv6 routers present
[17179610.940000] ACPI: Power Button (FF) [PWRF]
[17179610.940000] ACPI: Power Button (CM) [PWRB]
[17179611.056000] ibm_acpi: ec object not found
[17179611.092000] pcc_acpi: loading...
[17179616.720000] ppdev: user-space parallel port driver
[17179617.000000] apm: BIOS not found.
[17179620.384000] Bluetooth: Core ver 2.8
[17179620.384000] NET: Registered protocol family 31
[17179620.384000] Bluetooth: HCI device and connection manager initialized
[17179620.384000] Bluetooth: HCI socket layer initialized
[17179620.440000] Bluetooth: L2CAP ver 2.8
[17179620.440000] Bluetooth: L2CAP socket layer initialized
[17179620.480000] Bluetooth: RFCOMM socket layer initialized
[17179620.480000] Bluetooth: RFCOMM TTY layer initialized
[17179620.480000] Bluetooth: RFCOMM ver 1.7
[17179634.020000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179634.636000] ISO 9660 Extensions: RRIP_1991A
tekko@OFFICE:~$
```

---

### Post by skunkydog on 2006-11-09
So to recap:
on ubuntu, you are getting an IP, everything works on your intranet, but you can only get out to google?

maybe your nameserver?

try this:
1. ping [www.yahoo.com](www.yahoo.com)
2. ping 209.73.186.238 (the address i get for yahoo.com)

---

### Post by trubblemaker on 2006-11-09
I forget if your on dapper or on edgy, If you where on edgy this would be more likely. but you can try blacklisting ipv6 it's  more of a browsing issue than net issue, and kinda fits your problem.  ipv6 isn't completely implemented and would give mixed results if your router didn't make things work properly and you can ping things.

so to black list it:

add

"blacklist ipv6"

to /etc/modprobe.d/blacklist

you will need to use sudo and your favorite editor.("sudo vim /etc/modprobe.d/blacklist")  To be honest, it might not be the issue but lets rule it out.  

Then do a reboot and try surfing again. 
*note* although it is possible to not reboot _sometimes_ those methods don't work properly

---

### Post by marbig on 2006-11-09
Thanks skunkydog and trubblemaker for your help. It was the blacklisting of ipv6 that did the trick. Typing this post through Ubuntu instead of Win XP.

---

### Post by trubblemaker on 2006-11-09
for those that love ipv6, there are otherways of getting rid of ipv6 actually it's your browser that's messing up, fire fox tries to use ipv6 and you can just shut it off in firefox, but I"m convinced that if ipv6 isn't yet fully implemented then why use it?

---

### Post by handy on 2006-11-09
I have to do the ***about:config*** thing to disable IPv6 in firefox, or I can not browse, period.

I put it in [this how-to]("http://ubuntuforums.org/showthread.php?t=282034") for anyone that needs it. 

I don't have to go to the trouble of blacklisting IPv6, on my machines anyway, & the speed & function of web browsing is fine.

---

### Post by loclei on 2006-11-12
> **marbig said:**
> Thanks skunkydog for your reply.

ifconfig -a gives me

@OFFICE:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:6A: D0 :39:8D

i think in this lies your problem
the mac address which contains spaces
it should be 
```

hwaddr 00:0B:6A:D0:39:8D

```

you can change the mac adress with sudo gedit /etc/network/interfaces
and add a line after the gateway  line that looks like this:
```

hwaddress ether 00:0B:6A:D0:39:8D

```

---

### Post by marbig on 2006-11-12
Oh but if it were so loclei and my problems were solved.

'HWaddr 00:0B:6A: D0 :39:8D' was as I posted it. I put the gaps in. Without the gaps it became....   HWaddr 00:0B:6A:D0:39:8D on the post.

:(

---

### Post by marbig on 2006-11-13
:D:D:D:D Had a win. Added my ISP's primary and secondary DNS addresses to  System==>Administration==>Networking==>DNS==>Search Domains.

After downloads I do get an error message:```

W: Duplicate sources.list entry http://au.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://au.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
```Anyone any clues what this is?

---

