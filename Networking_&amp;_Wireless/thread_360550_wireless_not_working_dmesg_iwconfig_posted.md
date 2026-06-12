---
title: "wireless not working dmesg iwconfig posted"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by jlamr on 2007-02-13
Hi all, I'm having problems getting my laptop to connect to my wireless network. The router is a linksys, and the pmcia ethernet card is dynex (generic best buy brand), I believe it uses the atheros chipset, tho, not so sure at this point.
```

here's iwconfig|grep eth0

eth0      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan eth0
eth0      No scan results

lspci
00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
00:00.1 Multimedia audio controller: Intel Corporation 82440MX AC'97 Audio Controller
00:00.2 Modem: Intel Corporation 82440MX AC'97 Modem Controller
00:02.0 VGA compatible controller: Silicon Motion, Inc. SM712 LynxEM+ (rev a0)
00:03.0 CardBus bridge: O2 Micro, Inc. OZ6812 CardBus Controller (rev 05)
00:07.0 ISA bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller
00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller
00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
01:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

and dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000bfe0000 (usable)
[17179569.184000]  BIOS-e820: 000000000bfe0000 - 000000000bff0000 (reserved)
[17179569.184000]  BIOS-e820: 000000000bff0000 - 000000000bff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000bff8000 - 000000000c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 191MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 49120
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 45024 pages, LIFO batch:7
[17179569.184000] DMI not present or invalid.
[17179569.184000] ACPI: RSDP (v000 IBM                                   ) @ 0x000fe030
[17179569.184000] ACPI: RSDT (v001 IBM    ATLANTA2 0x00000001 IBM  0x00000000) @ 0x0bff0000
[17179569.184000] ACPI: FADT (v001 IBM    ATLANTA2 0x00000001 IBM  0x00000000) @ 0x0bff0088
[17179569.184000] ACPI: BOOT (v001 IBM    ATLANTA2 0x00000001 IBM  0x00000000) @ 0x0bff002c
[17179569.184000] ACPI: DSDT (v001    IBM ThinkPad 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01189000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 548.943 MHz processor.
[   15.577303] Using tsc for high-res timesource
[   15.579140] Console: colour VGA+ 80x25
[   15.579808] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.580588] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   15.605738] Memory: 184936k/196480k available (1910k kernel code, 11084k reserved, 1070k data, 308k init, 0k highmem)
[   15.605752] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.685175] Calibrating delay using timer specific routine.. 1099.43 BogoMIPS (lpj=2198870)
[   15.685310] Security Framework v1.0.0 initialized
[   15.685333] SELinux:  Disabled at boot.
[   15.685386] Mount-cache hash table entries: 512
[   15.685808] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.685836] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.685870] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.685880] CPU: L2 cache: 128K
[   15.685889] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   15.685957] Checking 'hlt' instruction... OK.
[   15.701391] SMP alternatives: switching to UP code
[   15.701811] Freeing SMP alternatives: 16k freed
[   15.702317] checking if image is initramfs... it is
[   17.514902] Freeing initrd memory: 5564k freed
[   17.514926] CPU0: Intel Celeron (Coppermine) stepping 03
[   17.514945] SMP motherboard not detected.
[   17.514954] Local APIC not detected. Using dummy APIC emulation.
[   17.515193] Brought up 1 CPUs
[   17.515252] migration_cost=0
[   17.516341] NET: Registered protocol family 16
[   17.516447] EISA bus registered
[   17.530960] PCI: PCI BIOS revision 2.10 entry at 0xf0200, last bus=0
[   17.530979] PCI: Using configuration type 1
[   17.530986] Setting up standard PCI resources
[   17.532245] ACPI: Interpreter disabled.
[   17.532262] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.532290] pnp: PnP ACPI: disabled
[   17.532299] PnPBIOS: Scanning system for PnP BIOS support...
[   17.532387] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6b90
[   17.532400] PnPBIOS: PnP BIOS version 1.0, entry 0xfa000:0x0, dseg 0xf0000
[   17.541221] PnPBIOS: get_dev_node: invalid handle
[   17.541285] PnPBIOS: 12 nodes reported by PnP BIOS; 12 recorded by driver
[   17.541492] PCI: Probing PCI hardware
[   17.541504] PCI: Probing PCI hardware (bus 00)
[   17.541939] Boot video device is 0000:00:02.0
[   17.542134] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[   17.543977] PCI: Using IRQ router PIIX/ICH [8086/7198] at 0000:00:07.0
[   17.555044] pnp: 00:08: ioport range 0xf000-0xf03f has been reserved
[   17.555058] pnp: 00:08: ioport range 0xf100-0xf11f has been reserved
[   17.555838] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   17.555873] PCI: Bus 1, cardbus bridge: 0000:00:03.0
[   17.555883]   IO window: 00001000-000010ff
[   17.555893]   IO window: 00001400-000014ff
[   17.555904]   PREFETCH window: 10000000-11ffffff
[   17.555915]   MEM window: 12000000-13ffffff
[   17.555950] PCI: Found IRQ 11 for device 0000:00:03.0
[   17.555961] PCI: Sharing IRQ 11 with 0000:00:00.1
[   17.555971] PCI: Sharing IRQ 11 with 0000:00:00.2
[   17.556072] NET: Registered protocol family 2
[   17.592849] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   17.593188] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   17.593459] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   17.593623] TCP: Hash tables configured (established 8192 bind 4096)
[   17.593633] TCP reno registered
[   17.594363] Simple Boot Flag at 0x6e set to 0x1
[   17.596334] audit: initializing netlink socket (disabled)
[   17.596377] audit(1171377422.204:1): initialized
[   17.596925] VFS: Disk quotas dquot_6.5.1
[   17.597000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.597183] Initializing Cryptographic API
[   17.597201] io scheduler noop registered
[   17.597226] io scheduler anticipatory registered
[   17.597248] io scheduler deadline registered
[   17.597294] io scheduler cfq registered (default)
[   17.598074] isapnp: Scanning for PnP cards...
[   17.952660] isapnp: No Plug & Play device found
[   18.107245] Real Time Clock Driver v1.12ac
[   18.107489] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.110800] PCI: Found IRQ 11 for device 0000:00:00.2
[   18.110819] PCI: Sharing IRQ 11 with 0000:00:00.1
[   18.111087] mice: PS/2 mouse device common for all mice
[   18.113587] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.114075] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.114090] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.114705] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   18.116814] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.117049] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.117830] EISA: Probing bus 0 at eisa.0
[   18.117853] Cannot allocate resource for EISA slot 1
[   18.117891] Cannot allocate resource for EISA slot 7
[   18.117900] Cannot allocate resource for EISA slot 8
[   18.117908] EISA: Detected 0 cards.
[   18.118210] TCP bic registered
[   18.118247] NET: Registered protocol family 1
[   18.118273] NET: Registered protocol family 8
[   18.118282] NET: Registered protocol family 20
[   18.118356] Using IPI No-Shortcut mode
[   18.120081] Freeing unused kernel memory: 308k freed
[   18.156163] input: AT Translated Set 2 keyboard as /class/input/input0
[   19.581402] Capability LSM initialized
[   22.032499] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   22.032537] PIIX4: chipset revision 0
[   22.032546] PIIX4: not 100% native mode: will probe irqs later
[   22.032565]     ide0: BM-DMA at 0x8040-0x8047, BIOS settings: hda:DMA, hdb:pio
[   22.032600] Probing IDE interface ide0...
[   22.319330] hda: IBM-DJSA-205, ATA DISK drive
[   22.767167] hdb: CRN-8241B, ATAPI CD/DVD-ROM drive
[   22.838012] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   22.863825] hda: max request size: 128KiB
[   22.913048] hda: 9767520 sectors (5000 MB) w/384KiB Cache, CHS=10336/15/63, UDMA(33)
[   22.913073] hda: cache flushes not supported
[   22.913210]  hda: hda1 hda2 < hda5 >
[   23.038298] hdb: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
[   23.038326] Uniform CD-ROM driver Revision: 3.20
[   23.452470] usbcore: registered new driver usbfs
[   23.452539] usbcore: registered new driver hub
[   23.457331] USB Universal Host Controller Interface driver v3.0
[   23.457469] PCI: Found IRQ 10 for device 0000:00:07.2
[   23.457513] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   23.457843] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   23.457899] uhci_hcd 0000:00:07.2: irq 10, io base 0x00008000
[   23.458202] usb usb1: configuration #1 chosen from 1 choice
[   23.458288] hub 1-0:1.0: USB hub found
[   23.458321] hub 1-0:1.0: 2 ports detected
[   23.499204] Probing IDE interface ide1...
[   24.122152] Attempting manual resume
[   24.179071] kjournald starting.  Commit interval 5 seconds
[   24.179117] EXT3-fs: mounted filesystem with ordered data mode.
[   47.162425] input: PC Speaker as /class/input/input1
[   47.715284] PCI: Found IRQ 11 for device 0000:00:03.0
[   47.715303] PCI: Sharing IRQ 11 with 0000:00:00.1
[   47.715313] PCI: Sharing IRQ 11 with 0000:00:00.2
[   47.715350] Yenta: CardBus bridge found at 0000:00:03.0 [1014:01a3]
[   47.715378] Yenta O2: res at 0x94/0xD4: 00/ea
[   47.715385] Yenta O2: old bridge, disabling read prefetch/write burst
[   47.844454] Yenta: ISA IRQ mask 0x02b8, PCI irq 10
[   47.844466] Socket status: 30000821
[   48.845173] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   48.870968] PCI: Found IRQ 11 for device 0000:00:00.1
[   48.870989] PCI: Sharing IRQ 11 with 0000:00:00.2
[   48.871255] PCI: Setting latency timer of device 0000:00:00.1 to 64
[   49.235261] pccard: CardBus card inserted into slot 0
[   49.438957] intel8x0_measure_ac97_clock: measured 55189 usecs
[   49.438972] intel8x0: clocking to 48000
[   51.271539] cs: IO port probe 0x100-0x3af: excluding 0x2c8-0x2cf
[   51.273832] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   51.274795] cs: IO port probe 0x820-0x8ff: clean.
[   51.275609] cs: IO port probe 0xc00-0xcf7: clean.
[   51.276747] cs: IO port probe 0xa00-0xaff: clean.
[   51.297622] ieee80211_crypt: registered algorithm 'NULL'
[   51.315126] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   51.315143] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   51.443295] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   51.458562] input: TPPS/2 IBM TrackPoint as /class/input/input2
[   51.497579] parport: PnPBIOS parport detected.
[   51.497622] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   51.610005] ts: Compaq touchscreen protocol output
[   51.648423] bcm43xx driver
[   51.648750] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[   51.648806] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   52.572557] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   52.590181] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   52.654659] lp0: using parport0 (interrupt-driven).
[   52.760640] Adding 240932k swap on /dev/disk/by-uuid/ab7bafdb-ebba-4d2f-8dc8-25c7a10def2a.  Priority:-1 extents:1 across:240932k
[   52.877806] EXT3 FS on hda1, internal journal
[   53.684337] NET: Registered protocol family 17
[   70.731313] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   79.809780] NET: Registered protocol family 10
[   79.810125] lo: Disabled Privacy Extensions
[   79.810407] IPv6 over IPv4 tunneling driver
[   82.517508] Bluetooth: Core ver 2.8
[   82.517529] NET: Registered protocol family 31
[   82.517536] Bluetooth: HCI device and connection manager initialized
[   82.517584] Bluetooth: HCI socket layer initialized
[   82.586910] Bluetooth: L2CAP ver 2.8
[   82.586929] Bluetooth: L2CAP socket layer initialized
[   82.608212] Bluetooth: RFCOMM socket layer initialized
[   82.608255] Bluetooth: RFCOMM TTY layer initialized
[   82.608262] Bluetooth: RFCOMM ver 1.7

```

sorry for the lengthy post, I just don't know what my problem is a this point. I should also add.  this is also my first go at setting up a wireless network. I pushed the reset button on the back of the router - I used 'linksys' as the essid and 'admin'. IAny advice on where to go next would be appreciated, thanks for reading-

Joe

---

### Post by Metaljaz on 2007-02-13
Based on the output you posted from iwconfig it looks like your card is based on the broadcom 43xx chipset. Below is a wiki that should get you where you need to be: 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

