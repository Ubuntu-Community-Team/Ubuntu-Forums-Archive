---
title: "network not working anymore after upgrade"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by antimatter on 2006-10-29
hi!
this is a problem i have had since i upgraded from breezy to dapper. after the upgrade my laptop would always tell me: eth0: interrupt(s) dropped, no ipv6 routers present. using my wlan card i get: ADDRCONF(NETDEV_UP): wlan0_ link ist not ready, spurios 8259A interrupt: IRQ15. the cards still work with breezys kernel though! i thought that upgrading to edgy would fix this, but it didnt. same errors still. the eth cards a 3com one. my wlan cards an acer wlan 11g.

anyone got a clue? if you need more output, let me know

---

### Post by Jose Catre-Vandis on 2006-10-29
So what kind of cards are they? PCIAMA, USB etc?
Do they work "out of the box" under Breezy, or what have you had to do to get them working - in which case what are the chipsets etc?
What is in your etc/network/interfaces file?
It will be best to work on one at a time, rather than both at once. start with the wired nic. Also, why two cards? Are you using them both at once or alternately depending on where you are? Linking to same network or different ones with the different nics?

---

### Post by antimatter on 2006-10-29
they worked out of the box under breezy. for my wlan card i used ndiswrapper, but that worked like a charm too. theyre both pcmcia cards. my laptop (thinkpad 240x) has only got pcmcia slot. ive got both wired aswell as a wlan at home. usually only use the wlan at my uni though and wired at home. im not seeing anything suspicious in the interfaces file. theres the loopback interface and the auto/iface lines for wlan0 and eth0. the wlan card uses the neti2220 driver. the lan cards a 3com megahertz 10/100(3CCFE574BT). they both worked with my home network under breezy and hoary(im selecting the breezy kernel in grub, because i still have it installed(thank god)). depending on where i am in the use i could switch the pcmcia cards.

---

### Post by antimatter on 2006-10-31
this is the third time im postin this thread and i still didnt get any support. whats up with that ubuntu people?

---

### Post by Jose Catre-Vandis on 2006-10-31
> **antimatter said:**
> this is the third time im postin this thread and i still didnt get any support. whats up with that ubuntu people?

Stay calm antimatter, it may be about the questions you ask and the detail you give. Getting these things to work takes time and is often a process of elimination, and many users only carry a part of the right answer, so you need to wait for them to spot the bit they know the answer too.

Best, as I suggested, to start with one of your cards, and work it through to the point where it doesn't comply with the accepted "working" setup, i.e. at which point in the setup does it not work, and what outputs are you getting?

If we start with the wired nic, please post the following (with only the wired nic in place:

```
 lspci -v
```
```
 dmesg
```

These outputs should tell us what your PC is seeing and doing with what it finds.

---

### Post by antimatter on 2006-11-02
thanks for you reply. i replied like that, because this thread was already on page xy, where nobody could see it and i had already given up on finding someone who could help me. anyway! heres the output:

> 
root@ly:/home/stefan # lspci -v
00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
        Flags: bus master, medium devsel, latency 64

00:07.0 Bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1020 [size=16]

00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 1000 [size=32]

00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
        Flags: medium devsel

00:09.0 VGA compatible controller: Silicon Motion, Inc. SM712 LynxEM+ (rev a0) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 01aa
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [40] Power Management version 1

00:0a.0 CardBus bridge: Texas Instruments PCI1211
        Subsystem: IBM Unknown device 019a
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 14000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
        Subsystem: IBM Unknown device 01a9
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at fc010000 (32-bit, non-prefetchable) [size=4K]
        Memory at fc000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2




> 
root@ly:/home/stefan # dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000bff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000bff0000 - 000000000bfffc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000bfffc00 - 000000000c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 191MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 49136
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 45040 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c90
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0bffcd07
[17179569.184000] ACPI: FADT (v001 IBM    TP240    0x06040000 PTL  0x000f4240) @ 0x0bfffb65
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0bfffbd9
[17179569.184000] ACPI: DSDT (v001    PTL    BX-TJ 0x06040000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=42dab2f1-a0b4-4499-867b-2e76dcf88be9 ro quiet
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0118a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 497.877 MHz processor.
[   44.377673] Using tsc for high-res timesource
[   44.379468] Console: colour VGA+ 80x25
[   44.380174] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   44.380920] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   44.407185] Memory: 183784k/196544k available (1910k kernel code, 12244k reserved, 1070k data, 308k init, 0k highmem)
[   44.407201] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   44.485523] Calibrating delay using timer specific routine.. 997.27 BogoMIPS (lpj=1994554)
[   44.485666] Security Framework v1.0.0 initialized
[   44.485689] SELinux:  Disabled at boot.
[   44.485746] Mount-cache hash table entries: 512
[   44.486167] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   44.486196] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   44.486231] CPU: L1 I cache: 16K, L1 D cache: 16K
[   44.486242] CPU: L2 cache: 256K
[   44.486253] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   44.486319] Checking 'hlt' instruction... OK.
[   44.501736] SMP alternatives: switching to UP code
[   44.502053] Freeing SMP alternatives: 16k freed
[   44.502495] checking if image is initramfs... it is
[   46.821736] Freeing initrd memory: 6721k freed
[   46.821760] CPU0: Intel Pentium III (Coppermine) stepping 03
[   46.821781] SMP motherboard not detected.
[   46.821791] Local APIC not detected. Using dummy APIC emulation.
[   46.822027] Brought up 1 CPUs
[   46.822091] migration_cost=0
[   46.823198] NET: Registered protocol family 16
[   46.823309] EISA bus registered
[   46.824284] PCI: PCI BIOS revision 2.10 entry at 0xfd9df, last bus=0
[   46.824304] PCI: Using configuration type 1
[   46.824312] Setting up standard PCI resources
[   46.828851] ACPI: Interpreter disabled.
[   46.828867] Linux Plug and Play Support v0.97 (c) Adam Belay
[   46.828894] pnp: PnP ACPI: disabled
[   46.828906] PnPBIOS: Scanning system for PnP BIOS support...
[   46.828971] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6d30
[   46.828985] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xac8b, dseg 0x400
[   46.833535] PnPBIOS: Unknown tag '0x82', length '25'.
[   46.836048] PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
[   46.836206] PCI: Probing PCI hardware
[   46.836219] PCI: Probing PCI hardware (bus 00)
[   46.836594] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[   46.836881] Boot video device is 0000:00:09.0
[   46.838445] PCI: Using IRQ router PIIX/ICH [8086/7198] at 0000:00:07.0
[   46.839825] pnp: 00:00: ioport range 0x398-0x399 has been reserved
[   46.839876] pnp: 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[   46.839888] pnp: 00:0b: ioport range 0x8000-0x803f has been reserved
[   46.839901] pnp: 00:0b: ioport range 0x2180-0x218f has been reserved
[   46.840820] PCI: Ignore bogus resource 6 [0:0] of 0000:00:09.0
[   46.840852] PCI: Bus 1, cardbus bridge: 0000:00:0a.0
[   46.840862]   IO window: 00001400-000014ff
[   46.840874]   IO window: 00001800-000018ff
[   46.840886]   PREFETCH window: 10000000-11ffffff
[   46.840898]   MEM window: 12000000-13ffffff
[   46.840933] PCI: Found IRQ 11 for device 0000:00:0a.0
[   46.840962] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   46.841045] NET: Registered protocol family 2
[   46.880871] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   46.881201] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   46.881453] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   46.881588] TCP: Hash tables configured (established 8192 bind 4096)
[   46.881598] TCP reno registered
[   46.882179] Simple Boot Flag at 0x41 set to 0x1
[   46.883982] audit: initializing netlink socket (disabled)
[   46.884023] audit(1162484754.692:1): initialized
[   46.884515] VFS: Disk quotas dquot_6.5.1
[   46.884593] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   46.884830] Initializing Cryptographic API
[   46.884847] io scheduler noop registered
[   46.884873] io scheduler anticipatory registered
[   46.884896] io scheduler deadline registered
[   46.884949] io scheduler cfq registered (default)
[   46.885626] isapnp: Scanning for PnP cards...
[   47.238871] isapnp: No Plug & Play device found
[   47.329841] Real Time Clock Driver v1.12ac
[   47.330055] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   47.343472] pnp: Device 00:0e activated.
[   47.343867] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   47.345009] mice: PS/2 mouse device common for all mice
[   47.347063] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   47.347793] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   47.347809] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   47.348360] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   47.350757] serio: i8042 AUX port at 0x60,0x64 irq 12
[   47.350937] serio: i8042 KBD port at 0x60,0x64 irq 1
[   47.351698] EISA: Probing bus 0 at eisa.0
[   47.351720] Cannot allocate resource for EISA slot 1
[   47.351759] Cannot allocate resource for EISA slot 8
[   47.351768] EISA: Detected 0 cards.
[   47.352494] TCP bic registered
[   47.352529] NET: Registered protocol family 1
[   47.352553] NET: Registered protocol family 8
[   47.352562] NET: Registered protocol family 20
[   47.352637] Using IPI No-Shortcut mode
[   47.354049] Freeing unused kernel memory: 308k freed
[   47.395065] input: AT Translated Set 2 keyboard as /class/input/input0
[   47.555382] Capability LSM initialized
[   49.218910] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   49.218953] PIIX4: chipset revision 0
[   49.218962] PIIX4: not 100% native mode: will probe irqs later
[   49.218985]     ide0: BM-DMA at 0x1020-0x1027, BIOS settings: hda:DMA, hdb:pio
[   49.219020]     ide1: BM-DMA at 0x1028-0x102f, BIOS settings: hdc:pio, hdd:pio
[   49.219046] Probing IDE interface ide0...
[   49.507755] hda: HITACHI_DK23DA-20, ATA DISK drive
[   50.179554] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   50.180245] Probing IDE interface ide1...
[   50.760937] hda: max request size: 128KiB
[   50.762595] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(33)
[   50.762820] hda: cache flushes supported
[   50.762944]  hda: hda1 hda2 hda3
[   51.307559] Probing IDE interface ide1...
[   51.312407] usbcore: registered new driver usbfs
[   51.314155] usbcore: registered new driver hub
[   51.320847] USB Universal Host Controller Interface driver v3.0
[   51.320968] PCI: Found IRQ 11 for device 0000:00:07.2
[   51.321016] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   51.321320] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   51.321375] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001000
[   51.321651] usb usb1: configuration #1 chosen from 1 choice
[   51.321737] hub 1-0:1.0: USB hub found
[   51.321766] hub 1-0:1.0: 2 ports detected
[   51.942897] ReiserFS: hda2: found reiserfs format "3.6" with standard journal
[   53.682136] ReiserFS: hda2: using ordered data mode
[   53.710525] ReiserFS: hda2: journal params: device hda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   53.717085] ReiserFS: hda2: checking transaction log (hda2)
[   53.793810] ReiserFS: hda2: Using r5 hash to sort names
[   80.046970] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   80.046986] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[   80.047066] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[   80.287923] PCI: Found IRQ 11 for device 0000:00:0a.0
[   80.287970] Yenta: CardBus bridge found at 0000:00:0a.0 [1014:019a]
[   80.287995] Yenta: Enabling burst memory read transactions
[   80.288006] Yenta: Using CSCINT to route CSC interrupts to PCI
[   80.288015] Yenta: Routing CardBus interrupts to PCI
[   80.288028] Yenta TI: socket 0000:00:0a.0, mfunc 0x012c1272, devctl 0x64
[   80.448535] input: PC Speaker as /class/input/input1
[   80.520647] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[   80.520661] Socket status: 30000010
[   81.159574] pccard: PCMCIA card inserted into slot 0
[   82.366111] irda_init()
[   82.366160] NET: Registered protocol family 23
[   82.435480] PnPBIOS: Unknown tag '0x82', length '25'.
[   82.447828] pnp: Device 00:0f activated.
[   82.447842] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   82.447884] nsc-ircc, chip->init
[   82.447893] nsc-ircc, Found chip at base=0x398
[   82.447929] nsc-ircc, driver loaded (Dag Brattli)
[   82.448234] IrDA: Registered device irda0
[   82.448244] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   82.815266] PCI: Found IRQ 5 for device 0000:00:0b.0
[   82.861126] Floppy drive(s): fd0 is 1.44M
[   82.878109] FDC 0 is a National Semiconductor PC87306
[   82.941620] pnp: Device 00:14 activated.
[   82.941635] parport: PnPBIOS parport detected.
[   82.941753] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   83.369926] gameport: CS4281 Gameport is pci0000:00:0b.0/gameport0, speed 2294kHz
[   83.560137] cs: IO port probe 0x100-0x4ff: clean.
[   83.561486] cs: IO port probe 0xc00-0xcf7: clean.
[   83.562231] cs: IO port probe 0xa00-0xaff: clean.
[   83.562976] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   83.567873] pcmcia: registering new device pcmcia0.0
[   83.688443] IBM TrackPoint firmware: 0x0b, buttons: 3/3
[   83.704654] input: TPPS/2 IBM TrackPoint as /class/input/input2
[   83.833593] ts: Compaq touchscreen protocol output
[   83.906356]   ASIC rev 1,<6>eth0: Megahertz 574B at io 0x300, irq 3, hw_addr 00:50:04:8C:06:D6.
[   83.915531]  64K FIFO split 1:1 Rx:Tx, autoselect MII interface.
[   84.632481] lp0: using parport0 (interrupt-driven).
[   84.890887] Adding 423352k swap on /dev/disk/by-uuid/52cf994d-55ec-424f-aa0c-c732998289ca.  Priority:-1 extents:1 across:423352k
[   92.364867] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[   92.640263] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   92.640278] md: bitmap version 4.39
[  104.301995] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[  104.688671] ReiserFS: hda1: using ordered data mode
[  104.705312] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  104.711275] ReiserFS: hda1: checking transaction log (hda1)
[  104.787170] ReiserFS: hda1: Using r5 hash to sort names
[  105.756928] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[  107.250489] NET: Registered protocol family 17
[  111.156303] pnp: Device 00:0f cannot be configured because it is in use.
[  111.156867] pnp: Device 00:0f cannot be configured because it is in use.
[  132.195957] IBM machine detected. Enabling interrupts during APM calls.
[  132.195982] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  133.195338] Non-volatile memory driver v1.2
[  133.393103] input: /usr/sbin/thinkpad-keys as /class/input/input3
[  136.034327] setup_irq: irq handler mismatch
[  136.034372]  <c01497d7> setup_irq+0x127/0x140  <cca2c910> nsc_ircc_interrupt+0x0/0x5a0 [nsc_ircc]
[  136.034449]  <c0149889> request_irq+0x99/0xb0  <cca2cf07> nsc_ircc_net_open+0x57/0x1e0 [nsc_ircc]
[  136.034505]  <c01e489c> vsnprintf+0x55c/0x640  <c0272281> dev_open+0x31/0x70
[  136.034571]  <c0270c6c> dev_change_flags+0xfc/0x130  <c02666b0> sock_ioctl+0x0/0x220
[  136.034654]  <c0272523> dev_ioctl+0x263/0x380  <c0158f41> __handle_mm_fault+0x211/0x900
[  136.034727]  <c02667c4> sock_ioctl+0x114/0x220  <c02666b0> sock_ioctl+0x0/0x220
[  136.034760]  <c017d5eb> do_ioctl+0x2b/0x90  <c017d6ac> vfs_ioctl+0x5c/0x2b0
[  136.034814]  <c017d972> sys_ioctl+0x72/0x90  <c0102fbb> sysenter_past_esp+0x54/0x79
[  136.034885] nsc-ircc, unable to allocate irq=3
[  143.766808] NET: Registered protocol family 10
[  143.767145] lo: Disabled Privacy Extensions
[  143.767442] IPv6 over IPv4 tunneling driver
[  144.179223] Bluetooth: Core ver 2.8
[  144.179244] NET: Registered protocol family 31
[  144.179253] Bluetooth: HCI device and connection manager initialized
[  144.179296] Bluetooth: HCI socket layer initialized
[  144.284715] Bluetooth: L2CAP ver 2.8
[  144.284734] Bluetooth: L2CAP socket layer initialized
[  144.410545] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[  144.899859] Bluetooth: RFCOMM socket layer initialized
[  144.899909] Bluetooth: RFCOMM TTY layer initialized
[  144.899918] Bluetooth: RFCOMM ver 1.7
[ 6208.638094] eth0: found link beat
[ 6208.638113] eth0: autonegotiation complete: 100baseT-FD selected
[ 6210.636978] eth0: interrupt(s) dropped!
[ 6217.346427] eth0: no IPv6 routers present



---

### Post by Jose Catre-Vandis on 2006-11-07
Did you run these commands with no PCMCIA cards in? With my wired card I get good output about an Ethernet Controller from lspci -v. try lspcmcia to check the cardbus bridge is functioning

---

### Post by antimatter on 2006-11-14
root@ly:/home/stefan # lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.0)
Socket 0 Device 0:      [3c574_cs]              (bus ID: 0.0)

---

### Post by antimatter on 2006-11-24
bump

---

### Post by Jose Catre-Vandis on 2006-12-07
OK, I can see that the cardbus is working and that the 3Com card is inserted, and that it is of the 3c574 series. This should be supported by the kernel in Dapper and Edgy. Another user found that booting up in recovery mode discovered and enabled the pc card (?)

Have a look in your network settings and see if you need to enable the device: System>Adminstration>Networking. Or try "ifconfig" in terminal for info

---

### Post by antimatter on 2006-12-14
the card is enabled. firing it up from neither the console via ifup nor the system panel works :-k

---

### Post by antimatter on 2007-06-11
ok in noticed a patter in my problem. whenever a kernel update comes out, the card starts working for a few days. then the laptop will eventually crash and the problem starts over again and ill have to wait for another kernel update. this problem ist REALLY WEIRD

---

