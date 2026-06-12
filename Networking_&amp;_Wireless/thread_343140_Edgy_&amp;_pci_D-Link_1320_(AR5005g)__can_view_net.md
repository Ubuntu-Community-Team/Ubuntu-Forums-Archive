---
title: "Edgy &amp; pci D-Link 1320 (AR5005g) : can view networks, can't connect"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by dshuck on 2007-01-21
I have been running Ubuntu on my laptop for about 9 months using both Dapper and Edgy.  I have never had any issues whatsoever with wireless networking on it, but apparently wireless on desktops is a whole different animal.  

I have now convinced the wife to convert her desktop machine to Edgy but I have been absolutely beaten setting up the wireless networking.  I know it is a common issue, but I can't seem to find *the* solution.  At this point, I have installed NetworkManager, and I can see my network (and my neighbors), but when I try to connect using the open passphrase, it just never successfully joins.  I have now invested about 10 hours in this and am about to call it quits, but I decided I would put a "please help" post out here before I did.

Per some other posts, I will include some info.  Here is some output from things that apparently make more sense to some of you than they do to me:

**This is my /etc/network/interfaces**
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

**This is output from iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:188425  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

**output from lspci**
```

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
01:09.0 SCSI storage controller: Advanced System Products, Inc ABP940-U / ABP960-U (rev 03)
02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
02:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

```

**This is output from dmesg**
```

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI not present or invalid.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6f70
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff7880
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Found and enabled local APIC!
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1531.213 MHz processor.
[   15.239664] Using tsc for high-res timesource
[   15.240925] Console: colour VGA+ 80x25
[   15.241317] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.241624] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.256111] Memory: 510184k/524224k available (1910k kernel code, 13416k reserved, 1070k data, 308k init, 0k highmem)
[   15.256116] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.335484] Calibrating delay using timer specific routine.. 3066.77 BogoMIPS (lpj=6133545)
[   15.335535] Security Framework v1.0.0 initialized
[   15.335543] SELinux:  Disabled at boot.
[   15.335562] Mount-cache hash table entries: 512
[   15.335740] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   15.335748] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   15.335757] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.335760] CPU: L2 Cache: 256K (64 bytes/line)
[   15.335763] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   15.335784] Checking 'hlt' instruction... OK.
[   15.351559] SMP alternatives: switching to UP code
[   15.351745] Freeing SMP alternatives: 16k freed
[   15.351935] checking if image is initramfs... it is
[   15.917659] Freeing initrd memory: 5137k freed
[   15.917668] CPU0: AMD Athlon(tm) XP 1800+ stepping 02
[   15.917675] SMP motherboard not detected.
[   16.022749] Brought up 1 CPUs
[   16.022775] migration_cost=0
[   16.023117] NET: Registered protocol family 16
[   16.023153] EISA bus registered
[   16.040833] PCI: PCI BIOS revision 2.10 entry at 0xfb590, last bus=2
[   16.040842] PCI: Using configuration type 1
[   16.040845] Setting up standard PCI resources
[   16.045152] ACPI: Interpreter disabled.
[   16.045157] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.045172] pnp: PnP ACPI: disabled
[   16.045175] PnPBIOS: Scanning system for PnP BIOS support...
[   16.045501] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbfe0
[   16.045509] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc010, dseg 0xf0000
[   16.046657] spurious 8259A interrupt: IRQ7.
[   16.046992] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   16.047049] PCI: Probing PCI hardware
[   16.047053] PCI: Probing PCI hardware (bus 00)
[   16.047688] PCI: Ignoring BAR0-3 of IDE controller 0000:00:09.0
[   16.048031] Boot video device is 0000:02:00.0
[   16.049378] PCI: Using IRQ router default [10de/01e0] at 0000:00:00.0
[   16.096459] PCI: Bridge: 0000:00:08.0
[   16.096463]   IO window: 9000-9fff
[   16.096470]   MEM window: e6000000-e7ffffff
[   16.096475]   PREFETCH window: 30000000-300fffff
[   16.096481] PCI: Bridge: 0000:00:1e.0
[   16.096484]   IO window: a000-afff
[   16.096489]   MEM window: e4000000-e5ffffff
[   16.096493]   PREFETCH window: c0000000-dfffffff
[   16.096506] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   16.096543] NET: Registered protocol family 2
[   16.126656] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.126787] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.127017] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   16.127136] TCP: Hash tables configured (established 16384 bind 8192)
[   16.127140] TCP reno registered
[   16.127928] audit: initializing netlink socket (disabled)
[   16.127941] audit(1169315901.972:1): initialized
[   16.128102] VFS: Disk quotas dquot_6.5.1
[   16.128131] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.128199] Initializing Cryptographic API
[   16.128205] io scheduler noop registered
[   16.128212] io scheduler anticipatory registered
[   16.128219] io scheduler deadline registered
[   16.128236] io scheduler cfq registered (default)
[   16.128556] isapnp: Scanning for PnP cards...
[   16.482947] isapnp: No Plug & Play device found
[   16.509523] Real Time Clock Driver v1.12ac
[   16.509607] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.509760] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.509984] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   16.510736] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.511138] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   16.511463] mice: PS/2 mouse device common for all mice
[   16.512131] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.512400] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.512406] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.512661] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   16.512664] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   16.514462] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.514579] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.515166] EISA: Probing bus 0 at eisa.0
[   16.515217] EISA: Detected 0 cards.
[   16.515541] TCP bic registered
[   16.515550] NET: Registered protocol family 1
[   16.515559] NET: Registered protocol family 8
[   16.515562] NET: Registered protocol family 20
[   16.515592] Using IPI No-Shortcut mode
[   16.516031] Freeing unused kernel memory: 308k freed
[   16.826639] input: AT Translated Set 2 keyboard as /class/input/input0
[   17.683846] Capability LSM initialized
[   18.309974] sata_nv: Unknown symbol ata_scsi_ioctl
[   18.310045] sata_nv: Unknown symbol ata_std_bios_param
[   18.310071] sata_nv: Unknown symbol ata_tf_read
[   18.310107] sata_nv: Unknown symbol ata_tf_load
[   18.310132] sata_nv: Unknown symbol ata_bmdma_start
[   18.310158] sata_nv: Unknown symbol ata_pio_data_xfer
[   18.310195] sata_nv: Unknown symbol ata_bmdma_setup
[   18.310232] sata_nv: Unknown symbol ata_bmdma_stop
[   18.310284] sata_nv: Unknown symbol sata_phy_reset
[   18.310310] sata_nv: Unknown symbol ata_exec_command
[   18.310340] sata_nv: Unknown symbol ata_pci_host_stop
[   18.310366] sata_nv: Unknown symbol ata_pci_init_native_mode
[   18.310392] sata_nv: Unknown symbol ata_qc_issue_prot
[   18.310454] sata_nv: Unknown symbol ata_bmdma_irq_clear
[   18.310480] sata_nv: Unknown symbol ata_scsi_slave_config
[   18.310506] sata_nv: Unknown symbol ata_std_dev_select
[   18.310535] sata_nv: Unknown symbol ata_port_disable
[   18.310561] sata_nv: Unknown symbol ata_bmdma_status
[   18.310597] sata_nv: Unknown symbol ata_scsi_queuecmd
[   18.310623] sata_nv: Unknown symbol ata_host_intr
[   18.310649] sata_nv: Unknown symbol ata_eng_timeout
[   18.310674] sata_nv: Unknown symbol ata_port_stop
[   18.310711] sata_nv: Unknown symbol ata_check_status
[   18.310741] sata_nv: Unknown symbol ata_qc_prep
[   18.310766] sata_nv: Unknown symbol ata_pci_remove_one
[   18.310802] sata_nv: Unknown symbol ata_device_add
[   18.310827] sata_nv: Unknown symbol ata_port_start
[   18.311734] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   18.311759] NFORCE2: chipset revision 162
[   18.311762] NFORCE2: not 100% native mode: will probe irqs later
[   18.311770] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   18.311777] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   18.311790]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   18.311804]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   18.311814] Probing IDE interface ide0...
[   18.599764] hda: WDC WD204BA, ATA DISK drive
[   19.272230] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.272492] Probing IDE interface ide1...
[   21.124781] hdd: DVD-ROM BDV316C, ATAPI CD/DVD-ROM drive
[   21.180800] ide1 at 0x170-0x177,0x376 on irq 15
[   21.190760] hda: max request size: 128KiB
[   21.201801] hda: 39876480 sectors (20416 MB) w/2048KiB Cache, CHS=39560/16/63, UDMA(66)
[   21.201812] hda: cache flushes not supported
[   21.201877]  hda: hda1 hda2 < hda5 >
[   21.831619] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   21.831632] Uniform CD-ROM driver Revision: 3.20
[   27.584038] SCSI subsystem initialized
[   30.859766] scsi0 : AdvanSys SCSI 3.3K: PCI Ultra: IO 0x9000-0x900F, IRQ 0xB
[   30.980409] usbcore: registered new driver usbfs
[   30.980825] usbcore: registered new driver hub
[   30.982737] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   30.983184] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   30.983190] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   30.983591] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   30.997075] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe8003000
[   31.055073] usb usb1: configuration #1 chosen from 1 choice
[   31.055113] hub 1-0:1.0: USB hub found
[   31.055129] hub 1-0:1.0: 3 ports detected
[   31.156969] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   31.156975] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   31.157003] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   31.172854] ohci_hcd 0000:00:02.1: irq 5, io mem 0xe8004000
[   31.230935] usb usb2: configuration #1 chosen from 1 choice
[   31.231072] hub 2-0:1.0: USB hub found
[   31.231090] hub 2-0:1.0: 3 ports detected
[   31.334556] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   31.334564] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   31.334630] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   31.334682] ehci_hcd 0000:00:02.2: debug port 1
[   31.334689] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   31.334702] ehci_hcd 0000:00:02.2: irq 12, io mem 0xe8005000
[   31.334711] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.334791] usb usb3: configuration #1 chosen from 1 choice
[   31.334823] hub 3-0:1.0: USB hub found
[   31.334836] hub 3-0:1.0: 6 ports detected
[   31.471513] Attempting manual resume
[   31.495139] kjournald starting.  Commit interval 5 seconds
[   31.495157] EXT3-fs: mounted filesystem with ordered data mode.
[   32.083805] usb 3-2: new high speed USB device using ehci_hcd and address 3
[   32.216539] usb 3-2: configuration #1 chosen from 1 choice
[   32.519272] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   32.733908] usb 1-1: configuration #1 chosen from 1 choice
[   43.492588] Linux agpgart interface v0.101 (c) Dave Jones
[   43.507313] agpgart: Detected NVIDIA nForce2 chipset
[   43.513086] agpgart: AGP aperture is 64M @ 0xe0000000
[   43.523506] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   43.523549] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   44.052359] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.161595] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.257996] parport: PnPBIOS parport detected.
[   44.258062] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   44.322084] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   44.322167] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   44.335853] Floppy drive(s): fd0 is 1.44M
[   44.358507] FDC 0 is a post-1991 82077
[   44.417826] input: PC Speaker as /class/input/input1
[   44.549422] sata_nv: Unknown symbol ata_scsi_ioctl
[   44.549503] sata_nv: Unknown symbol ata_std_bios_param
[   44.549537] sata_nv: Unknown symbol ata_tf_read
[   44.549580] sata_nv: Unknown symbol ata_tf_load
[   44.549614] sata_nv: Unknown symbol ata_bmdma_start
[   44.549647] sata_nv: Unknown symbol ata_pio_data_xfer
[   44.549692] sata_nv: Unknown symbol ata_bmdma_setup
[   44.549736] sata_nv: Unknown symbol ata_bmdma_stop
[   44.549800] sata_nv: Unknown symbol sata_phy_reset
[   44.549833] sata_nv: Unknown symbol ata_exec_command
[   44.549871] sata_nv: Unknown symbol ata_pci_host_stop
[   44.549905] sata_nv: Unknown symbol ata_pci_init_native_mode
[   44.549938] sata_nv: Unknown symbol ata_qc_issue_prot
[   44.550010] sata_nv: Unknown symbol ata_bmdma_irq_clear
[   44.550044] sata_nv: Unknown symbol ata_scsi_slave_config
[   44.550077] sata_nv: Unknown symbol ata_std_dev_select
[   44.550114] sata_nv: Unknown symbol ata_port_disable
[   44.550148] sata_nv: Unknown symbol ata_bmdma_status
[   44.550192] sata_nv: Unknown symbol ata_scsi_queuecmd
[   44.550226] sata_nv: Unknown symbol ata_host_intr
[   44.550259] sata_nv: Unknown symbol ata_eng_timeout
[   44.550292] sata_nv: Unknown symbol ata_port_stop
[   44.550337] sata_nv: Unknown symbol ata_check_status
[   44.550375] sata_nv: Unknown symbol ata_qc_prep
[   44.550408] sata_nv: Unknown symbol ata_pci_remove_one
[   44.550452] sata_nv: Unknown symbol ata_device_add
[   44.550485] sata_nv: Unknown symbol ata_port_start
[   44.789822] usbcore: registered new driver hiddev
[   44.807441] input: Logitech USB-PS/2 Trackball as /class/input/input2
[   44.807514] input: USB HID v1.00 Mouse [Logitech USB-PS/2 Trackball] on usb-0000:00:02.0-1
[   44.807531] usbcore: registered new driver usbhid
[   44.807536] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   44.841184] eth0: forcedeth.c: subsystem: 01297:0531 bound to 0000:00:04.0
[   44.841275] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   44.935759] ts: Compaq touchscreen protocol output
[   44.949819] usbcore: registered new driver libusual
[   44.964783] ath_hal: module license 'Proprietary' taints kernel.
[   44.972454] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   45.038855] wlan: 0.8.4.2 (0.9.2)
[   45.049664] ath_rate_sample: 1.2 (0.9.2)
[   45.066897] ath_pci: 0.9.4.5 (0.9.2)
[   45.109871] Initializing USB Mass Storage driver...
[   45.164422] intel8x0_measure_ac97_clock: measured 54770 usecs
[   45.164429] intel8x0: clocking to 48000
[   45.795826] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   45.795835] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   45.795845] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   45.795850] wifi0: mac 7.8 phy 4.5 radio 5.6
[   45.795855] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   45.795858] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   45.795861] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   45.795863] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   45.795866] wifi0: Use hw queue 8 for CAB traffic
[   45.795868] wifi0: Use hw queue 9 for beacons
[   45.799120] scsi1 : SCSI emulation for USB Mass Storage devices
[   45.799288] usbcore: registered new driver usb-storage
[   45.799293] USB Mass Storage support registered.
[   45.799298] usb-storage: device found at 3
[   45.799301] usb-storage: waiting for device to settle before scanning
[   45.812938] wifi0: Atheros 5212: mem=0xe7000000, irq=5
[   46.045137] lp0: using parport0 (interrupt-driven).
[   46.085479] Adding 843372k swap on /dev/disk/by-uuid/ecb774d0-98a9-497e-9a15-602b94c8dec9.  Priority:-1 extents:1 across:843372k
[   46.147482] EXT3 FS on hda1, internal journal
[   49.623299] [drm] Initialized drm 1.0.1 20051102
[   49.658406] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   50.511178] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.793979] usb-storage: device scan complete
[   50.796864]   Vendor: HTS54104  Model: 0G9AT00           Rev: MB2O
[   50.796876]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   50.827795] mtrr: 0xc0000000,0x10000000 overlaps existing 0xc0000000,0x8000000
[   50.828158] mtrr: 0xc0000000,0x10000000 overlaps existing 0xc0000000,0x8000000
[   50.828396] mtrr: 0xc0000000,0x10000000 overlaps existing 0xc0000000,0x8000000
[   50.828850] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   50.828869] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   50.828923] agpgart: Putting AGP V3 device at 0000:02:00.0 into 4x mode
[   50.857515] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[   50.858957] sda: Write Protect is off
[   50.858965] sda: Mode Sense: 00 14 00 00
[   50.858968] sda: assuming drive cache: write through
[   50.860793] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[   50.861756] sda: Write Protect is off
[   50.861762] sda: Mode Sense: 00 14 00 00
[   50.861765] sda: assuming drive cache: write through
[   50.862024]  sda:<6>[drm] Setting GART location based on new memory map
[   51.148786] [drm] Loading R300 Microcode
[   51.148841] [drm] writeback test succeeded in 1 usecs
[   51.195096]  sda1
[   51.195998] sd 1:0:0:0: Attached scsi disk sda
[   51.284994] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   59.084763] eth0: no link during initialization.
[   59.936959] Bluetooth: Core ver 2.8
[   59.936966] NET: Registered protocol family 31
[   59.936969] Bluetooth: HCI device and connection manager initialized
[   59.936993] Bluetooth: HCI socket layer initialized
[   59.963684] Bluetooth: L2CAP ver 2.8
[   59.963691] Bluetooth: L2CAP socket layer initialized
[   60.004010] Bluetooth: RFCOMM socket layer initialized
[   60.004033] Bluetooth: RFCOMM TTY layer initialized
[   60.004036] Bluetooth: RFCOMM ver 1.7
[   70.179545] ISO 9660 Extensions: Microsoft Joliet Level 3
[   70.336184] ISO 9660 Extensions: RRIP_1991A
[   72.680040] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[   76.669855] ReiserFS: sda1: using ordered data mode
[   76.699429] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   76.701566] ReiserFS: sda1: checking transaction log (sda1)
[   76.994774] ReiserFS: sda1: Using r5 hash to sort names
[ 2723.414318] NET: Registered protocol family 17
[19640.052193] ISO 9660 Extensions: Microsoft Joliet Level 3
[19642.393056] ISO 9660 Extensions: RRIP_1991A

```

If anyone sees anything that could put me on track or has any other advice, I would *GREATLY* appreciate it.

---

### Post by Dafydd on 2007-01-21
Hi
I'm battling with the same problem. Networkmanager just won't let me connect, so I have to open up a terminal and set the essid, key and then do sudo dhclient eth1.

Why not try another distro? Mandriva One seems good with wireless (if you install your driver).

Dafydd

---

### Post by dshuck on 2007-01-21
On other thing of note.  The reason I listed AR5005G as the chipset is that what displayed when I outputted lspci.  However, when I look in the madwifi.org compatibility [http://madwifi.org/wiki/Compatibility#WDA1320](http://madwifi.org/wiki/Compatibility#WDA1320) , it they list the chipset as AR5212(802.11a/b/g) . I don't know if that makes any difference, but I thought it should be noted.  Thanks.

And to Dafydd, I may try that download today.  I really know nothing about it.  Since you know what it is that you have to add to connect, is it possible that you could write a script that runs on session start to do that?  I am not terribly experienced when it comes to that kind of stuff, but it seems like that should be possible.

---

### Post by dshuck on 2007-01-21
Well, as much as I hate it I got it running with no issues at all on Mandriva One.  By default Mandriva One doesn't have the madwifi kernel.  Since the machine is not on a network, I pulled down the madwifi source to my laptop and moved it over with a usb drive.  It was at this point I realized that it doesn't have whatever libraries are needed for compilation either.  I decided to give the ndiswrapper a shot since it makes it a very easy and obvious choice.  When I did this it installed properly and joined my network.    On one hand and am thinking "YAY! FINALLY!", but on the other hand, I *really* wanted this to work on Ubuntu, as I am a big fan.  In fact the Beryl 3D stuff was what finally nudged my wife into letting me convert her machine.   At least at this point I can clearly see there is no problem with the card itself.

EDIT:
Well that is just ridiculous.  Apparently the 3D desktop is installed by default with Mandriva One!  This is a pretty dang cool distro afterall.

---

### Post by Dafydd on 2007-01-24
> **dshuck said:**
> Since you know what it is that you have to add to connect, is it possible that you could write a script that runs on session start to do that?  I am not terribly experienced when it comes to that kind of stuff, but it seems like that should be possible.

I don't know how to do scripts... I suppose I'm learning as a baby learns languages - you just pick up what you know and use it. if it works you remember it.

probably you know this, but to connect i type (after sudo su ):

iwconfig eth1 essid XXXXXXX

iwconfig eth1 key XXXXXXXXXXXXXXXXXXXXX

sudo dhclient eth1

But somehow, networkmanager is working. I think it worked after choosing > system > keyring manager. Then I manually placed the essid key. Somehow, it did not stick the correct key in (which is a text key).

daf

---

### Post by Sunflower1970 on 2007-02-01
I'm in the market for a wireless card, since I'm getting ready to connect two of my desktops together...and I was looking at this card, since it was a good deal at CompUSA and according to the support comments I saw it worked perfectly in Dapper and Edgy...Now I'm a bit worried. Has anyone had luck with this card with Edgy? 

Thanks.

---

### Post by Sunflower1970 on 2007-02-01
Just an update...

I took the plunge and bought this card. Plugged it in, set up the router, And it just works beautifully. I was expecting some sort of problem, but I didn't have any whatsoever. 

I'm one happy camper. :)

---

