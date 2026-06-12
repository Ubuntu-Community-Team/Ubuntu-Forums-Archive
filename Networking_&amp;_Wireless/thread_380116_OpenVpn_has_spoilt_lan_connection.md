---
title: "OpenVpn has spoilt lan connection"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by elvis_shock on 2007-03-09
Dear All,

I am using Ubuntu Edgy and recently ran into this problem while trying
to use openvpn.

After using openvpn to connect to a soc connection using sudo (why why
why did i ever do that), had to btw, it required root rights, it
created a few tap/tun connections and after that, my browsers stopped
responding to requests, any website entered returns the standard error
page for no connection.

Tried to do some digging in the log files and found three things which
seemed a little out of place, not sure if they will help, but
nonetheless, one was saying that a dhcpbd file was missing and the
path it was looking in was somehow /etc/redhat/..... now before
installing the openvpn, i read somewhere that it was originally
designed for redhat, hope it isnt the one causing problems.

next i saw is that the connection manager got IDHCP messages from the
server but dynamic modification was disabled.

lastly, it said that a subnet for the eth0 and eth1 connection was
missing from the dhcp.conf file and so it was going to ignore messages
on these two.

Any idea how I can solve the problem. I really do not want to
reinstall Ubuntu after 100s of hrs of customizing it.

Please give me detailed instructions, as you might have guessed I am a
noob at all this.

Warm regards.

PS: Am gonna post the logs below.

---

### Post by elvis_shock on 2007-03-09
**_USER.LOG_**

> 

Mar  9 21:05:03 ayush-laptop hpiod: 1.6.9 accepting connections at 2208... 
Mar  9 21:05:08 ayush-laptop dhcdbd: Started up.
Mar  9 21:05:08 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar  9 21:05:08 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar  9 21:08:50 ayush-laptop gconfd (ayush-4975): starting (version 2.16.0), pid 4975 user 'ayush'
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readwrite:/home/ayush/.gconf" to a writable configuration source at position 1
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar  9 21:08:55 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readwrite:/home/ayush/.gconf" to a writable configuration source at position 0



---

### Post by elvis_shock on 2007-03-09
**_SYSLOG_**

> 
/* Some text here */
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   MEM window: c2000000-c3ffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: Bridge: 0000:00:1e.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   IO window: 4000-8fff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   MEM window: c0200000-cfffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   PREFETCH window: e8000000-efffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: setting IRQ 11 as level-triggered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] NET: Registered protocol family 2
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP: Hash tables configured (established 131072 bind 65536)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP reno registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] Simple Boot Flag at 0x35 set to 0x1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] audit: initializing netlink socket (disabled)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] audit(1173474273.560:1): initialized
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] VFS: Disk quotas dquot_6.5.1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] Initializing Cryptographic API
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler noop registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler anticipatory registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler deadline registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler cfq registered (default)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] isapnp: Scanning for PnP cards...
Mar  9 21:04:59 ayush-laptop kernel: [17179570.916000] isapnp: No Plug & Play device found
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] Real Time Clock Driver v1.12ac
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] pnp: Device 00:0a activated.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] mice: PS/2 mouse device common for all mice
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] EISA: Probing bus 0 at eisa.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 2
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 3
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 4
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 5
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 6
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 7
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 8
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] EISA: Detected 0 cards.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] TCP bic registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] NET: Registered protocol family 1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] NET: Registered protocol family 8
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] NET: Registered protocol family 20
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Using IPI No-Shortcut mode
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] ACPI: (supports S0 S3 S4 S5)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Freeing unused kernel memory: 308k freed
Mar  9 21:04:59 ayush-laptop kernel: [17179570.952000] input: AT Translated Set 2 keyboard as /class/input/input0
Mar  9 21:04:59 ayush-laptop kernel: [17179572.116000] Capability LSM initialized
Mar  9 21:04:59 ayush-laptop kernel: [17179572.180000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Mar  9 21:04:59 ayush-laptop kernel: [17179572.180000] ACPI: Processor [CPU] (supports 8 throttling states)
Mar  9 21:04:59 ayush-laptop kernel: [17179572.180000] ACPI: Thermal Zone [THM0] (70 C)
Mar  9 21:04:59 ayush-laptop kernel: [17179572.428000] ICH4: IDE controller at PCI slot 0000:00:1f.1
Mar  9 21:04:59 ayush-laptop kernel: [17179572.428000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ICH4: chipset revision 1
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ICH4: not 100%% native mode: will probe irqs later
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] Probing IDE interface ide0...
Mar  9 21:04:59 ayush-laptop kernel: [17179572.720000] hda: HTS541040G9AT00, ATA DISK drive
Mar  9 21:04:59 ayush-laptop kernel: [17179573.392000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Mar  9 21:04:59 ayush-laptop kernel: [17179573.408000] Probing IDE interface ide1...
Mar  9 21:04:59 ayush-laptop kernel: [17179574.144000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, ATAPI CD/DVD-ROM drive
Mar  9 21:04:59 ayush-laptop kernel: [17179574.480000] ide1 at 0x170-0x177,0x376 on irq 15
Mar  9 21:04:59 ayush-laptop kernel: [17179574.484000] hda: max request size: 128KiB
Mar  9 21:04:59 ayush-laptop kernel: [17179574.492000] hda: 78140160 sectors (40007 MB) w/7539KiB Cache, CHS=65535/16/63, UDMA(100)
Mar  9 21:04:59 ayush-laptop kernel: [17179574.492000] hda: cache flushes supported
Mar  9 21:04:59 ayush-laptop kernel: [17179574.492000]  hda: hda1 hda2 hda3 hda4
Mar  9 21:04:59 ayush-laptop kernel: [17179574.540000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Mar  9 21:04:59 ayush-laptop kernel: [17179574.540000] Uniform CD-ROM driver Revision: 3.20
Mar  9 21:04:59 ayush-laptop kernel: [17179574.856000] usbcore: registered new driver usbfs
Mar  9 21:04:59 ayush-laptop kernel: [17179574.856000] usbcore: registered new driver hub
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] USB Universal Host Controller Interface driver v3.0
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] usb usb1: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] hub 1-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] hub 1-0:1.0: 2 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] usb usb2: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] hub 2-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] hub 2-0:1.0: 2 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] usb usb3: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] hub 3-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] hub 3-0:1.0: 2 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: debug port 1
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] usb usb4: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] hub 4-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] hub 4-0:1.0: 6 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179575.312000] Attempting manual resume
Mar  9 21:04:59 ayush-laptop kernel: [17179575.336000] kjournald starting.  Commit interval 5 seconds
Mar  9 21:04:59 ayush-laptop kernel: [17179575.336000] EXT3-fs: mounted filesystem with ordered data mode.
Mar  9 21:04:59 ayush-laptop kernel: [17179575.564000] usb 4-3: new high speed USB device using ehci_hcd and address 2
Mar  9 21:04:59 ayush-laptop kernel: [17179575.696000] usb 4-3: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179575.696000] hub 4-3:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179575.696000] hub 4-3:1.0: 4 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179576.000000] usb 4-3.1: new high speed USB device using ehci_hcd and address 3
Mar  9 21:04:59 ayush-laptop kernel: [17179576.092000] usb 4-3.1: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179576.292000] usb 4-3.3: new full speed USB device using ehci_hcd and address 4
Mar  9 21:04:59 ayush-laptop kernel: [17179576.384000] usb 4-3.3: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179576.584000] usb 4-3.4: new low speed USB device using ehci_hcd and address 5
Mar  9 21:04:59 ayush-laptop kernel: [17179576.676000] usb 4-3.4: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179587.820000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  9 21:04:59 ayush-laptop kernel: [17179587.824000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  9 21:04:59 ayush-laptop kernel: [17179588.092000] irda_init()
Mar  9 21:04:59 ayush-laptop kernel: [17179588.092000] NET: Registered protocol family 23
Mar  9 21:04:59 ayush-laptop kernel: [17179588.172000] hw_random: RNG not detected
Mar  9 21:04:59 ayush-laptop kernel: [17179588.192000] Floppy drive(s): fd0 is 1.44M
Mar  9 21:04:59 ayush-laptop kernel: [17179588.220000] FDC 0 is a National Semiconductor PC87306
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] pnp: Device 00:0c activated.
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, chip->init
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, Found chip at base=0x02e
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, driver loaded (Dag Brattli)
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] IrDA: Registered device irda0
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Mar  9 21:04:59 ayush-laptop kernel: [17179588.808000] parport: PnPBIOS parport detected.
Mar  9 21:04:59 ayush-laptop kernel: [17179588.812000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Mar  9 21:04:59 ayush-laptop kernel: [17179588.928000] Linux agpgart interface v0.101 (c) Dave Jones
Mar  9 21:04:59 ayush-laptop kernel: [17179588.932000] agpgart: Detected an Intel 855PM Chipset.
Mar  9 21:04:59 ayush-laptop kernel: [17179588.948000] agpgart: AGP aperture is 256M @ 0xd0000000
Mar  9 21:04:59 ayush-laptop kernel: [17179589.008000] ieee80211_crypt: registered algorithm 'NULL'
Mar  9 21:04:59 ayush-laptop kernel: [17179589.008000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Mar  9 21:04:59 ayush-laptop kernel: [17179589.008000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Mar  9 21:04:59 ayush-laptop kernel: [17179589.032000] input: PC Speaker as /class/input/input1
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] Driver 'ipw2200' needs updating - please use bus_type methods
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Mar  9 21:04:59 ayush-laptop kernel: [17179589.428000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta: Using INTVAL to route CSC interrupts to PCI
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta: Routing CardBus interrupts to PCI
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
Mar  9 21:04:59 ayush-laptop kernel: [17179589.436000] usbcore: registered new driver libusual
Mar  9 21:04:59 ayush-laptop kernel: [17179589.456000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3F11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.456000] usbcore: registered new driver usblp
Mar  9 21:04:59 ayush-laptop kernel: [17179589.456000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Mar  9 21:04:59 ayush-laptop kernel: [17179589.472000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
Mar  9 21:04:59 ayush-laptop kernel: [17179589.472000] e100: Copyright(c) 1999-2005 Intel Corporation
Mar  9 21:04:59 ayush-laptop kernel: [17179589.560000] usbcore: registered new driver hiddev
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] input: HID 04b3:3107 as /class/input/input2
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] input: USB HID v1.00 Mouse [HID 04b3:3107] on usb-0000:00:1d.7-3.4
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] usbcore: registered new driver usbhid
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Mar  9 21:04:59 ayush-laptop kernel: [17179589.632000] SCSI subsystem initialized
Mar  9 21:04:59 ayush-laptop kernel: [17179589.632000] Initializing USB Mass Storage driver...
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] scsi0 : SCSI emulation for USB Mass Storage devices
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] usbcore: registered new driver usb-storage
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] USB Mass Storage support registered.
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] usb-storage: device found at 3
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] usb-storage: waiting for device to settle before scanning
Mar  9 21:04:59 ayush-laptop kernel: [17179589.660000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
Mar  9 21:04:59 ayush-laptop kernel: [17179589.660000] serio: Synaptics pass-through port at isa0060/serio1/input0
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] Yenta: ISA IRQ mask 0x0430, PCI irq 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] Socket status: 30000086
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] cs: IO port probe 0x4000-0x8fff: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179589.672000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.672000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.696000] e100: eth0: e100_probe: addr 0xc0205000, irq 11, MAC addr 00:16:41:53:2A:ED
Mar  9 21:04:59 ayush-laptop kernel: [17179589.696000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.696000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179589.724000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Mar  9 21:04:59 ayush-laptop kernel: [17179589.800000] ts: Compaq touchscreen protocol output
Mar  9 21:04:59 ayush-laptop kernel: [17179589.864000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0x100-0x3af: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0x820-0x8ff: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0xc00-0xcf7: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0xa00-0xaff: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.516000] intel8x0_measure_ac97_clock: measured 55485 usecs
Mar  9 21:04:59 ayush-laptop kernel: [17179590.516000] intel8x0: clocking to 48000
Mar  9 21:04:59 ayush-laptop kernel: [17179590.668000] lp0: using parport0 (interrupt-driven).
Mar  9 21:04:59 ayush-laptop kernel: [17179590.676000] NET: Registered protocol family 17
Mar  9 21:04:59 ayush-laptop kernel: [17179590.724000] fuse init (API version 7.6)
Mar  9 21:04:59 ayush-laptop kernel: [17179590.744000] Adding 1325352k swap on /dev/disk/by-uuid/d193ad29-3512-45d7-89cd-392abf295430.  Priority:-1 extents:1 across:1325352k
Mar  9 21:04:59 ayush-laptop kernel: [17179590.852000] EXT3 FS on hda3, internal journal
Mar  9 21:04:59 ayush-laptop kernel: [17179591.024000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Mar  9 21:04:59 ayush-laptop kernel: [17179591.080000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
Mar  9 21:04:59 ayush-laptop kernel: [17179591.100000] NTFS volume version 3.1.
Mar  9 21:04:59 ayush-laptop kernel: [17179591.152000] NTFS volume version 3.1.
Mar  9 21:04:59 ayush-laptop kernel: [17179594.636000] usb-storage: device scan complete
Mar  9 21:04:59 ayush-laptop kernel: [17179594.636000]   Vendor: ST332062  Model: 0A                Rev: 0000
Mar  9 21:04:59 ayush-laptop kernel: [17179594.636000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar  9 21:04:59 ayush-laptop kernel: [17179594.668000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Write Protect is off
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Mode Sense: 27 00 00 00
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: assuming drive cache: write through
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Write Protect is off
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Mode Sense: 27 00 00 00
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: assuming drive cache: write through
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000]  sda: sda1
Mar  9 21:04:59 ayush-laptop kernel: [17179594.676000] sd 0:0:0:0: Attached scsi disk sda
Mar  9 21:04:59 ayush-laptop kernel: [17179594.692000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar  9 21:04:59 ayush-laptop kernel: [17179595.620000] ACPI: AC Adapter [AC] (on-line)
Mar  9 21:04:59 ayush-laptop kernel: [17179595.652000] ACPI: Battery Slot [BAT0] (battery absent)
Mar  9 21:04:59 ayush-laptop kernel: [17179595.668000] ACPI: Power Button (FF) [PWRF]
Mar  9 21:04:59 ayush-laptop kernel: [17179595.668000] ACPI: Lid Switch [LID]
Mar  9 21:04:59 ayush-laptop kernel: [17179595.668000] ACPI: Sleep Button (CM) [SLPB]
Mar  9 21:04:59 ayush-laptop kernel: [17179595.700000] ACPI: ACPI Dock Station Driver 
Mar  9 21:04:59 ayush-laptop kernel: [17179595.788000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
Mar  9 21:04:59 ayush-laptop kernel: [17179595.788000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Mar  9 21:04:59 ayush-laptop kernel: [17179595.804000] pcc_acpi: loading...
Mar  9 21:04:59 ayush-laptop kernel: [17179595.928000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Mar  9 21:04:59 ayush-laptop ntpdate[3437]: step time server 82.211.81.145 offset -0.488821 sec
Mar  9 21:05:01 ayush-laptop kernel: [17179598.424000] [drm] Initialized drm 1.0.1 20051102
Mar  9 21:05:01 ayush-laptop kernel: [17179598.440000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:05:01 ayush-laptop kernel: [17179598.444000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
Mar  9 21:05:02 ayush-laptop last message repeated 2 times
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Mar  9 21:05:02 ayush-laptop named[4110]: starting BIND 9.3.2 -u bind
Mar  9 21:05:02 ayush-laptop named[4110]: found 1 CPU, using 1 worker thread
Mar  9 21:05:02 ayush-laptop named[4110]: loading configuration from '/etc/bind/named.conf'
Mar  9 21:05:02 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:02 ayush-laptop named[4110]: no IPv6 interfaces found
Mar  9 21:05:02 ayush-laptop named[4110]: listening on IPv4 interface lo, 127.0.0.1#53
Mar  9 21:05:02 ayush-laptop named[4110]: listening on IPv4 interface eth0, 172.20.167.151#53
Mar  9 21:05:02 ayush-laptop named[4110]: command channel listening on 127.0.0.1#953
Mar  9 21:05:02 ayush-laptop named[4110]: zone 0.in-addr.arpa/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: zone 127.in-addr.arpa/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: zone 255.in-addr.arpa/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: zone localhost/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: running
Mar  9 21:05:02 ayush-laptop kernel: [17179600.072000] [drm] Setting GART location based on new memory map
Mar  9 21:05:02 ayush-laptop kernel: [17179600.072000] [drm] writeback test succeeded in 2 usecs
Mar  9 21:05:03 ayush-laptop ovpn-socvpn-linux[4128]: Options error: You must define CA file (--ca) or PKCS#12 file (--pkcs12)
Mar  9 21:05:03 ayush-laptop ovpn-socvpn-linux[4128]: Use --help for more information.
Mar  9 21:05:03 ayush-laptop hpiod: 1.6.9 accepting connections at 2208... 
Mar  9 21:05:03 ayush-laptop kernel: [17179601.020000] IBM machine detected. Enabling interrupts during APM calls.
Mar  9 21:05:03 ayush-laptop kernel: [17179601.020000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Mar  9 21:05:03 ayush-laptop kernel: [17179601.020000] apm: overridden by ACPI.
Mar  9 21:05:06 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Mar  9 21:05:08 ayush-laptop dhcdbd: Started up.
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Istarting... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'e100'. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IDeactivating device eth0. 
Mar  9 21:05:08 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Mar  9 21:05:08 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IWill activate connection 'eth0'. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IDevice eth0 activation scheduled... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) started... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar  9 21:05:09 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:09 ayush-laptop NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Mar  9 21:05:09 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar  9 21:05:09 ayush-laptop NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Mar  9 21:05:10 ayush-laptop hcid[4520]: Bluetooth HCI daemon
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] Bluetooth: Core ver 2.8
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] NET: Registered protocol family 31
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] Bluetooth: HCI device and connection manager initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] Bluetooth: HCI socket layer initialized
Mar  9 21:05:10 ayush-laptop hcid[4520]: Register path:/org/bluez fallback:1
Mar  9 21:05:10 ayush-laptop kernel: [17179607.636000] Bluetooth: L2CAP ver 2.8
Mar  9 21:05:10 ayush-laptop kernel: [17179607.636000] Bluetooth: L2CAP socket layer initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.640000] Bluetooth: RFCOMM socket layer initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.640000] Bluetooth: RFCOMM TTY layer initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.640000] Bluetooth: RFCOMM ver 1.7
Mar  9 21:05:10 ayush-laptop sdpd[4527]: Bluetooth SDP daemon 
Mar  9 21:05:10 ayush-laptop dhclient: isc-dhclient-V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar  9 21:05:10 ayush-laptop dhcpd: All rights reserved.
Mar  9 21:05:10 ayush-laptop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  9 21:05:10 ayush-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar  9 21:05:10 ayush-laptop dhcpd: All rights reserved.
Mar  9 21:05:10 ayush-laptop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  9 21:05:10 ayush-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar  9 21:05:10 ayush-laptop dhcpd: All rights reserved.
Mar  9 21:05:10 ayush-laptop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  9 21:05:10 ayush-laptop dhcpd: Wrote 0 leases to leases file.
Mar  9 21:05:10 ayush-laptop dhcpd: 
Mar  9 21:05:10 ayush-laptop dhcpd: Not configured to listen on any interfaces!
Mar  9 21:05:10 ayush-laptop NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Mar  9 21:05:12 ayush-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Mar  9 21:05:12 ayush-laptop dhclient: DHCPACK from 172.20.160.2
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  address 172.20.167.151 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  netmask 255.255.255.0 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  broadcast 172.20.167.255 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  gateway 172.20.167.1 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  nameserver 137.132.0.254 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  nameserver 137.132.0.252 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  domain name 'nus.edu.sg' 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar  9 21:05:12 ayush-laptop dhclient: bound to 172.20.167.151 -- renewal in 6546 seconds.
Mar  9 21:05:12 ayush-laptop anacron[4630]: Anacron 2.3 started on 2007-03-09
Mar  9 21:05:12 ayush-laptop anacron[4630]: Normal exit (0 jobs run)
Mar  9 21:05:12 ayush-laptop /usr/sbin/cron[4656]: (CRON) INFO (pidfile fd = 3)
Mar  9 21:05:12 ayush-laptop /usr/sbin/cron[4659]: (CRON) STARTUP (fork ok)
Mar  9 21:05:12 ayush-laptop /usr/sbin/cron[4659]: (CRON) INFO (Running @reboot jobs)
Mar  9 21:05:12 ayush-laptop kernel: [17179610.268000] Non-volatile memory driver v1.2
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IDHCP returned name servers but system has disabled dynamic modification! 
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar  9 21:05:13 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:13 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:14 ayush-laptop ntpdate[4800]: step time server 82.211.81.145 offset 0.001804 sec
Mar  9 21:05:19 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Mar  9 21:05:30 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar  9 21:05:37 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Mar  9 21:05:51 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Mar  9 21:05:55 ayush-laptop dhclient: No DHCPOFFERS received.
Mar  9 21:05:55 ayush-laptop dhclient: No working leases in persistent database - sleeping.
Mar  9 21:05:55 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:55 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:56 ayush-laptop ntpdate[4828]: step time server 82.211.81.145 offset -0.000058 sec
Mar  9 21:08:50 ayush-laptop gconfd (ayush-4975): starting (version 2.16.0), pid 4975 user 'ayush'
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readwrite:/home/ayush/.gconf" to a writable configuration source at position 1
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar  9 21:08:53 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:08:55 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readwrite:/home/ayush/.gconf" to a writable configuration source at position 0
Mar  9 21:08:58 ayush-laptop kernel: [17179835.396000] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar  9 21:08:58 ayush-laptop kernel: [17179835.528000] ISOFS: changing to secondary root
Mar  9 21:08:59 ayush-laptop ntfs-3g[5086]: Version 1.0 
Mar  9 21:08:59 ayush-laptop ntfs-3g[5086]: Mounted /dev/sda1 (Read-Write, label "Ext Drive", NTFS 3.1) 
Mar  9 21:08:59 ayush-laptop ntfs-3g[5086]: Options: noatime,rw,nosuid,nodev,user,nonempty,silent,allow_other,default_permissions,fsname=/dev/sda1 
Mar  9 21:09:19 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:10:54 ayush-laptop hcid[4520]: name_listener_add(:1.15)
Mar  9 21:10:54 ayush-laptop hcid[4520]: Default passkey agent (:1.15, /org/bluez/applet) registered
Mar  9 21:10:55 ayush-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Mar  9 21:11:58 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar  9 21:12:05 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar  9 21:12:12 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Mar  9 21:12:26 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17



---

### Post by elvis_shock on 2007-03-09
**_MESSAGES.LOG_**

> 

Mar  9 21:04:59 ayush-laptop syslogd 1.4.1#18ubuntu6: restart.
Mar  9 21:04:59 ayush-laptop kernel: Inspecting /boot/System.map-2.6.17-11-generic
Mar  9 21:04:59 ayush-laptop kernel: Loaded 22866 symbols from /boot/System.map-2.6.17-11-generic.
Mar  9 21:04:59 ayush-laptop kernel: Symbols match kernel version 2.6.17.
Mar  9 21:04:59 ayush-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] BIOS-provided physical RAM map:
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000002ff50000 (usable)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 000000002ff50000 - 000000002ff67000 (ACPI data)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 000000002ff67000 - 000000002ff79000 (ACPI NVS)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] 0MB HIGHMEM available.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] 767MB LOWMEM available.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] DMI present.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x1008
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cf800000)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Built 1 zonelists
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Initializing CPU#0
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Detected 1698.788 MHz processor.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Using pmtmr for high-res timesource
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] Console: colour VGA+ 80x25
Mar  9 21:04:59 ayush-laptop kernel: [17179569.800000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.800000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.824000] Memory: 768864k/785728k available (1911k kernel code, 16296k reserved, 1073k data, 308k init, 0k highmem)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.824000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] Calibrating delay using timer specific routine.. 3400.40 BogoMIPS (lpj=6800807)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] Security Framework v1.0.0 initialized
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] SELinux:  Disabled at boot.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] Mount-cache hash table entries: 512
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] CPU: L2 cache: 2048K
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] Checking 'hlt' instruction... OK.
Mar  9 21:04:59 ayush-laptop kernel: [17179569.920000] SMP alternatives: switching to UP code
Mar  9 21:04:59 ayush-laptop kernel: [17179569.920000] Freeing SMP alternatives: 16k freed
Mar  9 21:04:59 ayush-laptop kernel: [17179569.920000] checking if image is initramfs... it is
Mar  9 21:04:59 ayush-laptop kernel: [17179570.464000] Freeing initrd memory: 5561k freed
Mar  9 21:04:59 ayush-laptop kernel: [17179570.464000] ACPI: Core revision 20060707
Mar  9 21:04:59 ayush-laptop kernel: [17179570.464000] ACPI: Looking for DSDT ... not found!
Mar  9 21:04:59 ayush-laptop kernel: [17179570.468000] ACPI: setting ELCR to 0200 (from 0800)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.476000] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
Mar  9 21:04:59 ayush-laptop kernel: [17179570.476000] SMP motherboard not detected.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.476000] Local APIC not detected. Using dummy APIC emulation.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.476000] Brought up 1 CPUs
Mar  9 21:04:59 ayush-laptop kernel: [17179570.476000] migration_cost=0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.480000] NET: Registered protocol family 16
Mar  9 21:04:59 ayush-laptop kernel: [17179570.480000] EISA bus registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.480000] ACPI: bus type pci registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.480000] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
Mar  9 21:04:59 ayush-laptop kernel: [17179570.480000] PCI: Using configuration type 1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.480000] Setting up standard PCI resources
Mar  9 21:04:59 ayush-laptop kernel: [17179570.480000] ACPI: Found ECDT
Mar  9 21:04:59 ayush-laptop kernel: [17179570.488000] ACPI: Interpreter enabled
Mar  9 21:04:59 ayush-laptop kernel: [17179570.488000] ACPI: Using PIC for interrupt routing
Mar  9 21:04:59 ayush-laptop kernel: [17179570.488000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.496000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Mar  9 21:04:59 ayush-laptop kernel: [17179570.496000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Mar  9 21:04:59 ayush-laptop kernel: [17179570.496000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.496000] PCI: Transparent bridge - 0000:00:1e.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.500000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.500000] ACPI: Power Resource [PUBS] (on)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.504000] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar  9 21:04:59 ayush-laptop kernel: [17179570.504000] pnp: PnP ACPI init
Mar  9 21:04:59 ayush-laptop kernel: [17179570.508000] pnp: PnP ACPI: found 13 devices
Mar  9 21:04:59 ayush-laptop kernel: [17179570.508000] PnPBIOS: Disabled by ACPI PNP
Mar  9 21:04:59 ayush-laptop kernel: [17179570.508000] PCI: Using ACPI for IRQ routing
Mar  9 21:04:59 ayush-laptop kernel: [17179570.508000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: Bridge: 0000:00:01.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   IO window: 3000-3fff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   MEM window: c0100000-c01fffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   PREFETCH window: e0000000-e7ffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   IO window: 00004000-000040ff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   IO window: 00004400-000044ff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   PREFETCH window: e8000000-e9ffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   MEM window: c2000000-c3ffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: Bridge: 0000:00:1e.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   IO window: 4000-8fff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   MEM window: c0200000-cfffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000]   PREFETCH window: e8000000-efffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] NET: Registered protocol family 2
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP: Hash tables configured (established 131072 bind 65536)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] TCP reno registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] Simple Boot Flag at 0x35 set to 0x1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] audit: initializing netlink socket (disabled)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] audit(1173474273.560:1): initialized
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] VFS: Disk quotas dquot_6.5.1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] Initializing Cryptographic API
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler noop registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler anticipatory registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler deadline registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] io scheduler cfq registered (default)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.560000] isapnp: Scanning for PnP cards...
Mar  9 21:04:59 ayush-laptop kernel: [17179570.916000] isapnp: No Plug & Play device found
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] Real Time Clock Driver v1.12ac
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] pnp: Device 00:0a activated.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179570.936000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] mice: PS/2 mouse device common for all mice
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar  9 21:04:59 ayush-laptop kernel: [17179570.940000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] EISA: Probing bus 0 at eisa.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 2
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 3
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 4
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 5
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 6
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 7
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Cannot allocate resource for EISA slot 8
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] EISA: Detected 0 cards.
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] TCP bic registered
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] NET: Registered protocol family 1
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] NET: Registered protocol family 8
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] NET: Registered protocol family 20
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Using IPI No-Shortcut mode
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] ACPI: (supports S0 S3 S4 S5)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.944000] Freeing unused kernel memory: 308k freed
Mar  9 21:04:59 ayush-laptop kernel: [17179570.952000] input: AT Translated Set 2 keyboard as /class/input/input0
Mar  9 21:04:59 ayush-laptop kernel: [17179572.116000] Capability LSM initialized
Mar  9 21:04:59 ayush-laptop kernel: [17179572.180000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Mar  9 21:04:59 ayush-laptop kernel: [17179572.180000] ACPI: Processor [CPU] (supports 8 throttling states)
Mar  9 21:04:59 ayush-laptop kernel: [17179572.180000] ACPI: Thermal Zone [THM0] (70 C)
Mar  9 21:04:59 ayush-laptop kernel: [17179572.428000] ICH4: IDE controller at PCI slot 0000:00:1f.1
Mar  9 21:04:59 ayush-laptop kernel: [17179572.428000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ICH4: chipset revision 1
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] ICH4: not 100%% native mode: will probe irqs later
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
Mar  9 21:04:59 ayush-laptop kernel: [17179572.720000] hda: HTS541040G9AT00, ATA DISK drive
Mar  9 21:04:59 ayush-laptop kernel: [17179573.392000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Mar  9 21:04:59 ayush-laptop kernel: [17179574.144000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, ATAPI CD/DVD-ROM drive
Mar  9 21:04:59 ayush-laptop kernel: [17179574.480000] ide1 at 0x170-0x177,0x376 on irq 15
Mar  9 21:04:59 ayush-laptop kernel: [17179574.484000] hda: max request size: 128KiB
Mar  9 21:04:59 ayush-laptop kernel: [17179574.492000] hda: 78140160 sectors (40007 MB) w/7539KiB Cache, CHS=65535/16/63, UDMA(100)
Mar  9 21:04:59 ayush-laptop kernel: [17179574.492000] hda: cache flushes supported
Mar  9 21:04:59 ayush-laptop kernel: [17179574.492000]  hda: hda1 hda2 hda3 hda4
Mar  9 21:04:59 ayush-laptop kernel: [17179574.540000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Mar  9 21:04:59 ayush-laptop kernel: [17179574.540000] Uniform CD-ROM driver Revision: 3.20
Mar  9 21:04:59 ayush-laptop kernel: [17179574.856000] usbcore: registered new driver usbfs
Mar  9 21:04:59 ayush-laptop kernel: [17179574.856000] usbcore: registered new driver hub
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] USB Universal Host Controller Interface driver v3.0
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] usb usb1: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] hub 1-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] hub 1-0:1.0: 2 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] usb usb2: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] hub 2-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] hub 2-0:1.0: 2 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] usb usb3: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] hub 3-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] hub 3-0:1.0: 2 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: debug port 1
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] usb usb4: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] hub 4-0:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179575.176000] hub 4-0:1.0: 6 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179575.312000] Attempting manual resume
Mar  9 21:04:59 ayush-laptop kernel: [17179575.336000] kjournald starting.  Commit interval 5 seconds
Mar  9 21:04:59 ayush-laptop kernel: [17179575.336000] EXT3-fs: mounted filesystem with ordered data mode.
Mar  9 21:04:59 ayush-laptop kernel: [17179575.564000] usb 4-3: new high speed USB device using ehci_hcd and address 2
Mar  9 21:04:59 ayush-laptop kernel: [17179575.696000] usb 4-3: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179575.696000] hub 4-3:1.0: USB hub found
Mar  9 21:04:59 ayush-laptop kernel: [17179575.696000] hub 4-3:1.0: 4 ports detected
Mar  9 21:04:59 ayush-laptop kernel: [17179576.000000] usb 4-3.1: new high speed USB device using ehci_hcd and address 3
Mar  9 21:04:59 ayush-laptop kernel: [17179576.092000] usb 4-3.1: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179576.292000] usb 4-3.3: new full speed USB device using ehci_hcd and address 4
Mar  9 21:04:59 ayush-laptop kernel: [17179576.384000] usb 4-3.3: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179576.584000] usb 4-3.4: new low speed USB device using ehci_hcd and address 5
Mar  9 21:04:59 ayush-laptop kernel: [17179576.676000] usb 4-3.4: configuration #1 chosen from 1 choice
Mar  9 21:04:59 ayush-laptop kernel: [17179587.820000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  9 21:04:59 ayush-laptop kernel: [17179587.824000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  9 21:04:59 ayush-laptop kernel: [17179588.092000] NET: Registered protocol family 23
Mar  9 21:04:59 ayush-laptop kernel: [17179588.172000] hw_random: RNG not detected
Mar  9 21:04:59 ayush-laptop kernel: [17179588.192000] Floppy drive(s): fd0 is 1.44M
Mar  9 21:04:59 ayush-laptop kernel: [17179588.220000] FDC 0 is a National Semiconductor PC87306
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] pnp: Device 00:0c activated.
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, chip->init
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, Found chip at base=0x02e
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, driver loaded (Dag Brattli)
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] IrDA: Registered device irda0
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Mar  9 21:04:59 ayush-laptop kernel: [17179588.808000] parport: PnPBIOS parport detected.
Mar  9 21:04:59 ayush-laptop kernel: [17179588.812000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Mar  9 21:04:59 ayush-laptop kernel: [17179588.928000] Linux agpgart interface v0.101 (c) Dave Jones
Mar  9 21:04:59 ayush-laptop kernel: [17179588.932000] agpgart: Detected an Intel 855PM Chipset.
Mar  9 21:04:59 ayush-laptop kernel: [17179588.948000] agpgart: AGP aperture is 256M @ 0xd0000000
Mar  9 21:04:59 ayush-laptop kernel: [17179589.008000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Mar  9 21:04:59 ayush-laptop kernel: [17179589.008000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Mar  9 21:04:59 ayush-laptop kernel: [17179589.032000] input: PC Speaker as /class/input/input1
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] Driver 'ipw2200' needs updating - please use bus_type methods
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.256000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Mar  9 21:04:59 ayush-laptop kernel: [17179589.428000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta: Using INTVAL to route CSC interrupts to PCI
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta: Routing CardBus interrupts to PCI
Mar  9 21:04:59 ayush-laptop kernel: [17179589.432000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
Mar  9 21:04:59 ayush-laptop kernel: [17179589.436000] usbcore: registered new driver libusual
Mar  9 21:04:59 ayush-laptop kernel: [17179589.456000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3F11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.456000] usbcore: registered new driver usblp
Mar  9 21:04:59 ayush-laptop kernel: [17179589.456000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Mar  9 21:04:59 ayush-laptop kernel: [17179589.472000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
Mar  9 21:04:59 ayush-laptop kernel: [17179589.472000] e100: Copyright(c) 1999-2005 Intel Corporation
Mar  9 21:04:59 ayush-laptop kernel: [17179589.560000] usbcore: registered new driver hiddev
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] input: HID 04b3:3107 as /class/input/input2
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] input: USB HID v1.00 Mouse [HID 04b3:3107] on usb-0000:00:1d.7-3.4
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] usbcore: registered new driver usbhid
Mar  9 21:04:59 ayush-laptop kernel: [17179589.564000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Mar  9 21:04:59 ayush-laptop kernel: [17179589.632000] SCSI subsystem initialized
Mar  9 21:04:59 ayush-laptop kernel: [17179589.632000] Initializing USB Mass Storage driver...
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] scsi0 : SCSI emulation for USB Mass Storage devices
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] usbcore: registered new driver usb-storage
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] USB Mass Storage support registered.
Mar  9 21:04:59 ayush-laptop kernel: [17179589.660000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
Mar  9 21:04:59 ayush-laptop kernel: [17179589.660000] serio: Synaptics pass-through port at isa0060/serio1/input0
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] Yenta: ISA IRQ mask 0x0430, PCI irq 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] Socket status: 30000086
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] cs: IO port probe 0x4000-0x8fff: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179589.664000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
Mar  9 21:04:59 ayush-laptop kernel: [17179589.672000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.672000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.696000] e100: eth0: e100_probe: addr 0xc0205000, irq 11, MAC addr 00:16:41:53:2A:ED
Mar  9 21:04:59 ayush-laptop kernel: [17179589.696000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:04:59 ayush-laptop kernel: [17179589.724000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Mar  9 21:04:59 ayush-laptop kernel: [17179589.800000] ts: Compaq touchscreen protocol output
Mar  9 21:04:59 ayush-laptop kernel: [17179589.864000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0x100-0x3af: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0x820-0x8ff: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0xc00-0xcf7: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.068000] cs: IO port probe 0xa00-0xaff: clean.
Mar  9 21:04:59 ayush-laptop kernel: [17179590.516000] intel8x0_measure_ac97_clock: measured 55485 usecs
Mar  9 21:04:59 ayush-laptop kernel: [17179590.516000] intel8x0: clocking to 48000
Mar  9 21:04:59 ayush-laptop kernel: [17179590.668000] lp0: using parport0 (interrupt-driven).
Mar  9 21:04:59 ayush-laptop kernel: [17179590.676000] NET: Registered protocol family 17
Mar  9 21:04:59 ayush-laptop kernel: [17179590.724000] fuse init (API version 7.6)
Mar  9 21:04:59 ayush-laptop kernel: [17179590.744000] Adding 1325352k swap on /dev/disk/by-uuid/d193ad29-3512-45d7-89cd-392abf295430.  Priority:-1 extents:1 across:1325352k
Mar  9 21:04:59 ayush-laptop kernel: [17179590.852000] EXT3 FS on hda3, internal journal
Mar  9 21:04:59 ayush-laptop kernel: [17179591.024000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Mar  9 21:04:59 ayush-laptop kernel: [17179591.080000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
Mar  9 21:04:59 ayush-laptop kernel: [17179591.100000] NTFS volume version 3.1.
Mar  9 21:04:59 ayush-laptop kernel: [17179591.152000] NTFS volume version 3.1.
Mar  9 21:04:59 ayush-laptop kernel: [17179594.636000]   Vendor: ST332062  Model: 0A                Rev: 0000
Mar  9 21:04:59 ayush-laptop kernel: [17179594.636000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar  9 21:04:59 ayush-laptop kernel: [17179594.668000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Write Protect is off
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Write Protect is off
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000]  sda: sda1
Mar  9 21:04:59 ayush-laptop kernel: [17179594.676000] sd 0:0:0:0: Attached scsi disk sda
Mar  9 21:04:59 ayush-laptop kernel: [17179594.692000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar  9 21:04:59 ayush-laptop kernel: [17179595.620000] ACPI: AC Adapter [AC] (on-line)
Mar  9 21:04:59 ayush-laptop kernel: [17179595.652000] ACPI: Battery Slot [BAT0] (battery absent)
Mar  9 21:04:59 ayush-laptop kernel: [17179595.668000] ACPI: Power Button (FF) [PWRF]
Mar  9 21:04:59 ayush-laptop kernel: [17179595.668000] ACPI: Lid Switch [LID]
Mar  9 21:04:59 ayush-laptop kernel: [17179595.668000] ACPI: Sleep Button (CM) [SLPB]
Mar  9 21:04:59 ayush-laptop kernel: [17179595.700000] ACPI: ACPI Dock Station Driver 
Mar  9 21:04:59 ayush-laptop kernel: [17179595.788000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
Mar  9 21:04:59 ayush-laptop kernel: [17179595.788000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Mar  9 21:04:59 ayush-laptop kernel: [17179595.804000] pcc_acpi: loading...
Mar  9 21:04:59 ayush-laptop kernel: [17179595.928000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Mar  9 21:05:01 ayush-laptop kernel: [17179598.424000] [drm] Initialized drm 1.0.1 20051102
Mar  9 21:05:01 ayush-laptop kernel: [17179598.440000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Mar  9 21:05:01 ayush-laptop kernel: [17179598.444000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
Mar  9 21:05:02 ayush-laptop last message repeated 2 times
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Mar  9 21:05:02 ayush-laptop kernel: [17179599.816000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Mar  9 21:05:02 ayush-laptop kernel: [17179600.072000] [drm] Setting GART location based on new memory map
Mar  9 21:05:02 ayush-laptop kernel: [17179600.072000] [drm] writeback test succeeded in 2 usecs
Mar  9 21:05:03 ayush-laptop hpiod: 1.6.9 accepting connections at 2208... 
Mar  9 21:05:03 ayush-laptop kernel: [17179601.020000] IBM machine detected. Enabling interrupts during APM calls.
Mar  9 21:05:03 ayush-laptop kernel: [17179601.020000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Mar  9 21:05:03 ayush-laptop kernel: [17179601.020000] apm: overridden by ACPI.
Mar  9 21:05:08 ayush-laptop dhcdbd: Started up.
Mar  9 21:05:08 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar  9 21:05:08 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] Bluetooth: Core ver 2.8
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] NET: Registered protocol family 31
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] Bluetooth: HCI device and connection manager initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.576000] Bluetooth: HCI socket layer initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.636000] Bluetooth: L2CAP ver 2.8
Mar  9 21:05:10 ayush-laptop kernel: [17179607.636000] Bluetooth: L2CAP socket layer initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.640000] Bluetooth: RFCOMM socket layer initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.640000] Bluetooth: RFCOMM TTY layer initialized
Mar  9 21:05:10 ayush-laptop kernel: [17179607.640000] Bluetooth: RFCOMM ver 1.7
Mar  9 21:05:10 ayush-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar  9 21:05:10 ayush-laptop dhcpd: All rights reserved.
Mar  9 21:05:10 ayush-laptop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  9 21:05:10 ayush-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar  9 21:05:10 ayush-laptop dhcpd: All rights reserved.
Mar  9 21:05:10 ayush-laptop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  9 21:05:10 ayush-laptop dhcpd: Wrote 0 leases to leases file.
Mar  9 21:05:10 ayush-laptop dhcpd: 
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  9 21:05:12 ayush-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar  9 21:05:12 ayush-laptop kernel: [17179610.268000] Non-volatile memory driver v1.2
Mar  9 21:08:50 ayush-laptop gconfd (ayush-4975): starting (version 2.16.0), pid 4975 user 'ayush'
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readwrite:/home/ayush/.gconf" to a writable configuration source at position 1
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar  9 21:08:51 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar  9 21:08:55 ayush-laptop gconfd (ayush-4975): Resolved address "xml:readwrite:/home/ayush/.gconf" to a writable configuration source at position 0




---

### Post by elvis_shock on 2007-03-09
**_DEBUG_**


> Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] On node 0 totalpages: 196432
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000]   Normal zone: 192336 pages, LIFO batch:31
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f6d70
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: XSDT (v001 IBM    TP-1R    0x00003200  LTP 0x00000000) @ 0x2ff5a6cd
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: FADT (v003 IBM    TP-1R    0x00003200 IBM  0x00000001) @ 0x2ff5a800
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: SSDT (v001 IBM    TP-1R    0x00003200 MSFT 0x0100000e) @ 0x2ff5a9b4
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: ECDT (v001 IBM    TP-1R    0x00003200 IBM  0x00000001) @ 0x2ff66ebc
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: TCPA (v001 IBM    TP-1R    0x00003200 PTL  0x00000001) @ 0x2ff66f0e
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: BOOT (v001 IBM    TP-1R    0x00003200  LTP 0x00000001) @ 0x2ff66fd8
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] ACPI: DSDT (v001 IBM    TP-1R    0x00003200 MSFT 0x0100000e) @ 0x00000000
Mar  9 21:04:59 ayush-laptop kernel: [17179569.184000] mapped APIC to ffffd000 (0160c000)
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Mar  9 21:04:59 ayush-laptop kernel: [17179569.904000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
Mar  9 21:04:59 ayush-laptop kernel: [17179570.492000] PCI: Probing PCI hardware (bus 00)
Mar  9 21:04:59 ayush-laptop kernel: [17179570.496000] Boot video device is 0000:01:00.0
Mar  9 21:04:59 ayush-laptop kernel: [17179570.496000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar  9 21:04:59 ayush-laptop kernel: [17179570.504000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Mar  9 21:04:59 ayush-laptop kernel: [17179570.504000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179570.520000] PCI: setting IRQ 11 as level-triggered
Mar  9 21:04:59 ayush-laptop kernel: [17179572.432000] Probing IDE interface ide0...
Mar  9 21:04:59 ayush-laptop kernel: [17179573.408000] Probing IDE interface ide1...
Mar  9 21:04:59 ayush-laptop kernel: [17179574.860000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179574.964000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179575.068000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179575.172000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Mar  9 21:04:59 ayush-laptop kernel: [17179588.092000] irda_init()
Mar  9 21:04:59 ayush-laptop kernel: [17179588.252000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Mar  9 21:04:59 ayush-laptop kernel: [17179589.008000] ieee80211_crypt: registered algorithm 'NULL'
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] usb-storage: device found at 3
Mar  9 21:04:59 ayush-laptop kernel: [17179589.636000] usb-storage: waiting for device to settle before scanning
Mar  9 21:04:59 ayush-laptop kernel: [17179589.696000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Mar  9 21:04:59 ayush-laptop kernel: [17179594.636000] usb-storage: device scan complete
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Mode Sense: 27 00 00 00
Mar  9 21:04:59 ayush-laptop kernel: [17179594.672000] sda: Mode Sense: 27 00 00 00
Mar  9 21:08:58 ayush-laptop kernel: [17179835.396000] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar  9 21:08:58 ayush-laptop kernel: [17179835.528000] ISOFS: changing to secondary root
Mar  9 21:10:54 ayush-laptop hcid[4520]: name_listener_add(:1.15)


---

### Post by elvis_shock on 2007-03-09
**_Daemon.log_**


> 
Mar  9 21:04:59 ayush-laptop ntpdate[3437]: step time server 82.211.81.145 offset -0.488821 sec
Mar  9 21:05:02 ayush-laptop named[4110]: starting BIND 9.3.2 -u bind
Mar  9 21:05:02 ayush-laptop named[4110]: found 1 CPU, using 1 worker thread
Mar  9 21:05:02 ayush-laptop named[4110]: loading configuration from '/etc/bind/named.conf'
Mar  9 21:05:02 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:02 ayush-laptop named[4110]: no IPv6 interfaces found
Mar  9 21:05:02 ayush-laptop named[4110]: listening on IPv4 interface lo, 127.0.0.1#53
Mar  9 21:05:02 ayush-laptop named[4110]: listening on IPv4 interface eth0, 172.20.167.151#53
Mar  9 21:05:02 ayush-laptop named[4110]: command channel listening on 127.0.0.1#953
Mar  9 21:05:02 ayush-laptop named[4110]: zone 0.in-addr.arpa/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: zone 127.in-addr.arpa/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: zone 255.in-addr.arpa/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: zone localhost/IN: loaded serial 1
Mar  9 21:05:02 ayush-laptop named[4110]: running
Mar  9 21:05:03 ayush-laptop ovpn-socvpn-linux[4128]: Options error: You must define CA file (--ca) or PKCS#12 file (--pkcs12)
Mar  9 21:05:03 ayush-laptop ovpn-socvpn-linux[4128]: Use --help for more information.
Mar  9 21:05:06 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Istarting... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'e100'. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IDeactivating device eth0. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IWill activate connection 'eth0'. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IDevice eth0 activation scheduled... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) started... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar  9 21:05:08 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar  9 21:05:09 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:09 ayush-laptop NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Mar  9 21:05:09 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar  9 21:05:09 ayush-laptop NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Mar  9 21:05:10 ayush-laptop hcid[4520]: Bluetooth HCI daemon
Mar  9 21:05:10 ayush-laptop hcid[4520]: Register path:/org/bluez fallback:1
Mar  9 21:05:10 ayush-laptop sdpd[4527]: Bluetooth SDP daemon 
Mar  9 21:05:10 ayush-laptop dhclient: isc-dhclient-V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar  9 21:05:10 ayush-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar  9 21:05:10 ayush-laptop dhcpd: All rights reserved.
Mar  9 21:05:10 ayush-laptop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  9 21:05:10 ayush-laptop NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Mar  9 21:05:12 ayush-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Mar  9 21:05:12 ayush-laptop dhclient: DHCPACK from 172.20.160.2
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  address 172.20.167.151 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  netmask 255.255.255.0 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  broadcast 172.20.167.255 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  gateway 172.20.167.1 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  nameserver 137.132.0.254 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  nameserver 137.132.0.252 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^I  domain name 'nus.edu.sg' 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar  9 21:05:12 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar  9 21:05:12 ayush-laptop dhclient: bound to 172.20.167.151 -- renewal in 6546 seconds.
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IDHCP returned name servers but system has disabled dynamic modification! 
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Mar  9 21:05:13 ayush-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar  9 21:05:13 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:13 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:14 ayush-laptop ntpdate[4800]: step time server 82.211.81.145 offset 0.001804 sec
Mar  9 21:05:19 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Mar  9 21:05:30 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar  9 21:05:37 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Mar  9 21:05:51 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Mar  9 21:05:55 ayush-laptop dhclient: No DHCPOFFERS received.
Mar  9 21:05:55 ayush-laptop dhclient: No working leases in persistent database - sleeping.
Mar  9 21:05:55 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:55 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:05:56 ayush-laptop ntpdate[4828]: step time server 82.211.81.145 offset -0.000058 sec
Mar  9 21:08:53 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:08:59 ayush-laptop ntfs-3g[5086]: Version 1.0 
Mar  9 21:08:59 ayush-laptop ntfs-3g[5086]: Mounted /dev/sda1 (Read-Write, label "Ext Drive", NTFS 3.1) 
Mar  9 21:08:59 ayush-laptop ntfs-3g[5086]: Options: noatime,rw,nosuid,nodev,user,nonempty,silent,allow_other,default_permissions,fsname=/dev/sda1 
Mar  9 21:09:19 ayush-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Mar  9 21:10:54 ayush-laptop hcid[4520]: name_listener_add(:1.15)
Mar  9 21:10:54 ayush-laptop hcid[4520]: Default passkey agent (:1.15, /org/bluez/applet) registered
Mar  9 21:10:55 ayush-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Mar  9 21:11:58 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar  9 21:12:05 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar  9 21:12:12 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Mar  9 21:12:26 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Mar  9 21:12:43 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Mar  9 21:12:56 ayush-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Mar  9 21:12:59 ayush-laptop dhclient: No DHCPOFFERS received.
Mar  9 21:12:59 ayush-laptop dhclient: No working leases in persistent database - sleeping.




---

### Post by elvis_shock on 2007-03-11
can someone please help me? I am really in need of help.

---

