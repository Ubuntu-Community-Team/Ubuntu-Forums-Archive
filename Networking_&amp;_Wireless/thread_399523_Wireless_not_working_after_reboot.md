---
title: "Wireless not working after reboot"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by itsmeagain on 2007-04-02
Hi
Thought I try out Ubuntu to see what Linux is all about, version 6.06.1 desktop installed great, found some instructions on the forum on how to make my Lynksys wireless card work . Following the instructions I got the card up and running but after a reboot it fails. 
OK these are the commands / actions I took

lspci
Report:
0000:02:01.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless L AN Controller (rev 02)

sudo rmmod bcm43xx

sudo gedit /etc/modprobe.d/blacklist

Installed ndiswrapper using Synaptic Package Manager 

sudo ndiswrapper -i WMP11V27.inf ( this is the Windows driver that came with the card)

ndiswrapper -l
stewart@stewart-desktop:~/lynksys$ sudo ndiswrapper -l
Installed ndis drivers:
wmp11v27                driver present, hardware present

sudo ndiswrapper -m

sudo modprobe ndiswrapper
 
Went to System > Administration > Networking > input ESSID and WEP, activated it and bingo the driver worked and I could access the Internet, however after a reboot the card would not work.  I have done the following in different orders many times but still not good, I have rerun ndiswrapper -l, sudo modprobe -m, sudo modprobe ndiswrapper.  I Deactivated the network and Activated the network but still not working.  I made a fresh installation, carried out the exact instructions as above and its the same scenario, Internet works but after a reboot nothing. Can any body point to what is going on here

---

### Post by spd106 on 2007-04-02
Check that ndiswrapper has been added to the /etc/modules file.
```
cat /etc/modules
```

If not then add it.

---

### Post by itsmeagain on 2007-04-03
Yes I did the command "sudo ndiswrapper -m"
However this command did not add ndiswrapper to /etc/modules file. 
So I did "sudo gedit /etc/modules" and typed ndiswrapper at the bottom of the file and then saved it.
I have discovered that after a reboot if I open Network, Deactivate wlan0 and then Activate it the card works and I can access the internet

Can you think on any thing else ?

---

### Post by spd106 on 2007-04-03
Check the /etc/network/interfaces file has an *auto wlan0* line.

When you start up next time could you copy the output of entering **dmesg** at a terminal before bringing up the wifi card. Then post it here.

---

### Post by itsmeagain on 2007-04-04
Hi 
Find below the /var/log.  It long. Also find my interfaces file

[14000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000037ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000037ff0000 - 0000000037ff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000037ff3000 - 0000000038000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 895MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f4a80
[17179569.184000] On node 0 totalpages: 229360
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225264 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f6560
[17179569.184000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x37ff3000
[17179569.184000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x37ff3040
[17179569.184000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x37ff6740
[17179569.184000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:1 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 38000000:c6c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1713.926 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.248000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.252000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.296000] Memory: 898868k/917440k available (1977k kernel code, 17912k reserved, 605k data, 288k init, 0k highmem)
[17179571.296000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.376000] Calibrating delay using timer specific routine.. 3431.06 BogoMIPS (lpj=6862124)
[17179571.376000] Security Framework v1.0.0 initialized
[17179571.376000] SELinux:  Disabled at boot.
[17179571.376000] Mount-cache hash table entries: 512
[17179571.376000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.376000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.376000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.376000] CPU: L2 cache: 256K
[17179571.376000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[17179571.376000] mtrr: v2.0 (20020519)
[17179571.376000] CPU: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[17179571.376000] Enabling fast FPU save and restore... done.
[17179571.376000] Enabling unmasked SIMD FPU exception support... done.
[17179571.376000] Checking 'hlt' instruction... OK.
[17179571.392000] checking if image is initramfs... it is
[17179572.248000] Freeing initrd memory: 6616k freed
[17179572.276000] ACPI: Looking for DSDT ... not found!
[17179572.284000] ENABLING IO-APIC IRQs
[17179572.284000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.428000] NET: Registered protocol family 16
[17179572.428000] EISA bus registered
[17179572.428000] ACPI: bus type pci registered
[17179572.440000] PCI: PCI BIOS revision 2.10 entry at 0xf9d70, last bus=2
[17179572.440000] PCI: Using configuration type 1
[17179572.440000] ACPI: Subsystem revision 20051216
[17179572.452000] ACPI: Interpreter enabled
[17179572.452000] ACPI: Using IOAPIC for interrupt routing
[17179572.452000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.452000] PCI: Probing PCI hardware (bus 00)
[17179572.456000] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[17179572.456000] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[17179572.456000] Boot video device is 0000:01:00.0
[17179572.456000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.456000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.484000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179572.484000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179572.484000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179572.484000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179572.484000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179572.488000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179572.488000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179572.488000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179572.488000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179572.492000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.492000] pnp: PnP ACPI init
[17179572.500000] pnp: PnP ACPI: found 12 devices
[17179572.500000] PnPBIOS: Disabled by ACPI PNP
[17179572.500000] PCI: Using ACPI for IRQ routing
[17179572.500000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.584000] PCI: Bridge: 0000:00:01.0
[17179572.584000]   IO window: 9000-9fff
[17179572.584000]   MEM window: dc000000-ddffffff
[17179572.584000]   PREFETCH window: d8000000-dbffffff
[17179572.584000] PCI: Bridge: 0000:00:1e.0
[17179572.584000]   IO window: a000-afff
[17179572.584000]   MEM window: de000000-dfffffff
[17179572.584000]   PREFETCH window: e0000000-e00fffff
[17179572.584000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.584000] audit: initializing netlink socket (disabled)
[17179572.584000] audit(1175666110.584:1): initialized
[17179572.584000] VFS: Disk quotas dquot_6.5.1
[17179572.584000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.584000] Initializing Cryptographic API
[17179572.584000] io scheduler noop registered
[17179572.584000] io scheduler anticipatory registered
[17179572.584000] io scheduler deadline registered
[17179572.584000] io scheduler cfq registered
[17179572.584000] isapnp: Scanning for PnP cards...
[17179572.940000] isapnp: No Plug & Play device found
[17179572.968000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.968000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.968000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.968000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.968000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.968000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.972000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.976000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.976000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.976000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.976000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.976000] mice: PS/2 mouse device common for all mice
[17179572.976000] EISA: Probing bus 0 at eisa.0
[17179572.976000] Cannot allocate resource for EISA slot 4
[17179572.976000] Cannot allocate resource for EISA slot 5
[17179572.976000] EISA: Detected 0 cards.
[17179572.976000] NET: Registered protocol family 2
[17179573.000000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.020000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.020000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.020000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.020000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.020000] TCP reno registered
[17179573.020000] TCP bic registered
[17179573.020000] NET: Registered protocol family 1
[17179573.020000] NET: Registered protocol family 8
[17179573.020000] NET: Registered protocol family 20
[17179573.020000] Using IPI Shortcut mode
[17179573.020000] ACPI wakeup devices: 
[17179573.020000] SLPB PCI0 HUB0 USB0 USB1 
[17179573.020000] ACPI: (supports S0 S1 S4 S5)
[17179573.020000] Freeing unused kernel memory: 288k freed
[17179573.112000] vga16fb: initializing
[17179573.112000] vga16fb: mapped to 0xc00a0000
[17179573.240000] Console: switching to colour frame buffer device 80x25
[17179573.240000] fb0: VGA16 VGA frame buffer device
[17179574.364000] Capability LSM initialized
[17179574.436000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179575.672000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179575.672000] ICH2: chipset revision 5
[17179575.672000] ICH2: not 100% native mode: will probe irqs later
[17179575.672000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179575.672000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179575.672000] Probing IDE interface ide0...
[17179575.960000] hda: ST310211A, ATA DISK drive
[17179576.240000] hdb: ST340810A, ATA DISK drive
[17179576.296000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.304000] Probing IDE interface ide1...
[17179577.040000] hdc: LITE-ON DVDRW SHW-16H5S, ATAPI CD/DVD-ROM drive
[17179577.824000] hdd: LG CD-ROM CRD-8522B, ATAPI CD/DVD-ROM drive
[17179577.880000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.908000] hda: max request size: 128KiB
[17179577.944000] hda: 19541088 sectors (10005 MB) w/512KiB Cache, CHS=19386/16/63, UDMA(100)
[17179577.944000] hda: cache flushes not supported
[17179577.944000]  hda: hda1 hda2 < hda5 >
[17179578.016000] hdb: max request size: 128KiB
[17179578.016000] hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179578.016000] hdb: cache flushes not supported
[17179578.016000]  hdb: hdb1 hdb2 < hdb5 >
[17179578.068000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.068000] Uniform CD-ROM driver Revision: 3.20
[17179578.072000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[17179578.740000] usbcore: registered new driver usbfs
[17179578.744000] usbcore: registered new driver hub
[17179578.748000] USB Universal Host Controller Interface driver v2.3
[17179578.748000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 169
[17179578.748000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179578.748000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179578.748000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179578.748000] uhci_hcd 0000:00:1f.2: irq 169, io base 0x0000b000
[17179578.748000] hub 1-0:1.0: USB hub found
[17179578.748000] hub 1-0:1.0: 2 ports detected
[17179578.852000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 177
[17179578.852000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179578.852000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179578.852000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179578.852000] uhci_hcd 0000:00:1f.4: irq 177, io base 0x0000b800
[17179578.852000] hub 2-0:1.0: USB hub found
[17179578.852000] hub 2-0:1.0: 2 ports detected
[17179579.140000] Attempting manual resume
[17179579.196000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179579.212000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.212000] EXT3-fs: write access will be enabled during recovery.
[17179579.400000] usbcore: registered new driver hiddev
[17179579.404000] hiddev96: USB HID v1.00 Device [Yealink Network Technology Ltd. VOIP USB Phone           ] on usb-0000:00:1f.4-1
[17179579.404000] usbcore: registered new driver usbhid
[17179579.404000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179582.216000] EXT3-fs: recovery complete.
[17179582.216000] kjournald starting.  Commit interval 5 seconds
[17179582.216000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.092000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.108000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.128000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.164000] agpgart: Detected an Intel i845 Chipset.
[17179597.172000] agpgart: AGP aperture is 128M @ 0xd0000000
[17179597.700000] hw_random: RNG not detected
[17179598.708000] usbcore: registered new driver yealink
[17179598.708000] drivers/usb/input/yealink.c: Yealink phone driver:yld-20051230
[17179598.748000] parport: PnPBIOS parport detected.
[17179598.748000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179598.764000] input: PC Speaker as /class/input/input1
[17179598.792000] Real Time Clock Driver v1.12
[17179598.912000] Floppy drive(s): fd0 is 1.44M
[17179598.932000] FDC 0 is a post-1991 82077
[17179598.996000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179598.996000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179598.996000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179599.024000] e100: eth0: e100_probe: addr 0xe0000000, irq 185, MAC addr 00:08:C7:CA:91:FF
[17179599.112000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179599.328000] usbcore: registered new driver snd-usb-audio
[17179599.604000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179599.640000] ts: Compaq touchscreen protocol output
[17179601.588000] lp0: using parport0 (interrupt-driven).
[17179601.644000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179601.712000] ndiswrapper: driver wmp11v27 (Linksys,07/30/2002, 3.08.28.0) loaded
[17179601.716000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 201
[17179601.720000] ndiswrapper: using irq 201
[17179602.748000] wlan0: vendor: ''
[17179602.748000] wlan0: ndiswrapper ethernet device 00:06:25:1c:f3:d6 using driver wmp11v27, 14E4:4301:1737:4301.5.conf
[17179602.748000] ndiswrapper (set_auth_mode:686): setting auth mode to 3 failed (C0010015)
[17179602.748000] wlan0: encryption modes supported: WEP
[17179602.872000] Adding 433712k swap on /dev/hda5.  Priority:-1 extents:1 across:433712k
[17179603.108000] EXT3 FS on hda1, internal journal
[17179603.368000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179603.368000] md: bitmap version 4.39
[17179604.272000] NET: Registered protocol family 17
[17179604.420000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179604.776000] cdrom: open failed.
[17179605.424000] cdrom: open failed.
[17179605.428000] cdrom: open failed.7179569.18


interfaces
#auto lo
#iface lo inet loopback

#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Homer
wireless-key 8830A3A237813996F774223CB6

iface lo inet loopback

auto wlan0

---

### Post by spd106 on 2007-04-04
First thing to do is to clean up the interfaces file. Uncomment the two loopback lines at the top and delete the one at the end.

From the log file you can see that ndiswrapper is being loaded, that just means that the card is not being activated for some reason. What happens when you run this command? ```
sudo ifup wlan0
```

---

### Post by itsmeagain on 2007-04-04
Hello
I modified the interfaces file as suggested and saved it.
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Homer
wireless-key 8830A3A237813996F774223CB6

auto wlan0

Rebooted the machine and the situation was the same, wifi card not working
I opened Network and could see that wlan0 was active. I Deactivated wlan0, closed Network, opened Network and Activated wlan0, close Network and bingo the card sprung into action.  I know it may seem strange but if I do not close Network after each  Deactivating or Activating the wifi card does not work. This is the only way I can get the card to work

IFUP
stewart@stewart-desktop:~$ sudo ifup wlan0
Password:
ifup: interface wlan0 already configured
stewart@stewart-desktop:~$

IF DOWN 
stewart@stewart-desktop:~$ sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:06:25:1c:f3:d6
Sending on   LPF/wlan0/00:06:25:1c:f3:d6
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
stewart@stewart-desktop:~$


IFUP AGAIN
stewart@stewart-desktop:~$ sudo ifup wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:06:25:1c:f3:d6
Sending on   LPF/wlan0/00:06:25:1c:f3:d6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
stewart@stewart-desktop:~$

Hope this information helps

regards

Stewart

---

