---
title: "Installing New Network Card"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by kramerkeller on 2007-03-10
I am wanting to install a second and third network card.  I physically installed them and am wondering what to do from there.

My overall goal is to set up a local dns so I can access the websites I host locally from my other local machines, but that may be for a different forum.

I would appreciate any help on installing the network cards.

---

### Post by Mr. C. on 2007-03-10
[ deleted ]

---

### Post by Mr. C. on 2007-03-10
[ deleted ]

---

### Post by kramerkeller on 2007-03-10
In this thread I only want to know how to install a network card.  I was simply explaining my end goal.  In the other thread I asked about the dns server.  I still don't know how to install two new network cards.

I would like to know how to install 2 new network cards.  That didn't seem like an appropriate question for the other thread.  Is this where I should ask about that?

---

### Post by Mr. C. on 2007-03-10
Apologies - I deleted my two previous posts.  I don't know what happened to the forums here, but I saw the same post 3 or 4 times.

Anyway, let's get your problem solved.

Do you need to know how to physically install them, or simply the configuration side?

MrC

---

### Post by kramerkeller on 2007-03-11
I physically installed them, but I don't see a eth1 or eth2 just an eth0.

I have done a lot of stuff with linux, but with hardware I suppose, I am a complete newbie.  That is why I loved ubuntu, I didn't have to worry about that stuff.  Anyhow, I put the cards into the pci slots, but I have no clue from there.  I thought iftab or mtab or fstab would pick them up, but I don't see anything.

Any help would be appreciated.

---

### Post by Mr. C. on 2007-03-11
Ok, let's see what we can do.

Not knowing what cards you have installed, let's find out.  Please show output from:
```

dmesg
ifconfig -a
lspci
lspci -n
```

This will tell us what cards are availabe in the PCI space (if these are old ISA cards, they will not show up this way). 

btw. the iftab is the only network relevant file.  The files iftab and mtab are all file system related.

MrC

---

### Post by kramerkeller on 2007-03-11
Here is all the info.  I have 3 cards in total.  I guess one may not be working.  I could take one out at a time and try and figure it out I suppose.  I know the one is working cause I can get online.  Anyhow, I have no clue what all this stuff is, so let me know what to do to get the card installed.


root@createcandor:/# dmesg
[42949372.960000] Linux version 2.6.17-11-server (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:53:33 UTC 2007 (Ubuntu 2.6.17-11.35-server)
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[42949372.960000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[42949372.960000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[42949372.960000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[42949372.960000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[42949372.960000]  BIOS-e820: 00000000040ffc00 - 0000000018000000 (usable)
[42949372.960000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[42949372.960000] 0MB HIGHMEM available.
[42949372.960000] 384MB LOWMEM available.
[42949372.960000] On node 0 totalpages: 98304
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   Normal zone: 94208 pages, LIFO batch:31
[42949372.960000] DMI 2.1 present.
[42949372.960000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ac0
[42949372.960000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000000 PTL  0x01000000) @ 0x040fda87
[42949372.960000] ACPI: FADT (v001 GATEWA TABOR II 0x19990422 PTL  0x000f4240) @ 0x040ff78c
[42949372.960000] ACPI: DSDT (v001 GATEWA TABOR II 0x00000000 MSFT 0x01000000) @ 0x00000000
[42949372.960000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[42949372.960000] ACPI: Disabling ACPI support
[42949372.960000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7fe7000)
[42949372.960000] Built 1 zonelists
[42949372.960000] Kernel command line: root=/dev/hdb1 ro quiet splash
[42949372.960000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[42949372.960000] mapped APIC to ffffd000 (0130a000)
[42949372.960000] Enabling fast FPU save and restore... done.
[42949372.960000] Enabling unmasked SIMD FPU exception support... done.
[42949372.960000] Initializing CPU#0
[42949372.960000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 498.687 MHz processor.
[   32.860677] Using tsc for high-res timesource
[   32.862120] Console: colour VGA+ 80x25
[   32.863274] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.864477] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.919013] Memory: 380136k/393216k available (1904k kernel code, 12432k reserved, 1072k data, 312k init, 0k highmem)
[   32.919030] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.060501] Calibrating delay using timer specific routine.. 998.62 BogoMIPS (lpj=4993118)
[   33.060660] Security Framework v1.0.0 initialized
[   33.060687] SELinux:  Disabled at boot.
[   33.060747] Mount-cache hash table entries: 512
[   33.061218] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   33.061248] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   33.061283] CPU: L1 I cache: 16K, L1 D cache: 16K
[   33.061294] CPU: L2 cache: 512K
[   33.061305] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   33.061375] Checking 'hlt' instruction... OK.
[   33.100714] SMP alternatives: switching to UP code
[   33.101093] Freeing SMP alternatives: 16k freed
[   33.101509] checking if image is initramfs... it is
[   34.825861] Freeing initrd memory: 5176k freed
[   34.825884] CPU0: Intel Pentium III (Katmai) stepping 02
[   34.825906] SMP motherboard not detected.
[   34.825915] Local APIC not detected. Using dummy APIC emulation.
[   34.826156] Brought up 1 CPUs
[   34.826227] migration_cost=0
[   34.827324] NET: Registered protocol family 16
[   34.827428] EISA bus registered
[   34.827809] PCI: PCI BIOS revision 2.10 entry at 0xfd983, last bus=1
[   34.827831] PCI: Using configuration type 1
[   34.827839] Setting up standard PCI resources
[   34.829141] ACPI: Interpreter disabled.
[   34.829158] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.829187] pnp: PnP ACPI: disabled
[   34.829200] PnPBIOS: Scanning system for PnP BIOS support...
[   34.829247] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
[   34.829262] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e31, dseg 0x400
[   34.837000] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   34.837210] PCI: Probing PCI hardware
[   34.837225] PCI: Probing PCI hardware (bus 00)
[   34.837645] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[   34.837792] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   34.837805] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   34.838384] Boot video device is 0000:01:00.0
[   34.840596] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   34.840691] PCI: Cannot allocate resource region 0 of device 0000:00:0f.0
[   34.843086] pnp: 00:00: ioport range 0x370-0x371 has been reserved
[   34.843131] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   34.843145] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   34.843157] pnp: 00:0a: ioport range 0x7000-0x700f has been reserved
[   34.844277] PCI: Failed to allocate mem resource #6:10000@fd000000 for 0000:01:00.0
[   34.844290] PCI: Bridge: 0000:00:01.0
[   34.844297]   IO window: disabled.
[   34.844311]   MEM window: f5000000-f5ffffff
[   34.844323]   PREFETCH window: fc000000-fcffffff
[   34.844417] NET: Registered protocol family 2
[   34.920386] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   34.920771] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   34.921319] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   34.921589] TCP: Hash tables configured (established 16384 bind 8192)
[   34.921601] TCP reno registered
[   34.924456] audit: initializing netlink socket (disabled)
[   34.924494] audit(1173662791.030:1): initialized
[   34.924968] VFS: Disk quotas dquot_6.5.1
[   34.925052] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.925250] Initializing Cryptographic API
[   34.925268] io scheduler noop registered
[   34.925300] io scheduler anticipatory registered
[   34.925326] io scheduler deadline registered (default)
[   34.925378] io scheduler cfq registered
[   34.925393] Limiting direct PCI/PCI transfers.
[   34.926185] isapnp: Scanning for PnP cards...
[   35.283326] isapnp: No Plug & Play device found
[   35.415489] Real Time Clock Driver v1.12ac
[   35.415789] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.416121] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.416566] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.418707] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.419439] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.420394] mice: PS/2 mouse device common for all mice
[   35.423158] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.423949] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.423968] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.424573] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   35.424586] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   35.426754] serio: i8042 AUX port at 0x60,0x64 irq 12
[   35.426835] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.427630] EISA: Probing bus 0 at eisa.0
[   35.427655] Cannot allocate resource for EISA slot 1
[   35.427702] Cannot allocate resource for EISA slot 7
[   35.427711] Cannot allocate resource for EISA slot 8
[   35.427720] EISA: Detected 0 cards.
[   35.428519] TCP bic registered
[   35.428557] NET: Registered protocol family 1
[   35.428580] NET: Registered protocol family 8
[   35.428589] NET: Registered protocol family 20
[   35.428673] Using IPI No-Shortcut mode
[   35.430165] Freeing unused kernel memory: 312k freed
[   35.627725] Capability LSM initialized
[   37.229028] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   37.229071] PIIX4: chipset revision 1
[   37.229080] PIIX4: not 100% native mode: will probe irqs later
[   37.229103]     ide0: BM-DMA at 0x14e0-0x14e7, BIOS settings: hda:pio, hdb:DMA
[   37.229138]     ide1: BM-DMA at 0x14e8-0x14ef, BIOS settings: hdc:DMA, hdd:pio
[   37.229165] Probing IDE interface ide0...
[   37.529692] hda: QUANTUM FIREBALL CX13.6A, ATA DISK drive
[   37.829621] hdb: WDC WD400JB-00ENA0, ATA DISK drive
[   37.890941] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   37.891123] Probing IDE interface ide1...
[   38.679441] hdc: TOSHIBA CD-ROM XM-6202BH, ATAPI CD/DVD-ROM drive
[   39.039504] ide1 at 0x170-0x177,0x376 on irq 15
[   39.071010] hda: max request size: 128KiB
[   39.073021] hda: 26760384 sectors (13701 MB) w/418KiB Cache, CHS=26548/16/63, UDMA(33)
[   39.073045] hda: cache flushes not supported
[   39.073156]  hda:
[   39.095206] hdb: max request size: 128KiB
[   39.178053] hdb: 78165360 sectors (40020 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
[   39.178079] hdb: cache flushes not supported
[   39.178204]  hdb: hdb1 hdb2 < hdb5 >
[   39.362972] hdc: ATAPI 32X CD-ROM drive, 256kB Cache, DMA
[   39.363001] Uniform CD-ROM driver Revision: 3.20
[   39.809345] usbcore: registered new driver usbfs
[   39.809428] usbcore: registered new driver hub
[   39.816270] USB Universal Host Controller Interface driver v3.0
[   39.816403] PCI: Found IRQ 9 for device 0000:00:07.2
[   39.816436] PCI: Sharing IRQ 9 with 0000:00:10.0
[   39.816467] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   39.816803] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   39.816858] uhci_hcd 0000:00:07.2: irq 9, io base 0x000014c0
[   39.817156] usb usb1: configuration #1 chosen from 1 choice
[   39.817262] hub 1-0:1.0: USB hub found
[   39.817301] hub 1-0:1.0: 2 ports detected
[   40.042540] Attempting manual resume
[   40.097963] EXT3-fs: INFO: recovery required on readonly filesystem.
[   40.097981] EXT3-fs: write access will be enabled during recovery.
[   42.865179] kjournald starting.  Commit interval 5 seconds
[   42.865229] EXT3-fs: hdb1: orphan cleanup on readonly fs
[   42.865255] ext3_orphan_cleanup: deleting unreferenced inode 4669446
[   42.865344] ext3_orphan_cleanup: deleting unreferenced inode 4669445
[   42.865374] ext3_orphan_cleanup: deleting unreferenced inode 4669444
[   42.865403] ext3_orphan_cleanup: deleting unreferenced inode 4669443
[   42.865431] ext3_orphan_cleanup: deleting unreferenced inode 4669442
[   42.865454] EXT3-fs: hdb1: 5 orphan inodes deleted
[   42.865463] EXT3-fs: recovery complete.
[   42.874903] EXT3-fs: mounted filesystem with ordered data mode.
[   50.046587] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.058933] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.532981] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   51.763353] PCI: Found IRQ 11 for device 0000:00:0e.0
[   51.763384] PCI: Sharing IRQ 11 with 0000:00:0c.0
[   51.763403] PCI: Sharing IRQ 11 with 0000:01:00.0
[   51.763425] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[   51.763444] 0000:00:0e.0: 3Com PCI 3c900 Cyclone 10Mbps TPC at d884e000.
[   51.802271] Linux agpgart interface v0.101 (c) Dave Jones
[   51.832393] agpgart: Detected an Intel 440BX Chipset.
[   51.838668] agpgart: AGP aperture is 64M @ 0xf8000000
[   52.771695] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[   52.771825] PCI: Found IRQ 9 for device 0000:00:10.0
[   52.771849] PCI: Sharing IRQ 9 with 0000:00:07.2
[   52.777386] eth1: VIA Rhine III at 0x11000, 00:0e:2e:0c:de:1c, IRQ 9.
[   52.778120] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   53.292967] input: PC Speaker as /class/input/input0
[   54.065618] PCI: Found IRQ 11 for device 0000:00:0c.0
[   54.065651] PCI: Sharing IRQ 11 with 0000:00:0e.0
[   54.065668] PCI: Sharing IRQ 11 with 0000:01:00.0
[   54.327127] parport: PnPBIOS parport detected.
[   54.327203] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   54.812441] PCI: Found IRQ 11 for device 0000:00:0e.0
[   54.812474] PCI: Sharing IRQ 11 with 0000:00:0c.0
[   54.812493] PCI: Sharing IRQ 11 with 0000:01:00.0
[   54.813205] eth0:  setting full-duplex.
[   55.425875] lp0: using parport0 (interrupt-driven).
[   55.665992] Adding 1124508k swap on /dev/disk/by-uuid/1bb7b649-f7ae-476a-946c-e8a6b65ccf00.  Priority:-1 extents:1 across:1124508k
[   55.899235] EXT3 FS on hdb1, internal journal
[   55.942936] NET: Registered protocol family 17
[   59.417923] NET: Registered protocol family 10
[   59.418247] lo: Disabled Privacy Extensions
[   59.418751] IPv6 over IPv4 tunneling driver
[   69.802624] eth0: no IPv6 routers present
root@createcandor:/# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:04:98:AD:2D  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fe98:ad2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21497 (20.9 KiB)  TX bytes:83952 (81.9 KiB)
          Interrupt:11 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0E:2E:0C:DE:1C  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@createcandor:/# lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
00:0e.0 Ethernet controller: 3Com Corporation 3c900B-TPC Etherlink XL [Cyclone] (rev 04)
00:0f.0 Host bridge: MYSON Technology Inc Unknown device 0c03
00:10.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)
root@createcandor:/# lspci -n
00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:07.0 0601: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 02)
00:0c.0 0401: 1274:1371 (rev 06)
00:0e.0 0200: 10b7:9006 (rev 04)
00:0f.0 0600: 1516:0c03
00:10.0 0200: 1106:3106 (rev 8b)
01:00.0 0300: 10de:0020 (rev 04)

---

### Post by Mr. C. on 2007-03-11
Eth1 is being found, its a via Rhine.

```
[ 52.777386] eth1: VIA Rhine III at 0x11000, 00:0e:2e:0c:de:1c, IRQ 9.
[ 52.778120] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
```

Have you tried to configure eth1's IP information?  I see nothing assigned:
```

eth1 Link encap:Ethernet HWaddr 00:0E:2E:0CE:1C
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
```

I see no third ethernet card (eth2).  Is it and ISA or EISA card?

MrC

---

### Post by kramerkeller on 2007-03-11
No, I haven't done anything.  I have no clue what to do.  I am reading up on the other stuff you gave me and in the other post and it is very interresting.

How do I configure eth1's IP information.  I am eventually going to want to use it as a gateway or dhcp server.

---

### Post by Mr. C. on 2007-03-11
Ah, ok!

Go to System->Administration->Networking

Select the Wired connection that is your Rhine card.  Configure it's IP address, etc.

I presume you know what you want your network to look like, and what you are going to do with those three cards.

MrC

---

### Post by kramerkeller on 2007-03-12
Oh, I don't have a GUI.  I do everything from command line.  The machine is a server for hosting so I didn't want to bog it down.  How would I configure this without the GUI.

And I got my DNS up, I will be posting again in the other forum with a few questions.  Your class notes were really good.

---

### Post by Mr. C. on 2007-03-12
The GUI simply modifies the files /etc/networking/interfaces and /etc/resolv.conf

Edit them and add your IP, etc. info such as:
```

auto eth1
iface eth1 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
```

Don't add the gateway should you already have a gateway for eth0 or other interface.  There can be only one.

Your resolv.conf should look like:

```
search yourdomain.com
nameserver 192.168.0.10
```

Place your nameserver's IP address after nameserver.  You can have up to 3 nameserver lines.  Place the fastest ones first.  But this file will likely be correct already, since you have eth0 already configured.

Then just bring up the interface:

```
ifup eth1
```

> Your class notes were really good.
Thanks!
MrC

---

