---
title: "Internet problems with Ubuntu"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by uposer111 on 2007-09-05
When i tried ubuntu out on the Live cd, the internet already worked without any configuration. Now that i setup a dual boot with windows vista and ubuntu, only my windows has internet. I have a regular cable modem connected to my PC, no wireless.

[IMG]http://i74.photobucket.com/albums/i274/levidicus/Screenshot3.png[/IMG]

[IMG]http://i74.photobucket.com/albums/i274/levidicus/Screenshot2.png[/IMG]

[IMG]http://i74.photobucket.com/albums/i274/levidicus/Screenshot1.png[/IMG]

Thanks in advance

Jeff

---

### Post by krazy1912 on 2007-09-05
What's with the backround?

---

### Post by uposer111 on 2007-09-05
Yeh its pictures that a friend of mine makes. [www.spookyart.com](www.spookyart.com)

Jeff

---

### Post by PeterF on 2007-09-05
If the live-CD had Internet connection it should work now.
In your screen-shots I can't see the Network manager, check in Synaptic if it's installed
(network-manager and network-manager-gnome).
The network manager works best if no manual configuration is done, to check launch the terminal and type:

```
sudo gedit /etc/network/interfaces
```

the file should only contain the description for the loopback interface

```
auto lo
iface lo inet loopback
```

if there are more lines for eth0 or others remove those. Then reboot your system and the network icon should appear next to the clock, here you can connect to your wired network (if not already connected).

---

### Post by uposer111 on 2007-09-05
I tried what you said and here is what happened. I do not have the network manager installed.

[IMG]http://i74.photobucket.com/albums/i274/levidicus/Screenshot.png[/IMG]

Thanks,

Jeff

---

### Post by uposer111 on 2007-09-06
bump

---

### Post by noob12 on 2007-09-06
Please post the result of these commands:
```

lspci -nn

sudo lshw -C network

ifconfig -a

```
Text works.  We don't need screenshots.  (I'm  spooked already :-) )

---

### Post by uposer111 on 2007-09-06
Here is what i got.

lspci -nn
```
0000:00:00.0 0600: 8086:29a0 (rev 02)
0000:00:01.0 0604: 8086:29a1 (rev 02)
0000:00:19.0 0200: 8086:104b (rev 02)
0000:00:1a.0 0c03: 8086:2834 (rev 02)
0000:00:1a.1 0c03: 8086:2835 (rev 02)
0000:00:1a.7 0c03: 8086:283a (rev 02)
0000:00:1b.0 0403: 8086:284b (rev 02)
0000:00:1c.0 0604: 8086:283f (rev 02)
0000:00:1c.4 0604: 8086:2847 (rev 02)
0000:00:1d.0 0c03: 8086:2830 (rev 02)
0000:00:1d.1 0c03: 8086:2831 (rev 02)
0000:00:1d.2 0c03: 8086:2832 (rev 02)
0000:00:1d.7 0c03: 8086:2836 (rev 02)
0000:00:1e.0 0604: 8086:244e (rev f2)
0000:00:1f.0 0601: 8086:2812 (rev 02)
0000:00:1f.2 0104: 8086:2822 (rev 02)
0000:00:1f.3 0c05: 8086:283e (rev 02)
0000:01:00.0 0300: 1002:7280 (rev 9a)
0000:01:00.1 0380: 1002:72a0 (rev 9a)
0000:04:05.0 0780: 14f1:2f20
```

sudo lshw -C network```

*-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:dffe0000-dfffffff iomemory:dffdb000-dffdbfff ioport:ecc0-ecdf irq:10
```


ifconfig -a```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:864 (864.0 b)  TX bytes:864 (864.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
lspci -nn
```

Thanks
Jeff

---

### Post by noob12 on 2007-09-06
OK.  The driver hasn't claimed the device.   I think 8086:104b is your ethernet card; **lspci -vv** would verify.  The e1000 driver should claim it.  We need to look at your **dmesg** to see why not.

Can you post the output of 
```

dmesg

```

---

### Post by uposer111 on 2007-09-06
Here is what came up with

dmesg
```
[17179569.184000] Memory: 2066888k/2095436k available (1976k kernel code, 27352k reserved, 606k data, 288k init, 1177932k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1862.026 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3726.71 BogoMIPS (lpj=7453420)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000040 0000e3bd 00000000 00000001
[17179569.268000] mtrr: v2.0 (20020519)
[17179569.268000] CPU: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[17179569.268000] Enabling fast FPU save and restore... done.
[17179569.268000] Enabling unmasked SIMD FPU exception support... done.
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] checking if image is initramfs... it is
[17179569.804000] Freeing initrd memory: 6840k freed
[17179569.824000] ACPI: Looking for DSDT ... not found!
[17179569.924000] ENABLING IO-APIC IRQs
[17179569.924000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.076000] NET: Registered protocol family 16
[17179570.076000] EISA bus registered
[17179570.076000] ACPI: bus type pci registered
[17179570.092000] PCI: PCI BIOS revision 2.10 entry at 0xfb77d, last bus=4
[17179570.092000] PCI: Using MMCONFIG
[17179570.092000] ACPI: Subsystem revision 20051216
[17179570.176000] ACPI: Interpreter enabled
[17179570.176000] ACPI: Using IOAPIC for interrupt routing
[17179570.180000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.180000] PCI: Probing PCI hardware (bus 00)
[17179570.180000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.224000] Boot video device is 0000:01:00.0
[17179570.224000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.896000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[17179571.908000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[17179571.928000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.940000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[17179572.016000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179572.016000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179572.020000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179572.020000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179572.020000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179572.024000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179572.024000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179572.028000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[17179572.028000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.028000] pnp: PnP ACPI init
[17179572.080000] pnp: PnP ACPI: found 8 devices
[17179572.080000] PnPBIOS: Disabled by ACPI PNP
[17179572.080000] PCI: Using ACPI for IRQ routing
[17179572.080000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.112000] pnp: 00:00: ioport range 0x800-0x85f could not be reserved
[17179572.112000] pnp: 00:00: ioport range 0xc00-0xc7f has been reserved
[17179572.112000] pnp: 00:00: ioport range 0x860-0x8ff has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x100-0x1fe has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x200-0x277 has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x280-0x2e7 has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x2e8-0x2ef has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x2f0-0x2f7 has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x2f8-0x2ff has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x300-0x377 has been reserved
[17179572.112000] pnp: 00:06: ioport range 0x380-0x3bb has been reserved
[17179572.112000] PCI: Bridge: 0000:00:01.0
[17179572.112000]   IO window: d000-dfff
[17179572.112000]   MEM window: dfd00000-dfefffff
[17179572.112000]   PREFETCH window: c0000000-cfffffff
[17179572.112000] PCI: Bridge: 0000:00:1c.0
[17179572.112000]   IO window: disabled.
[17179572.112000]   MEM window: dfc00000-dfcfffff
[17179572.112000]   PREFETCH window: disabled.
[17179572.112000] PCI: Bridge: 0000:00:1c.4
[17179572.112000]   IO window: disabled.
[17179572.112000]   MEM window: disabled.
[17179572.112000]   PREFETCH window: disabled.
[17179572.112000] PCI: Bridge: 0000:00:1e.0
[17179572.112000]   IO window: c000-cfff
[17179572.112000]   MEM window: dfb00000-dfbfffff
[17179572.112000]   PREFETCH window: disabled.
[17179572.112000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.112000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.112000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.112000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.112000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.112000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[17179572.112000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.112000] Simple Boot Flag at 0x7a set to 0x1
[17179572.112000] audit: initializing netlink socket (disabled)
[17179572.112000] audit(1189114634.112:1): initialized
[17179572.112000] highmem bounce pool size: 64 pages
[17179572.112000] VFS: Disk quotas dquot_6.5.1
[17179572.112000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.112000] Initializing Cryptographic API
[17179572.112000] io scheduler noop registered
[17179572.112000] io scheduler anticipatory registered
[17179572.112000] io scheduler deadline registered
[17179572.112000] io scheduler cfq registered
[17179572.128000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.128000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.128000] assign_interrupt_mode Found MSI capability
[17179572.128000] Allocate Port Service[pcie00]
[17179572.128000] Allocate Port Service[pcie03]
[17179572.128000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.128000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.128000] assign_interrupt_mode Found MSI capability
[17179572.128000] Allocate Port Service[pcie00]
[17179572.128000] Allocate Port Service[pcie02]
[17179572.128000] Allocate Port Service[pcie03]
[17179572.128000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.128000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[17179572.128000] assign_interrupt_mode Found MSI capability
[17179572.128000] Allocate Port Service[pcie00]
[17179572.128000] Allocate Port Service[pcie02]
[17179572.128000] Allocate Port Service[pcie03]
[17179572.128000] isapnp: Scanning for PnP cards...
[17179572.480000] isapnp: No Plug & Play device found
[17179572.492000] hpet_resources: 0xfed00000 is busy
[17179572.492000] PNP: No PS/2 controller found. Probing ports directly.
[17179572.492000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.492000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.492000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.492000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.492000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.492000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.492000] mice: PS/2 mouse device common for all mice
[17179572.496000] EISA: Probing bus 0 at eisa.0
[17179572.496000] Cannot allocate resource for EISA slot 2
[17179572.496000] Cannot allocate resource for EISA slot 5
[17179572.496000] Cannot allocate resource for EISA slot 6
[17179572.496000] EISA: Detected 0 cards.
[17179572.496000] NET: Registered protocol family 2
[17179572.532000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.532000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179572.532000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.532000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.532000] TCP reno registered
[17179572.532000] TCP bic registered
[17179572.532000] NET: Registered protocol family 1
[17179572.532000] NET: Registered protocol family 8
[17179572.532000] NET: Registered protocol family 20
[17179572.532000] Using IPI Shortcut mode
[17179572.532000] ACPI wakeup devices:
[17179572.532000] VBTN PCI0 PCI4 PCI2 PCI3 PCI1 PCI5 PCI6 USB0 USB1 USB2 USB3 USB4
[17179572.532000] ACPI: (supports S0 S3 S4 S5)
[17179572.532000] Freeing unused kernel memory: 288k freed
[17179572.568000] vga16fb: initializing
[17179572.568000] vga16fb: mapped to 0xc00a0000
[17179572.664000] Console: switching to colour frame buffer device 80x25
[17179572.664000] fb0: VGA16 VGA frame buffer device
[17179573.764000] Capability LSM initialized
[17179574.168000] SCSI subsystem initialized
[17179574.168000] ACPI: bus type scsi registered
[17179574.168000] libata version 1.20 loaded.
[17179574.168000] ahci 0000:00:1f.2: version 1.2
[17179574.168000] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 209
[17179581.604000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179581.604000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[17179581.604000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part coal enc
[17179581.604000] ata1: SATA max UDMA/133 cmd 0xF8868100 ctl 0x0 bmdma 0x0 irq 217
[17179581.604000] ata2: SATA max UDMA/133 cmd 0xF8868180 ctl 0x0 bmdma 0x0 irq 217
[17179581.604000] ata3: SATA max UDMA/133 cmd 0xF8868200 ctl 0x0 bmdma 0x0 irq 217
[17179581.604000] ata4: SATA max UDMA/133 cmd 0xF8868280 ctl 0x0 bmdma 0x0 irq 217
[17179581.604000] ata5: SATA max UDMA/133 cmd 0xF8868300 ctl 0x0 bmdma 0x0 irq 217
[17179581.604000] ata6: SATA max UDMA/133 cmd 0xF8868380 ctl 0x0 bmdma 0x0 irq 217
[17179581.808000] ata1: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f61 84:4023 85:7469 86:3e41 87:4023 88:407f 93:0000
[17179581.808000] ata1: dev 0 ATA-7, max UDMA/133, 488281250 sectors: LBA48
[17179581.904000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0x00000000[17179581.904000] ata1: dev 0 configured for UDMA/133
[17179582.000000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0x00000000[17179582.000000] scsi0 : ahci
[17179582.364000] ata2: dev 0 cfg 00:85c0 49:0f00 82:0000 83:4000 84:4000 85:0000 86:0000 87:4000 88:0407 93:0000
[17179582.364000] ata2: dev 0 ATAPI, max UDMA/33
[17179582.460000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0x00000000[17179582.464000] ata2: dev 0 configured for UDMA/33
[17179582.560000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0x00000000[17179582.560000] scsi1 : ahci
[17179582.764000] ata3: no device found (phy stat 00000000)
[17179582.764000] scsi2 : ahci
[17179582.968000] ata4: no device found (phy stat 00000000)
[17179582.968000] scsi3 : ahci
[17179583.172000] ata5: no device found (phy stat 00000004)
[17179583.172000] scsi4 : ahci
[17179583.376000] ata6: no device found (phy stat 00000004)
[17179583.376000] scsi5 : ahci
[17179583.376000]   Vendor: ATA       Model: WDC WD2500JS-75N  Rev: 10.0
[17179583.376000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179583.376000]   Vendor: TSSTcorp  Model: DVD+-RW TS-H653A  Rev: D300
[17179583.376000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179583.380000] Driver 'sd' needs updating - please use bus_type methods
[17179583.384000] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[17179583.384000] SCSI device sda: drive cache: write back
[17179583.388000] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[17179583.388000] SCSI device sda: drive cache: write back
[17179583.388000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[17179583.440000] sd 0:0:0:0: Attached scsi disk sda
[17179583.444000] ata2: translated ATA stat/err 0x51/60 to SCSI SK/ASC/ASCQ 0x3/11/04
[17179583.456000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[17179583.456000] Uniform CD-ROM driver Revision: 3.20
[17179583.456000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179583.468000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.468000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.468000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.468000] sr 1:0:0:0: SCSI error: return code = 0x8000002
[17179583.468000] sr0: Current [descriptor]: sense key: Aborted Command
[17179583.468000]     Additional sense: No additional sense information
[17179583.468000] Descriptor sense data with sense descriptors (in hex):
[17179583.468000]         72 0b 00 00 00 00 00 0e 09 0e 00 54 00 03 00 00
[17179583.468000]         00 00 00 00 a0 51
[17179583.468000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.468000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.468000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.468000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[17179583.468000]    : Current [descriptor]: sense key: Aborted Command
[17179583.468000]     Additional sense: No additional sense information
[17179583.472000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.472000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.472000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.472000] sr 1:0:0:0: SCSI error: return code = 0x8000002
[17179583.472000] sr0: Current [descriptor]: sense key: Aborted Command
[17179583.472000]     Additional sense: No additional sense information
[17179583.472000] Descriptor sense data with sense descriptors (in hex):
[17179583.472000]         72 0b 00 00 00 00 00 0e 09 0e 00 54 00 03 00 00
[17179583.472000]         00 00 00 00 a0 51
[17179583.472000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.472000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.472000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179583.472000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[17179583.472000]    : Current [descriptor]: sense key: Aborted Command
[17179583.472000]     Additional sense: No additional sense information
[17179584.036000] usbcore: registered new driver usbfs
[17179584.036000] usbcore: registered new driver hub
[17179584.040000] USB Universal Host Controller Interface driver v2.3
[17179584.040000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179584.040000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[17179584.040000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[17179584.040000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[17179584.040000] uhci_hcd 0000:00:1a.0: irq 169, io base 0x0000ff20
[17179584.040000] hub 1-0:1.0: USB hub found
[17179584.040000] hub 1-0:1.0: 2 ports detected
[17179584.144000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 225
[17179584.144000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[17179584.144000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[17179584.144000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[17179584.144000] uhci_hcd 0000:00:1a.1: irq 225, io base 0x0000ff00
[17179584.144000] hub 2-0:1.0: USB hub found
[17179584.144000] hub 2-0:1.0: 2 ports detected
[17179584.248000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179584.248000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179584.248000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179584.248000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[17179584.248000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x0000ff80
[17179584.248000] hub 3-0:1.0: USB hub found
[17179584.248000] hub 3-0:1.0: 2 ports detected
[17179584.248000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 50
[17179584.248000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[17179584.248000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[17179584.248000] ehci_hcd 0000:00:1a.7: debug port 1
[17179584.248000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[17179584.352000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 225
[17179584.352000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179584.352000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179584.352000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[17179584.352000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x0000ff60
[17179584.352000] hub 4-0:1.0: USB hub found
[17179584.352000] hub 4-0:1.0: 2 ports detected
[17179584.384000] usb 1-1: new low speed USB device using uhci_hcd and address 2[17179584.456000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 58
[17179584.456000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179584.456000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179584.456000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[17179584.456000] uhci_hcd 0000:00:1d.2: irq 58, io base 0x0000ff40
[17179584.456000] hub 5-0:1.0: USB hub found
[17179584.456000] hub 5-0:1.0: 2 ports detected
[17179584.560000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[17179584.560000] ehci_hcd 0000:00:1a.7: irq 50, io mem 0xdffdac00
[17179584.564000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179584.564000] hub 6-0:1.0: USB hub found
[17179584.564000] hub 6-0:1.0: 4 ports detected
[17179584.668000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179584.668000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179584.668000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179584.668000] ehci_hcd 0000:00:1d.7: debug port 1
[17179584.668000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179584.668000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[17179584.668000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xff980800
[17179584.672000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179584.716000] usb 1-1: USB disconnect, address 2
[17179584.716000] usbcore: registered new driver hiddev
[17179584.716000] hub 7-0:1.0: USB hub found
[17179584.716000] hub 7-0:1.0: 6 ports detected
[17179584.844000] usbcore: registered new driver usbhid
[17179584.844000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179584.848000] Probing IDE interface ide0...
[17179585.412000] Probing IDE interface ide1...
[17179585.708000] usb 6-3: new high speed USB device using ehci_hcd and address 4
[17179585.840000] usb 6-3: configuration #1 chosen from 2 choices
[17179585.848000] Initializing USB Mass Storage driver...
[17179586.024000] scsi6 : SCSI emulation for USB Mass Storage devices
[17179586.024000] usb-storage: device found at 4
[17179586.024000] usb-storage: waiting for device to settle before scanning
[17179586.024000] usbcore: registered new driver usb-storage
[17179586.024000] USB Mass Storage support registered.
[17179586.068000] Attempting manual resume
[17179586.104000] EXT3-fs: mounted filesystem with ordered data mode.
[17179586.120000] kjournald starting.  Commit interval 5 seconds
[17179586.264000] usb 1-1: new low speed USB device using uhci_hcd and address 3[17179586.452000] input: DELL DELL USB Keyboard as /class/input/input0
[17179586.452000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1a.0-1
[17179586.692000] usb 1-2: new low speed USB device using uhci_hcd and address 4[17179586.872000] input: USB Optical Mouse as /class/input/input1
[17179586.872000] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.0-2
[17179587.112000] usb 5-2: new full speed USB device using uhci_hcd and address 2
[17179591.024000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17179591.024000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179591.024000] SCSI device sdb: 3999743 512-byte hdwr sectors (2048 MB)
[17179591.024000] sdb: Write Protect is off
[17179591.024000] sdb: Mode Sense: 68 00 00 08
[17179591.024000] sdb: assuming drive cache: write through
[17179591.028000] SCSI device sdb: 3999743 512-byte hdwr sectors (2048 MB)
[17179591.028000] sdb: Write Protect is off
[17179591.028000] sdb: Mode Sense: 68 00 00 08
[17179591.028000] sdb: assuming drive cache: write through
[17179591.028000]  sdb: sdb1 sdb2
[17179591.032000] sd 6:0:0:0: Attached scsi removable disk sdb
[17179591.032000] usb-storage: device scan complete
[17179592.136000] ts: Compaq touchscreen protocol output
[17179592.152000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.152000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.152000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.152000] sr 1:0:0:0: SCSI error: return code = 0x8000002
[17179592.152000] sr0: Current [descriptor]: sense key: Aborted Command
[17179592.152000]     Additional sense: No additional sense information
[17179592.152000] Descriptor sense data with sense descriptors (in hex):
[17179592.152000]         72 0b 00 00 00 00 00 0e 09 0e 00 54 00 03 00 00
[17179592.152000]         00 00 00 00 a0 51
[17179592.216000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179592.216000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179592.216000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[17179592.972000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.972000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.972000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.976000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[17179592.976000]    : Current [descriptor]: sense key: Aborted Command
[17179592.976000]     Additional sense: No additional sense information
[17179592.976000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.976000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.976000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.976000] sr 1:0:0:0: SCSI error: return code = 0x8000002
[17179592.976000] sr0: Current [descriptor]: sense key: Aborted Command
[17179592.976000]     Additional sense: No additional sense information
[17179592.976000] Descriptor sense data with sense descriptors (in hex):
[17179592.976000]         72 0b 00 00 00 00 00 0e 09 0e 00 54 00 03 00 00
[17179592.976000]         00 00 00 00 a0 51
[17179592.976000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.976000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.976000] ata2: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/00/00
[17179592.976000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[17179592.976000]    : Current [descriptor]: sense key: Aborted Command
[17179592.976000]     Additional sense: No additional sense information
[17179593.232000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.252000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.812000] hw_random hardware driver 1.0.0 loaded
[17179593.968000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179593.968000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179594.140000] Real Time Clock Driver v1.12
[17179594.188000] input: PC Speaker as /class/input/input2
[17179599.392000] lp: driver loaded but no devices found
[17179599.428000] Adding 2538228k swap on /dev/sda5.  Priority:-1 extents:1 across:2538228k
[17179599.532000] EXT3 FS on sda3, internal journal
[17179599.640000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179599.640000] md: bitmap version 4.39
[17179600.036000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179605.580000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179605.608000] NTFS volume version 3.1.
[17179607.136000] NET: Registered protocol family 17
[17179612.072000] ACPI: Power Button (FF) [PWRF]
[17179612.072000] ACPI: Power Button (CM) [VBTN]
[17179612.260000] ibm_acpi: ec object not found
[17179612.288000] pcc_acpi: loading...
[17179615.684000] ppdev: user-space parallel port driver
[17179615.924000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179615.924000] apm: overridden by ACPI.
[17179619.736000] Bluetooth: Core ver 2.8
[17179619.736000] NET: Registered protocol family 31
[17179619.736000] Bluetooth: HCI device and connection manager initialized
[17179619.736000] Bluetooth: HCI socket layer initialized
[17179619.764000] Bluetooth: L2CAP ver 2.8
[17179619.764000] Bluetooth: L2CAP socket layer initialized
[17179619.772000] Bluetooth: RFCOMM socket layer initialized
[17179619.772000] Bluetooth: RFCOMM TTY layer initialized
[17179619.772000] Bluetooth: RFCOMM ver 1.7
[17179626.888000] NET: Registered protocol family 10
[17179626.888000] lo: Disabled Privacy Extensions
[17179626.888000] IPv6 over IPv4 tunneling driver
[17179628.760000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179628.760000] ISOFS: changing to secondary root
[17179628.860000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

### Post by jso2897 on 2007-09-06
> **PeterF said:**
> If the live-CD had Internet connection it should work now.
In your screen-shots I can't see the Network manager, check in Synaptic if it's installed
(network-manager and network-manager-gnome).
The network manager works best if no manual configuration is done, to check launch the terminal and type:

```
sudo gedit /etc/network/interfaces
```

the file should only contain the description for the loopback interface

```
auto lo
iface lo inet loopback
```

if there are more lines for eth0 or others remove those. Then reboot your system and the network icon should appear next to the clock, here you can connect to your wired network (if not already connected).
 
Dude! I'm not really part of this thread, but you solved MY problem. I just upgraded an old box from Xubuntu to Ubuntu Fiesty, and couldn't connect - but that little edit fixed it!
 THe Ubuntu forums - is there ANYTHING they can't do?:KS

---

### Post by uposer111 on 2007-09-07
I went ahead and tried that, and when it opened up the document, the page was blank. then i tried to add this ```
auto lo
iface lo inet loopback
``` into the document but it wouldnt save, it said the document did not exist.

Jeff

---

### Post by chilisastry on 2007-09-07
I have exactly this problem as well.  When I enhter [www.yahoo.com](www.yahoo.com) in the Firefox browser, it cannot find the serve.  But if I enter the IP address 209.131.36.158, the correct yahoo page is loaded.

The network card is configured using DHCP - the DNS settings are correct.

---

### Post by noob12 on 2007-09-07
uposer111:  You have a different problem.  You have no driver associated with your ethernet device.  The UNCLAIMED in the output of **sudo lshw -C network** means that there is no associated driver yet.  We need to determine why.

Your dmesg output was incomplete, but we may get a clue if you can run these and post the output.
```

uname -r

sudo modprobe -r e1000
sudo modprobe -v e1000 debug=16

tail -25 /var/log/kern.log

```

---

### Post by uposer111 on 2007-09-07
Ok here is what happened.

uname -r
```
2.6.15-26-386

```
sudo modprobe -r e1000, nothing happens.


sudo modprobe -v e1000 debug=16```
insmod /lib/modules/2.6.15-26-386/kernel/drivers/net/e1000/e1000.ko debug=16

```

tail -25 /var/log/kern.log```


Sep  7 02:03:35 localhost kernel: [17179604.760000] NTFS volume version 3.1.
Sep  7 02:03:35 localhost kernel: [17179606.296000] NET: Registered protocol family 17
Sep  7 02:03:35 localhost kernel: [17179611.256000] ACPI: Power Button (FF) [PWRF]
Sep  7 02:03:35 localhost kernel: [17179611.256000] ACPI: Power Button (CM) [VBTN]
Sep  7 02:03:35 localhost kernel: [17179611.444000] ibm_acpi: ec object not found
Sep  7 02:03:35 localhost kernel: [17179611.472000] pcc_acpi: loading...
Sep  7 02:03:37 localhost kernel: [17179614.940000] ppdev: user-space parallel port driver
Sep  7 02:03:37 localhost kernel: [17179615.168000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Sep  7 02:03:37 localhost kernel: [17179615.168000] apm: overridden by ACPI.
Sep  7 02:03:41 localhost kernel: [17179618.880000] Bluetooth: Core ver 2.8
Sep  7 02:03:41 localhost kernel: [17179618.880000] NET: Registered protocol family 31
Sep  7 02:03:41 localhost kernel: [17179618.880000] Bluetooth: HCI device and connection manager initialized
Sep  7 02:03:41 localhost kernel: [17179618.880000] Bluetooth: HCI socket layer initialized
Sep  7 02:03:41 localhost kernel: [17179618.920000] Bluetooth: L2CAP ver 2.8
Sep  7 02:03:41 localhost kernel: [17179618.920000] Bluetooth: L2CAP socket layer initialized
Sep  7 02:03:41 localhost kernel: [17179618.928000] Bluetooth: RFCOMM socket layer initialized
Sep  7 02:03:41 localhost kernel: [17179618.928000] Bluetooth: RFCOMM TTY layer initialized
Sep  7 02:03:41 localhost kernel: [17179618.928000] Bluetooth: RFCOMM ver 1.7
Sep  7 02:03:51 localhost kernel: [17179628.896000] NET: Registered protocol family 10
Sep  7 02:03:51 localhost kernel: [17179628.896000] lo: Disabled Privacy Extensions
Sep  7 02:03:51 localhost kernel: [17179628.896000] IPv6 over IPv4 tunneling driver
Sep  7 02:03:53 localhost kernel: [17179631.108000] ISO 9660 Extensions: Microsoft Joliet Level 3
Sep  7 02:03:53 localhost kernel: [17179631.112000] ISOFS: changing to secondary root
Sep  7 02:06:34 localhost kernel: [17179791.932000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
Sep  7 02:06:34 localhost kernel: [17179791.932000] Copyright (c) 1999-2005 Intel Corporation.


```


Thanks,
Jeff

---

### Post by uposer111 on 2007-09-07
bump

---

### Post by noob12 on 2007-09-07
You're running an older kernel.  Things may improve by upgrading.

Looks like after you did the explicit loading (the second modprobe)  that the driver didn't complain.  Can you repeat the sequence of modprobe commands  and then examine the output of **sudo lshw -C network** to see if the device is no longer UNCLAIMED.  If the driver has claimed it we're mostly there.

**UPDATE:**  Based on a net search it looks like the mapping for this device to the driver may have been introduced in a later kernel or driver version.
I would recommend upgrading the kernel.  Current Feisty generic has  2.6.20-16-generic.

---

### Post by uposer111 on 2007-09-07
I re entered in what you said, and here is what i got
```
uname -r
2.6.15-26-386

sudo modprobe -r e1000
nothing happens

sudo modprobe -v e1000 debug=16
insmod /lib/modules/2.6.15-26-386/kernel/drivers/net/e1000/e1000.ko debug=16

---------------------------------------
tail -25 /var/log/kern.log
Sep  7 05:43:52 localhost kernel: [17179821.616000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for error 0x20
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for status: 0x51
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for error 0x20
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for status: 0x51
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for error 0x20
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for status: 0x51
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Sep  7 05:43:52 localhost kernel: [17179821.620000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
Sep  7 05:43:52 localhost kernel: [17179821.620000] sr: Current [descriptor]: sense key: Medium Error
Sep  7 05:43:52 localhost kernel: [17179821.620000]     Additional sense: Unrecovered read error - auto reallocate failed
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for error 0x20
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for status: 0x51
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for error 0x20
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for status: 0x51
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for error 0x20
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: no sense translation for status: 0x51
Sep  7 05:43:52 localhost kernel: [17179821.620000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Sep  7 05:43:52 localhost kernel: [17179821.620000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
Sep  7 05:43:52 localhost kernel: [17179821.620000]    : Current [descriptor]: sense key: Medium Error
Sep  7 05:43:52 localhost kernel: [17179821.620000]     Additional sense: Unrecovered read error - auto reallocate failed
---------------------------
sudo lshw -C network
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:dffe0000-dfffffff iomemory:dffdb000-dffdbfff ioport:ecc0-ecdf irq:10



```

Looks like its still unclaimed :(

---

### Post by noob12 on 2007-09-07
You might have missed my update in my last post.  I suggest you upgrade your kernel to the latest Feisty kernel if possible.  I think things will just work if you do.  The mapping for your device for the e1000 driver seems to have been added at some point in the 2.6.18 kernel versions.  I'm on 2.6.20-16-generic and find that the mapping is there.  You are on 2.6.15.

---

### Post by uposer111 on 2007-09-07
Oh sorry, How would i go about doing that? I cant connect to the net when using ubuntu, is there a later version of the live cd that i used?


Jeff

---

### Post by noob12 on 2007-09-07
The LiveCD for Ubuntu 7.04 ("Feisty Fawn") (the latest stable released version) has kernel version 2.6.20-15 on it, which should work for you, and once you have the network running you will get an auto-upgrade to 2.6.20-16.  It sounds like you used 6.06 ("Dapper Drake").

I don't have other suggestions but someone else on the forum might.

---

### Post by uposer111 on 2007-09-07
Hey even though i didnt get my internet to work yet, you still put the time into trying to help me out. Thanks man

Jeff

---

### Post by uposer111 on 2007-09-07
Solved thanks to Noob12 I had a old version of Ubuntu, even though my friend said it was the latest.

Thanks for your time.

Jeff

---

### Post by chilisastry on 2007-09-08
I am using Feisty Fawn (7.04), but cannot access the Internet, except when I use IP addresses.  Not even with the Live CD.

The DNS settings are correct, and the routes look OK, so I have to assume that DNS lookup is not working correctly.

---

