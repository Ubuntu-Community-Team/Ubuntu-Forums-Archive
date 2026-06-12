---
title: "WLAN card disappeared (IPW3945)"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Seb1982 on 2007-04-08
Hi everyone!

I bought a new laptop yesterday (BenQ Joybook S73U) and put Ubuntu 6.10 on it. But sadly the Intel WLAN interface (ipw3945) causes some trouble.

A few hours ago i got so far that the bar next to the network item turned green, even if i still wasn't able to connect to the WLAN. Than, after a reboot, my interface suddenly disappeared! Ubuntu says that it doesn't exist, even if 'lspci' has a different opinion.

I bootet the earlier kernel version and tada, there it was! But I was not able to use it because of the driver (i guess).

Does anyone out there know, what's wrong with the interface?

Thanks and happy easter!

Seb

---

### Post by Seb1982 on 2007-04-08
By the way, this is the result auf 'sudo modprobe ipw3945':

FATAL: Error inserting ipw3945 (/lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
2007-04-08 22:08:14: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

Seb

---

### Post by handaxe on 2007-04-08
Make sure the linux restricted modules for your kernel are installed.

Reboot.

Check interface.

If problems then in terminal type ```
sudo lsmod | grep ipw
```

If ipw3945 gets returned then the module is loaded and we must look afresh.

HA

---

### Post by Seb1982 on 2007-04-08
Interesting, interesting!

I installed 'network-manager' and 'network-manager-gnome', pretty nice tool by the way.

When booting Kernel 2.6.17.11 nothing happens. My wired connection is managed by the new tool instead of the old one. And the Kernel does not discover the wireless interface.

But everything is different when booting the older 2.6.17.10 kernel! It works instantly and perfectly!!!

So i guess it's a driver problem. The following packages are installed:

linux-restricted-modules-2.6.17-10-generic
linux-restricted-modules-2.6.17-11-generic
linux-restricted-modules-common
linux-restricted-modules-generic

Does anyone know what might be wrong?

Seb

---

### Post by handaxe on 2007-04-09
Hi,

Under 2.6.17.11, is the driver module loading?

If not, does ```
sudo depmod -a
``` and then ```
sudo modprobe ipw3945
``` make any difference? (I can't tell whether your modprobe results reported were with the restricted modules installed or not).

I am on that kernel with the same card........

HA

---

### Post by Seb1982 on 2007-04-09
I do not knwo whether the module is loaded or not.

'sudo depmod -a' does something but i don't see the reslult.

'sudo modprobe ipw3945' returns the following:
```
FATAL: Error inserting ipw3945 (/lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
2007-04-09 11:35:15: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
```

---

### Post by Seb1982 on 2007-04-09
Maybe this could help! 'sudo dmesg' returns:

```
[17179571.824000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.824000] pnp: PnP ACPI init
[17179571.952000] pnp: PnP ACPI: found 8 devices
[17179571.952000] PnPBIOS: Disabled by ACPI PNP
[17179571.952000] PCI: Using ACPI for IRQ routing
[17179571.952000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.952000] pnp: 00:01: ioport range 0x164e-0x164f has been reserved
[17179571.952000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.952000] PCI: Bridge: 0000:00:1c.0
[17179571.952000]   IO window: 5000-5fff
[17179571.952000]   MEM window: 6b300000-6c2fffff
[17179571.952000]   PREFETCH window: 64100000-650fffff
[17179571.952000] PCI: Bridge: 0000:00:1c.1
[17179571.952000]   IO window: 4000-4fff
[17179571.952000]   MEM window: 6a200000-6b2fffff
[17179571.952000]   PREFETCH window: 65100000-660fffff
[17179571.952000] PCI: Bridge: 0000:00:1c.2
[17179571.952000]   IO window: 3000-3fff
[17179571.952000]   MEM window: 69200000-6a1fffff
[17179571.952000]   PREFETCH window: 66100000-670fffff
[17179571.952000] PCI: Bridge: 0000:00:1c.3
[17179571.952000]   IO window: 2000-2fff
[17179571.952000]   MEM window: 68100000-691fffff
[17179571.952000]   PREFETCH window: 67100000-680fffff
[17179571.952000] PCI: Bus 6, cardbus bridge: 0000:05:05.0
[17179571.952000]   IO window: 00001000-000010ff
[17179571.952000]   IO window: 00001400-000014ff
[17179571.952000]   PREFETCH window: 60000000-61ffffff
[17179571.952000]   MEM window: 62000000-63ffffff
[17179571.952000] PCI: Bridge: 0000:00:1e.0
[17179571.952000]   IO window: 1000-1fff
[17179571.952000]   MEM window: 62000000-640fffff
[17179571.952000]   PREFETCH window: 60000000-61ffffff
[17179571.952000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.952000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.952000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179571.952000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179571.952000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179571.952000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179571.952000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179571.952000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179571.952000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.952000] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.952000] PCI: Setting latency timer of device 0000:05:05.0 to 64
[17179571.952000] NET: Registered protocol family 2
[17179572.000000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.000000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.000000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.000000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.000000] TCP reno registered
[17179572.000000] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[17179572.000000] Simple Boot Flag at 0x44 set to 0x1
[17179572.004000] audit: initializing netlink socket (disabled)
[17179572.004000] audit(1176118417.004:1): initialized
[17179572.004000] highmem bounce pool size: 64 pages
[17179572.004000] VFS: Disk quotas dquot_6.5.1
[17179572.004000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.004000] Initializing Cryptographic API
[17179572.004000] io scheduler noop registered
[17179572.004000] io scheduler anticipatory registered
[17179572.004000] io scheduler deadline registered
[17179572.004000] io scheduler cfq registered (default)
[17179572.004000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.004000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.004000] assign_interrupt_mode Found MSI capability
[17179572.004000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179572.004000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179572.004000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179572.004000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179572.004000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179572.004000] assign_interrupt_mode Found MSI capability
[17179572.004000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179572.004000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179572.004000] Allocate Port Service[0000:00:1c.1:pcie03]
[17179572.004000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179572.004000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179572.004000] assign_interrupt_mode Found MSI capability
[17179572.004000] Allocate Port Service[0000:00:1c.2:pcie00]
[17179572.004000] Allocate Port Service[0000:00:1c.2:pcie02]
[17179572.004000] Allocate Port Service[0000:00:1c.2:pcie03]
[17179572.004000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179572.004000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179572.004000] assign_interrupt_mode Found MSI capability
[17179572.004000] Allocate Port Service[0000:00:1c.3:pcie00]
[17179572.004000] Allocate Port Service[0000:00:1c.3:pcie02]
[17179572.004000] Allocate Port Service[0000:00:1c.3:pcie03]
[17179572.004000] isapnp: Scanning for PnP cards...
[17179572.360000] isapnp: No Plug & Play device found
[17179572.404000] Real Time Clock Driver v1.12ac
[17179572.404000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.404000] mice: PS/2 mouse device common for all mice
[17179572.404000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.404000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.404000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.404000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[17179572.408000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.412000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.412000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.412000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.416000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.416000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.416000] EISA: Probing bus 0 at eisa.0
[17179572.416000] Cannot allocate resource for EISA slot 1
[17179572.416000] Cannot allocate resource for EISA slot 2
[17179572.416000] Cannot allocate resource for EISA slot 3
[17179572.416000] Cannot allocate resource for EISA slot 4
[17179572.416000] Cannot allocate resource for EISA slot 5
[17179572.416000] Cannot allocate resource for EISA slot 6
[17179572.416000] EISA: Detected 0 cards.
[17179572.416000] TCP bic registered
[17179572.416000] NET: Registered protocol family 1
[17179572.416000] NET: Registered protocol family 8
[17179572.416000] NET: Registered protocol family 20
[17179572.420000] Starting balanced_irq
[17179572.420000] Using IPI No-Shortcut mode
[17179572.420000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.420000] Freeing unused kernel memory: 308k freed
[17179572.428000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.576000] Capability LSM initialized
[17179573.640000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179573.644000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.644000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179573.644000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179573.652000] ACPI: Thermal Zone [TZ0] (35 C)
[17179574.288000] SCSI subsystem initialized
[17179574.292000] libata version 1.20 loaded.
[17179574.296000] ata_piix 0000:00:1f.2: version 1.05
[17179574.296000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 177
[17179574.296000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179574.296000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x60A0 irq 14
[17179574.460000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f09 84:6063 85:3469 86:be09 87:6063 88:203f
[17179574.460000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[17179574.468000] ata1: dev 0 configured for UDMA/100
[17179574.468000] scsi0 : ata_piix
[17179574.468000]   Vendor: ATA       Model: FUJITSU MHV2080B  Rev: 0000
[17179574.468000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179574.468000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x60A8 irq 15
[17179574.788000] ata2: dev 0 cfg 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179574.788000] ata2: dev 0 ATAPI, max UDMA/33
[17179574.788000] ata2(0): applying bridge limits
[17179574.960000] ata2: dev 0 configured for UDMA/33
[17179574.960000] scsi1 : ata_piix
[17179574.960000]   Vendor: MATSHITA  Model: DVD-RAM UJ-850S   Rev: 1.20
[17179574.960000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179574.976000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179574.976000] sda: Write Protect is off
[17179574.976000] sda: Mode Sense: 00 3a 00 00
[17179574.976000] SCSI device sda: drive cache: write back
[17179574.976000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179574.976000] sda: Write Protect is off
[17179574.976000] sda: Mode Sense: 00 3a 00 00
[17179574.976000] SCSI device sda: drive cache: write back
[17179574.976000]  sda: sda1 sda2 < sda5 > sda3
[17179575.088000] sd 0:0:0:0: Attached scsi disk sda
[17179575.492000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179575.492000] ide0: ports already in use, skipping probe
[17179575.492000] ide1: I/O resource 0x170-0x177 not free.
[17179575.492000] ide1: ports already in use, skipping probe
[17179575.552000] usbcore: registered new driver usbfs
[17179575.556000] usbcore: registered new driver hub
[17179575.556000] USB Universal Host Controller Interface driver v3.0
[17179575.556000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 22 (level, low) -> IRQ 50
[17179575.556000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.556000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.556000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.556000] uhci_hcd 0000:00:1d.0: irq 50, io base 0x00006080
[17179575.556000] usb usb1: configuration #1 chosen from 1 choice
[17179575.556000] hub 1-0:1.0: USB hub found
[17179575.556000] hub 1-0:1.0: 2 ports detected
[17179575.620000] ieee1394: Initialized config rom entry `ip1394'
[17179575.660000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179575.660000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.660000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.660000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.660000] uhci_hcd 0000:00:1d.1: irq 177, io base 0x00006060
[17179575.660000] usb usb2: configuration #1 chosen from 1 choice
[17179575.660000] hub 2-0:1.0: USB hub found
[17179575.660000] hub 2-0:1.0: 2 ports detected
[17179575.764000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179575.764000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.764000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.764000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.764000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00006040
[17179575.764000] usb usb3: configuration #1 chosen from 1 choice
[17179575.764000] hub 3-0:1.0: USB hub found
[17179575.764000] hub 3-0:1.0: 2 ports detected
[17179575.868000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179575.868000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179575.868000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179575.868000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179575.868000] uhci_hcd 0000:00:1d.3: irq 193, io base 0x00006020
[17179575.868000] usb usb4: configuration #1 chosen from 1 choice
[17179575.868000] hub 4-0:1.0: USB hub found
[17179575.868000] hub 4-0:1.0: 2 ports detected
[17179575.972000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 22 (level, low) -> IRQ 50
[17179575.972000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.972000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.972000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179575.972000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.972000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.972000] ehci_hcd 0000:00:1d.7: irq 50, io mem 0x6c444400
[17179575.976000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.976000] usb usb5: configuration #1 chosen from 1 choice
[17179575.976000] hub 5-0:1.0: USB hub found
[17179575.976000] hub 5-0:1.0: 8 ports detected
[17179576.080000] ACPI: PCI Interrupt 0000:05:05.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179576.080000] PCI: Setting latency timer of device 0000:05:05.1 to 64
[17179576.128000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[64006000-640067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179576.160000] Attempting manual resume
[17179576.216000] kjournald starting.  Commit interval 5 seconds
[17179576.216000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.400000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d001003ee6a0]
[17179587.656000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.696000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.724000] hw_random: RNG not detected
[17179588.056000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.060000] agpgart: Detected an Intel 945GM Chipset.
[17179588.064000] agpgart: Detected 7932K stolen memory.
[17179588.084000] agpgart: AGP aperture is 256M @ 0x50000000
[17179588.376000] tg3.c:v3.59.1 (August 25, 2006)
[17179588.376000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179588.376000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[17179588.412000] eth0: Tigon3 [partno(BCM95789) rev 4201 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:40:d0:9d:a6:74
[17179588.412000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179588.412000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[17179588.424000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.456000] ieee80211: 802.11 data/management/control stack, 1.2.17
[17179588.456000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.556000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 23 (level, low) -> IRQ 58
[17179588.556000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179588.564000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x92a0b1, caps: 0xa04713/0x200000
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encodeext
[17179588.612000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encode
[17179588.612000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encode
[17179588.612000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_txb_free
[17179588.612000] ipw3945: Unknown symbol ieee80211_txb_free
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encodeext
[17179588.612000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_wx_get_scan
[17179588.612000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_freq_to_channel
[17179588.612000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_set_geo
[17179588.612000] ipw3945: Unknown symbol ieee80211_set_geo
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_rx
[17179588.612000] ipw3945: Unknown symbol ieee80211_rx
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_get_channel
[17179588.612000] ipw3945: Unknown symbol ieee80211_get_channel
[17179588.612000] ipw3945: disagrees about version of symbol ieee80211_channel_to_index
[17179588.612000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17179588.616000] ipw3945: disagrees about version of symbol ieee80211_rx_mgt
[17179588.616000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17179588.616000] ipw3945: disagrees about version of symbol ieee80211_get_geo
[17179588.616000] ipw3945: Unknown symbol ieee80211_get_geo
[17179588.616000] ipw3945: disagrees about version of symbol free_ieee80211
[17179588.616000] ipw3945: Unknown symbol free_ieee80211
[17179588.616000] ipw3945: disagrees about version of symbol ieee80211_tx_frame
[17179588.616000] ipw3945: Unknown symbol ieee80211_tx_frame
[17179588.616000] ipw3945: disagrees about version of symbol ieee80211_is_valid_channel
[17179588.616000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17179588.616000] ipw3945: disagrees about version of symbol ieee80211_get_channel_flags
[17179588.616000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17179588.616000] ipw3945: disagrees about version of symbol alloc_ieee80211
[17179588.616000] ipw3945: Unknown symbol alloc_ieee80211
[17179588.616000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179588.776000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179588.776000] sdhci: Copyright(c) Pierre Ossman
[17179588.800000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179588.804000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179588.812000] ts: Compaq touchscreen protocol output
[17179588.852000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[17179588.852000] Uniform CD-ROM driver Revision: 3.20
[17179588.852000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179588.940000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[17179589.268000] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.268000] Yenta: CardBus bridge found at 0000:05:05.0 [17ff:0600]
[17179589.268000] Yenta: Enabling burst memory read transactions
[17179589.268000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.268000] Yenta: Routing CardBus interrupts to PCI
[17179589.268000] Yenta TI: socket 0000:05:05.0, mfunc 0x01aa1b22, devctl 0x64
[17179589.500000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[17179589.500000] Socket status: 30000006
[17179589.500000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[17179589.500000] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[17179589.500000] cs: IO port probe 0x1000-0x1fff: clean.
[17179589.500000] pcmcia: parent PCI bridge Memory window: 0x62000000 - 0x640fffff
[17179589.500000] pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x61ffffff
[17179589.500000] ACPI: PCI Interrupt 0000:05:05.2[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.500000] PCI: Setting latency timer of device 0000:05:05.2 to 64
[17179589.500000] sdhci: SDHCI controller found at 0000:05:05.3 [104c:803c] (rev 0)
[17179589.500000] ACPI: PCI Interrupt 0000:05:05.3[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.500000] mmc0: SDHCI at 0x64006800 irq 169 PIO
[17179589.868000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x377
[17179589.872000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x418-0x47f 0x4d0-0x4d7
[17179589.872000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.872000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.872000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.048000] lp: driver loaded but no devices found
[17179590.088000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179590.088000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179590.132000] Adding 3004112k swap on /dev/disk/by-uuid/6208a5a5-b2b4-4d59-a8de-d765d2aad2c1.  Priority:-1 extents:1 across:3004112k
[17179590.208000] EXT3 FS on sda1, internal journal
[17179591.848000] ACPI: AC Adapter [AC] (off-line)
[17179592.300000] ACPI: Battery Slot [BAT0] (battery present)
[17179592.332000] ACPI: Power Button (FF) [PWRF]
[17179592.332000] ACPI: Lid Switch [LID0]
[17179592.332000] ACPI: Sleep Button (CM) [SLPB]
[17179592.572000] ibm_acpi: ec object not found
[17179592.624000] pcc_acpi: loading...
[17179592.828000] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[17179596.476000] [drm] Initialized drm 1.0.1 20051102
[17179596.480000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179596.480000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179596.596000] apm: BIOS not found.
[17179600.112000] PM: Writing back config space on device 0000:04:00.0 at offset 1 (was 100406, writing 100006)
[17179600.900000] Bluetooth: Core ver 2.8
[17179600.900000] NET: Registered protocol family 31
[17179600.900000] Bluetooth: HCI device and connection manager initialized
[17179600.900000] Bluetooth: HCI socket layer initialized
[17179600.920000] Bluetooth: L2CAP ver 2.8
[17179600.920000] Bluetooth: L2CAP socket layer initialized
[17179600.924000] Bluetooth: RFCOMM socket layer initialized
[17179600.924000] Bluetooth: RFCOMM TTY layer initialized
[17179600.924000] Bluetooth: RFCOMM ver 1.7
[17179601.888000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179601.888000] tg3: eth0: Flow control is on for TX and on for RX.
[17179604.076000] NET: Registered protocol family 17
[17179605.784000] NET: Registered protocol family 10
[17179605.784000] lo: Disabled Privacy Extensions
[17179605.784000] IPv6 over IPv4 tunneling driver
[17179613.300000] smbfs: mount_data version 1684370019 is not supported
[17179613.300000] smbfs: mount_data version 1684370019 is not supported
[17179613.300000] smbfs: mount_data version 1684370019 is not supported
[17179613.300000] smbfs: mount_data version 1684370019 is not supported
[17179623.224000] eth0: no IPv6 routers present
[17179670.676000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encodeext
[17179670.676000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17179670.676000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encode
[17179670.676000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17179670.676000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encode
[17179670.676000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17179670.676000] ipw3945: disagrees about version of symbol ieee80211_txb_free
[17179670.676000] ipw3945: Unknown symbol ieee80211_txb_free
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encodeext
[17179670.680000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_wx_get_scan
[17179670.680000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_freq_to_channel
[17179670.680000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_set_geo
[17179670.680000] ipw3945: Unknown symbol ieee80211_set_geo
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_rx
[17179670.680000] ipw3945: Unknown symbol ieee80211_rx
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_get_channel
[17179670.680000] ipw3945: Unknown symbol ieee80211_get_channel
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_channel_to_index
[17179670.680000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_rx_mgt
[17179670.680000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_get_geo
[17179670.680000] ipw3945: Unknown symbol ieee80211_get_geo
[17179670.680000] ipw3945: disagrees about version of symbol free_ieee80211
[17179670.680000] ipw3945: Unknown symbol free_ieee80211
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_tx_frame
[17179670.680000] ipw3945: Unknown symbol ieee80211_tx_frame
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_is_valid_channel
[17179670.680000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17179670.680000] ipw3945: disagrees about version of symbol ieee80211_get_channel_flags
[17179670.680000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17179670.680000] ipw3945: disagrees about version of symbol alloc_ieee80211
[17179670.680000] ipw3945: Unknown symbol alloc_ieee80211
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encodeext
[17180229.216000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encode
[17180229.216000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encode
[17180229.216000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_txb_free
[17180229.216000] ipw3945: Unknown symbol ieee80211_txb_free
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encodeext
[17180229.216000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_wx_get_scan
[17180229.216000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_freq_to_channel
[17180229.216000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_set_geo
[17180229.216000] ipw3945: Unknown symbol ieee80211_set_geo
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_rx
[17180229.216000] ipw3945: Unknown symbol ieee80211_rx
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_get_channel
[17180229.216000] ipw3945: Unknown symbol ieee80211_get_channel
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_channel_to_index
[17180229.216000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_rx_mgt
[17180229.216000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_get_geo
[17180229.216000] ipw3945: Unknown symbol ieee80211_get_geo
[17180229.216000] ipw3945: disagrees about version of symbol free_ieee80211
[17180229.216000] ipw3945: Unknown symbol free_ieee80211
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_tx_frame
[17180229.216000] ipw3945: Unknown symbol ieee80211_tx_frame
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_is_valid_channel
[17180229.216000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17180229.216000] ipw3945: disagrees about version of symbol ieee80211_get_channel_flags
[17180229.216000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17180229.216000] ipw3945: disagrees about version of symbol alloc_ieee80211
[17180229.216000] ipw3945: Unknown symbol alloc_ieee80211

```

---

### Post by handaxe on 2007-04-09
My guess is that you have ipw3945d-2.6.17-10-generic and not ipw3945d-2.6.17-11-generic
on your machine.

```
ls /sbin/ipw*
``` should show this.

If so, you could uninstall  linux-restricted-modules-2.6.17-10-generic and re-install  linux-restricted-modules-2.6.17-11-generic and see if the series 17-11 kernel ipw driver then loads.

Alternatively, once running the 2.6.17.11 kernel, you can

```
uname -r 
```(to check the running kernel version)

```
sudo cp /sbin/ipw3945d-2.6.17-10-generic /sbin/ipw3945d-`uname -r`
sudo depmod -a
sudo modprobe ipw3945
```

HA

---

