---
title: "cant compile drivers for atheros ar8151"
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by the-technomancer on 2019-02-03
after a lot of searching, I found them. so after downloading and uncompressing them, I open the read me the file and I follow the instructions.
[ATTACH=CONFIG]282396[/ATTACH]
I got some other errors before but i managed to fix them and now I get this. i can't fix it I've been googling for hours.

[ATTACH=CONFIG]282397[/ATTACH]

```
georgevaio@Georgevaio:~/Downloads/ethernet/2666793-AR81Family-linux-v1.0.1.14$ cd src/georgevaio@Georgevaio:~/Downloads/ethernet/2666793-AR81Family-linux-v1.0.1.14/src$ make install
gcc: error: /lib/modules/4.18.0-13-generic/build/include/linux/utsrelease.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
Makefile:173: *** *** Aborting the build. *** This driver is not supported on kernel versions older than 2.4.0.  Stop.
georgevaio@Georgevaio:~/Downloads/ethernet/2666793-AR81Family-linux-v1.0.1.14/src$ sudo make install
[sudo] password for georgevaio: 
gcc: error: /lib/modules/4.18.0-13-generic/build/include/linux/utsrelease.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
Makefile:173: *** *** Aborting the build. *** This driver is not supported on kernel versions older than 2.4.0.  Stop.
```

---

### Post by howefield on 2019-02-03
Thread moved to the "*Networking & Wireless*" forum.

The text in your image is difficult to read, much better to copy/paste the text in to your posting and place between code tags.

---

### Post by the-technomancer on 2019-02-03
done

---

### Post by praseodym on 2019-02-03
As the output reads: That driver is outdated. Please show
```

lspci -nnk
```

---

### Post by the-technomancer on 2019-02-05
```

georgevaio@Georgevaio:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
Subsystem: Sony Corporation Core Processor DRAM Controller [104d:9071]
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
Kernel driver in use: pcieport
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
Subsystem: Sony Corporation 5 Series/3400 Series Chipset HECI Controller [104d:9071]
Kernel driver in use: mei_me
Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
Subsystem: Sony Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [104d:9071]
Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
Subsystem: Sony Corporation 5 Series/3400 Series Chipset High Definition Audio [104d:9071]
Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
Subsystem: Sony Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [104d:9071]
Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation HM55 Chipset LPC Interface Controller [8086:3b09] (rev 05)
Subsystem: Sony Corporation HM55 Chipset LPC Interface Controller [104d:9071]
Kernel driver in use: lpc_ich
Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
Subsystem: Sony Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [104d:9071]
Kernel driver in use: ahci
Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
Subsystem: Sony Corporation 5 Series/3400 Series Chipset SMBus Controller [104d:9071]
Kernel driver in use: i801_smbus
Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
Subsystem: Sony Corporation 5 Series/3400 Series Chipset Thermal Subsystem [104d:9071]
Kernel driver in use: intel ips
Kernel modules: intel_ips
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1]
Subsystem: Sony Corporation Mobility Radeon HD 5650 [104d:9071]
Kernel driver in use: radeon
Kernel modules: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series] [1002:aa60]
Subsystem: Sony Corporation Redwood HDMI Audio [Radeon HD 5000 Series] [104d:9071]
Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
Kernel driver in use: ath9k
Kernel modules: ath9k
03:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
Subsystem: Sony Corporation MMC/SD Host Controller [104d:9071]
Kernel driver in use: sdhci-pci
Kernel modules: sdhci_pci
03:00.1 System peripheral [0880]: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [1180:e230]
Subsystem: Sony Corporation R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [104d:9071]
03:00.4 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
Subsystem: Sony Corporation MMC/SD Host Controller [104d:9071]
Kernel driver in use: sdhci-pci
Kernel modules: sdhci_pci
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
Subsystem: Sony Corporation Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [104d:9071]
Kernel driver in use: sky2
Kernel modules: sky2
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
Subsystem: Sony Corporation Core Processor QuickPath Architecture Generic Non-core Registers [104d:9071]
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
Subsystem: Sony Corporation Core Processor QuickPath Architecture System Address Decoder [104d:9071]
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
Subsystem: Sony Corporation Core Processor QPI Link 0 [104d:9071]
3f:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:2d11] (rev 02)
Subsystem: Sony Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [104d:9071]
3f:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d12] (rev 02)
Subsystem: Sony Corporation 1st Generation Core i3/5/7 Processor Reserved [104d:9071]
3f:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d13] (rev 02)
Subsystem: Sony Corporation 1st Generation Core i3/5/7 Processor Reserved [104d:9071]

```

---

### Post by chili555 on 2019-02-05
As far as I know, AR8151 is an ethernet driver. Your ethernet device is this and it has a driver:> 
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
Subsystem: Sony Corporation Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [104d:9071]
[COLOR="#FF0000"]Kernel driver in use: sky2[/COLOR]
Kernel modules: sky2Please clarify your intentions.

Is your not-an-Atheros ethernet not working roperly?

---

### Post by jeremy31 on 2019-02-05
The only Atheros device is wifi and it also shows a loaded driver
```
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
Kernel driver in use: ath9k
Kernel modules: ath9k
```

The AR8151 also has a working driver in Ubuntu, atl1c

---

### Post by the-technomancer on 2019-02-06
the wifi works just fine but wired ethernet doesn't work
I found the name of the controller and searched the forum. found other threads and the driver for the controller but i am stuck in the installation

---

### Post by chili555 on 2019-02-06
Your ethernet has a driver. There is no way nor no need to install an old, obsolete driver.

Let's check the logs to see if we can see waht's wrong. Please run and post:```
dmesg | grep -e en -e sky
```

---

### Post by the-technomancer on 2019-02-07
this is the output
```

georgevaio@Georgevaio:~$ dmesg | grep -e en -e sky
[    0.000000] Linux version 4.18.0-13-generic (buildd@lgw01-amd64-048) (gcc version 8.2.0 (Ubuntu 8.2.0-7ubuntu1)) #14-Ubuntu SMP Wed Dec 5 09:04:24 UTC 2018 (Ubuntu 4.18.0-13.14-generic 4.18.17)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-13-generic root=UUID=f6cff3fb-a49e-4151-8332-96a720301edb ro quiet splash vt.handoff=1
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] SMBIOS 2.6 present.
[    0.000000] MTRR fixed ranges enabled:
[    0.000000] MTRR variable ranges enabled:
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-13-generic root=UUID=f6cff3fb-a49e-4151-8332-96a720301edb ro quiet splash vt.handoff=1
[    0.000000] Kernel/User page tables isolation: enabled
[    0.000000] ftrace: allocating 40813 entries in 160 pages
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Tasks RCU enabled.
[    0.000000] vt handoff: transparent VT on vt#1
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.024000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4521.99 BogoMIPS (lpj=9043988)
[    0.028405] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.028880] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.028908] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.028924] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.029271] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.029272] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.029275] Spectre V2 : Mitigation: Full generic retpoline
[    0.036000] Performance Events: PEBS fmt1+, Westmere events, 16-deep LBR, Intel PMU driver.
[    0.036000] core: CPUID marked event: 'bus cycles' unavailable
[    0.036000] ... generic registers:      4
[    0.036000] ... fixed-purpose events:   3
[    0.036000] ... event mask:             000000070000000f
[    0.036000] Hierarchical SRCU implementation.
[    0.036000] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.044530] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.044530] audit: type=2000 audit(1549530759.044:1): state=initialized audit_enabled=0 res=1
[    0.044530] cpuidle: using governor menu
[    0.044530] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.048101] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.048104] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.500180] ACPI: Interpreter enabled
[    0.511626] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.516003] pci 0000:01:00.0: enabling Extended Tags
[    0.516187] pci 0000:01:00.1: enabling Extended Tags
[    0.516877] pci 0000:03:00.0: MMC controller base frequency changed to 50Mhz.
[    0.520608] pci_bus 0000:0d: extended config space not accessible
[    0.522083] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.552968] ACPI: EC: event unblocked
[    0.552994] ACPI: \_SB_.PCI0.LPCB.EC__: Used as boot DSDT EC to handle transactions and events
[    0.570706] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.571133] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.571136] system 00:00: [io  0xff00-0xff0f] has been reserved
[    0.571138] system 00:00: [io  0xff10-0xff13] has been reserved
[    0.571140] system 00:00: [io  0x0800-0x0803] has been reserved
[    0.571141] system 00:00: [io  0x0400-0x047f] has been reserved
[    0.571143] system 00:00: [io  0x0500-0x057f] has been reserved
[    0.571145] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.571794] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.571796] system 00:04: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.571798] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.571800] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.571802] system 00:04: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.571804] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.571805] system 00:04: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.571811] system 00:04: [mem 0xf7fff000-0xf7ffffff] has been reserved
[    0.610540] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes)
[    0.610567] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.610670] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.610879] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.610910] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    5.233256] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 244)
[    5.234455] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    5.377192] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    5.384396] PPP generic driver version 2.4.2
[    5.404226] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.18
[    5.404235] usb usb1: Manufacturer: Linux 4.18.0-13-generic ehci_hcd
[    5.424181] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.18
[    5.424190] usb usb2: Manufacturer: Linux 4.18.0-13-generic ehci_hcd
[    5.424724] ehci-platform: EHCI generic platform driver
[    5.424744] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.424765] ohci-platform: OHCI generic platform driver
[    5.431005] i2c /dev entries driver
[    5.431152] device-mapper: uevent: version 1.0.3
[    5.441457] Segment Routing with IPv6
[    5.446234] Loaded X.509 cert 'Build time autogenerated kernel key: 0a4c8c749a456fd3db5c73dc83f83eab291d4463'
[    5.457849] Key type encrypted registered
[    5.457856] AppArmor: AppArmor sha1 policy hashing enabled
[    5.457907] evm: Initialising EVM extended attributes:
[    5.513996] ACPI: Battery Slot [BAT0] (battery present)
[    5.733329] sky2: driver version 1.30
[    5.733741] sky2 0000:04:00.0: Yukon-2 Optima chip revision 1
[    5.735194] sky2 0000:04:00.0 eth0: addr 54:42:49:07:97:c0
[    5.738176] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    5.738210] mmc0 bounce up to 128 segments into one, max segment size 65536 bytes
[    5.738765] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
[    5.738802] mmc1 bounce up to 128 segments into one, max segment size 65536 bytes
[    5.757477] sky2 0000:04:00.0 enp4s0: renamed from eth0
[    5.900640] usb 1-1: New USB device found, idVendor=8087, idProduct=0020, bcdDevice= 0.00
[    5.924490] usb 2-1: New USB device found, idVendor=8087, idProduct=0020, bcdDevice= 0.00
[    6.066854] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.066917] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.066953] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.329773] usb 1-1.2: New USB device found, idVendor=0c45, idProduct=6409, bcdDevice=9c.30
[    6.525263] usb 1-1.6: New USB device found, idVendor=0489, idProduct=e00f, bcdDevice= 5.96
[    6.805708] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   12.511679] systemd[1]: Listening on Journal Socket (/dev/log).
[   12.513087] systemd[1]: Listening on Journal Audit Socket.
[   12.513203] systemd[1]: Listening on Journal Socket.
[   12.530634] systemd[1]: Listening on Syslog Socket.
[   13.542277] Adding 2097148k swap on /swapfile.  Priority:-2 extents:6 across:2260988k FS
[   17.884221] audit: type=1400 audit(1549530777.921:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
[   17.884226] audit: type=1400 audit(1549530777.921:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
[   17.884233] audit: type=1400 audit(1549530777.921:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
[   19.341959] audit: type=1400 audit(1549530779.377:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=436 comm="apparmor_parser"
[   23.983252] [drm] radeon kernel modesetting enabled.
[   23.983357] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[   24.116540] ath: phy0: ASPM enabled: 0x42
[   24.398573] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[   24.722645] [drm] PCIE GART of 1024M enabled (table at 0x000000000014C000).
[   24.722789] radeon 0000:01:00.0: WB enabled
[   24.722793] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x0000000055df02c0
[   24.722796] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x00000000a96655fe
[   24.723208] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0x0000000028ea8418
[   26.938814] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   28.198278] uvcvideo 1-1.2:1.0: Entity type for entity Extension 5 was not initialized!
[   28.198280] uvcvideo 1-1.2:1.0: Entity type for entity Extension 4 was not initialized!
[   28.198282] uvcvideo 1-1.2:1.0: Entity type for entity Processing 3 was not initialized!
[   28.198283] uvcvideo 1-1.2:1.0: Entity type for entity Camera 1 was not initialized!
[   42.121606] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   42.124959] sky2 0000:04:00.0 enp4s0: enabling interface
[   42.125583] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   44.631341] wlp2s0: authenticate with 56:d9:e7:45:fc:fc
[   44.644910] wlp2s0: send auth to 56:d9:e7:45:fc:fc (try 1/3)
[   44.648327] wlp2s0: authenticated
[  184.190965] usb 2-1.6: New USB device found, idVendor=046d, idProduct=c045, bcdDevice=27.30
[  184.241637] hidraw: raw HID events driver (C) Jiri Kosina
[  184.344302] hid-generic 0003:046D:C045.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1.6/input0
[  338.649993] wlp2s0: authenticate with 56:d9:e7:47:4e:09
[  338.663497] wlp2s0: send auth to 56:d9:e7:47:4e:09 (try 1/3)
[  338.711134] wlp2s0: send auth to 56:d9:e7:47:4e:09 (try 2/3)
[  338.815813] wlp2s0: send auth to 56:d9:e7:47:4e:09 (try 3/3)
[  338.819745] wlp2s0: authenticated
[  375.718597] wlp2s0: authenticate with 56:d9:e7:45:fc:fc
[  375.732301] wlp2s0: send auth to 56:d9:e7:45:fc:fc (try 1/3)
[  375.739010] wlp2s0: authenticated
[  386.461622] wlp2s0: authenticate with 56:d9:e7:45:fc:af
[  386.475147] wlp2s0: send auth to 56:d9:e7:45:fc:af (try 1/3)
[  386.479613] wlp2s0: authenticated
[  397.285754] wlp2s0: authenticate with 56:d9:e7:45:fc:fc
[  397.299735] wlp2s0: send auth to 56:d9:e7:45:fc:fc (try 1/3)
[  397.827800] wlp2s0: send auth to 56:d9:e7:45:fc:fc (try 2/3)
[  398.434410] wlp2s0: send auth to 56:d9:e7:45:fc:fc (try 3/3)
[  398.631247] wlp2s0: authenticated
[  424.443135] wlp2s0: authenticate with 56:d9:e7:47:4e:09
[  424.461286] wlp2s0: send auth to 56:d9:e7:47:4e:09 (try 1/3)
[  424.518596] wlp2s0: authenticated
[  425.367085] wlp2s0: authenticate with 56:d9:e7:45:fc:af
[  425.384101] wlp2s0: send auth to 56:d9:e7:45:fc:af (try 1/3)
[  425.387595] wlp2s0: authenticated
[  482.470890] audit: type=1400 audit(1549531241.349:41): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/georgevaio/.cache/mesa_shader_cache/index" pid=3925 comm="soffice.bin" requested_mask="wrc" denied_mask="wrc" fsuid=1000 ouid=1000



```

---

### Post by chili555 on 2019-02-07
In your logs, we see:

> [    5.733329] sky2: driver version 1.30
[    5.733741] sky2 0000:04:00.0: Yukon-2 Optima chip revision 1
[    5.735194] sky2 0000:04:00.0 eth0: addr 54:42:49:07:97:c0
[    5.757477] sky2 0000:04:00.0 enp4s0: renamed from eth0

....

[   42.121606] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   42.124959] sky2 0000:04:00.0 enp4s0: enabling interface
[   42.125583] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready

In other words, we see nothing at all wrong or alarming. We see no reason that your ethernet shouldn't work perfectly well.

Please use the airplane mode switch to disable the wireless temporarily and confirm that you have a known working ethernet cable attached to the computer and a known working port on the router or switch.

Does Network Manager see a wired connection when you click the icon at the top right?

[IMG]http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2012/05/u2.jpg[/IMG]

Does it attempt to connect?

Let's have a look at:

```
dmesg | grep enp4s0
```

---

### Post by the-technomancer on 2019-02-12
sorry for the late reply.  it logged me out for some reason so no notifications and when i refreshed i didn't notice the 2nd page.

if i enable aeroplane mode i see my ethernet card with if config now but it doesn't have an ip. and now i don't see it on the top bar. 
```

georgevaio@Georgevaio:~$ ifconfig
enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:42:49:07:97:c0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 651  bytes 56109 (56.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 651  bytes 56109 (56.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


georgevaio@Georgevaio:~$ dmesg | grep enp4s0
[    5.778228] sky2 0000:04:00.0 enp4s0: renamed from eth0
[   44.568762] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   44.572103] sky2 0000:04:00.0 enp4s0: enabling interface
[   44.572720] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
georgevaio@Georgevaio:~$ 



```

---

### Post by chili555 on 2019-02-12
Are there any interesting entries here?```
cat /etc/network/interfaces
```Or here?```
cat /etc/netplan/*.yaml
```Or here?```
cat /etc/NetworkManager/NetworkManager.conf
```And, finally, here?```
cat /var/log/syslog  | grep enp4s0 | tail -n20
```We still see no fault that shows why the ethernet doesn't work as expected.

---

### Post by jeremy31 on 2019-02-13
Does it work after sleep/suspend?

---

### Post by the-technomancer on 2019-02-14
here you go

```

georgevaio@Georgevaio:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
georgevaio@Georgevaio:~$ cat /etc/netplan/*.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
georgevaio@Georgevaio:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no
georgevaio@Georgevaio:~$ cat /var/log/syslog  | grep enp4s0 | tail -n20
Feb 14 11:13:54 Georgevaio NetworkManager[714]: <info>  [1550135634.8434] settings: (enp4s0): created default wired connection 'Wired connection 1'
Feb 14 11:13:54 Georgevaio NetworkManager[714]: <info>  [1550135634.8441] device (enp4s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Feb 14 11:13:54 Georgevaio kernel: [   41.798254] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
Feb 14 11:13:54 Georgevaio kernel: [   41.801545] sky2 0000:04:00.0 enp4s0: enabling interface
Feb 14 11:13:54 Georgevaio kernel: [   41.802170] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
Feb 14 18:30:00 Georgevaio kernel: [    5.780607] sky2 0000:04:00.0 enp4s0: renamed from eth0
Feb 14 18:30:05 Georgevaio NetworkManager[659]: <info>  [1550161805.0111] devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/enp4s0, iface: enp4s0)
Feb 14 18:30:05 Georgevaio NetworkManager[659]: <info>  [1550161805.0112] device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/enp4s0, iface: enp4s0): no ifupdown configuration found.
Feb 14 18:30:06 Georgevaio NetworkManager[659]: <info>  [1550161806.6905] manager: (enp4s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Feb 14 18:30:06 Georgevaio NetworkManager[659]: <info>  [1550161806.6933] settings: (enp4s0): created default wired connection 'Wired connection 1'
Feb 14 18:30:06 Georgevaio NetworkManager[659]: <info>  [1550161806.6941] device (enp4s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Feb 14 18:30:06 Georgevaio kernel: [   41.672882] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
Feb 14 18:30:06 Georgevaio kernel: [   41.676221] sky2 0000:04:00.0 enp4s0: enabling interface
Feb 14 18:30:06 Georgevaio kernel: [   41.676844] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
Feb 14 18:38:39 Georgevaio NetworkManager[659]: <info>  [1550162319.6431] device (enp4s0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Feb 14 18:38:39 Georgevaio kernel: [  555.372642] sky2 0000:04:00.0 enp4s0: disabling interface
Feb 14 18:48:37 Georgevaio kernel: [  564.812967] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
Feb 14 18:48:37 Georgevaio kernel: [  564.816371] sky2 0000:04:00.0 enp4s0: enabling interface
Feb 14 18:48:37 Georgevaio kernel: [  564.820183] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
Feb 14 18:48:37 Georgevaio NetworkManager[659]: <info>  [1550162917.7450] device (enp4s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'managed')



```

---

### Post by the-technomancer on 2019-02-14
> 
[COLOR=#000000]Does it work after sleep/suspend?[/COLOR]


no, it doesn't

---

### Post by chili555 on 2019-02-16
I am still unable to see a reason that the ethernet doesn't work. On the chance that Network Manager is at fault, let's try disabling it temporarily:```
sudo service network-manager stop
sudo dhclient enp4s0
```Are there any interesting messages, errors, warnings, etc.?

Restart NM with:```
sudo service network-manager start
```

---

### Post by the-technomancer on 2019-02-17
nothing

---

### Post by chili555 on 2019-02-17
> **the-technomancer said:**
> nothingAfter doing so, what does this report?```
cat /var/log/syslog | grep dhclient | tail -n10
```

---

### Post by the-technomancer on 2019-02-21
```

georgevaio@Georgevaio:~$ cat /var/log/syslog | grep dhclient | tail -n10
Feb 21 11:28:10 Georgevaio dhclient[1109]: bound to 172.16.1.79 -- renewal in 9154 seconds.
Feb 21 20:56:06 Georgevaio kernel: [   20.727894] audit: type=1400 audit(1550775340.775:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=455 comm="apparmor_parser"
Feb 21 20:56:06 Georgevaio kernel: [   20.727906] audit: type=1400 audit(1550775340.775:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
Feb 21 20:56:09 Georgevaio NetworkManager[952]: <info>  [1550775369.3159] dhcp-init: Using DHCP client 'dhclient'
Feb 21 20:56:12 Georgevaio NetworkManager[952]: <info>  [1550775372.8700] dhcp4 (wlp2s0): dhclient started with pid 1566
Feb 21 20:56:13 Georgevaio dhclient[1566]: DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0xa78f6b07)
Feb 21 20:56:13 Georgevaio dhclient[1566]: DHCPREQUEST of 192.168.0.24 on wlp2s0 to 255.255.255.255 port 67 (xid=0x76b8fa7)
Feb 21 20:56:13 Georgevaio dhclient[1566]: DHCPOFFER of 192.168.0.24 from 192.168.0.2
Feb 21 20:56:14 Georgevaio dhclient[1566]: DHCPACK of 192.168.0.24 from 192.168.0.2
Feb 21 20:56:15 Georgevaio dhclient[1566]: bound to 192.168.0.24 -- renewal in 1550 seconds.



```

---

### Post by chili555 on 2019-02-21
What we have here is a textbook perfect, oh so sweet example of a successful DHCP transaction for your wireless. It tells us nothing about the ethernet.

Please turn off the wireless with the airplane mode switch. Hook up a known working ethernet cable to the computer and the router. Next, run:```

sudo service network-manager stop
sudo dhclient enp4s0
cat /var/log/syslog | grep dhclient | tail -n10


```Let's see what the ethernet isn't doing as expected.

---

### Post by the-technomancer on 2019-02-23
thanks for the help so far

```

georgevaio@Georgevaio:~$ cat /var/log/syslog | grep dhclient | tail -n10
Feb 23 22:14:44 Georgevaio dhclient[6367]: bound to 192.168.0.24 -- renewal in 1766 seconds.
Feb 23 22:16:01 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 3 (xid=0x97791352)
Feb 23 22:16:04 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 6 (xid=0x97791352)
Feb 23 22:16:10 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 6 (xid=0x97791352)
Feb 23 22:16:16 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 9 (xid=0x97791352)
Feb 23 22:16:25 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 8 (xid=0x97791352)
Feb 23 22:16:33 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 8 (xid=0x97791352)
Feb 23 22:16:41 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 11 (xid=0x97791352)
Feb 23 22:16:52 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 17 (xid=0x97791352)
Feb 23 22:17:09 Georgevaio dhclient[6726]: DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 10 (xid=0x97791352)
georgevaio@Georgevaio:~$ 



```

---

### Post by the-technomancer on 2019-03-05
what can i do now?

---

### Post by chili555 on 2019-03-05
I'm sorry, but we see nothing wrong and therefore fixable. I can offer no explanation as to why the ethernet won't work perfectly.

If your wireless is working well, I'd just use it and compromise. Otherwise, I'd look into any number of alternative devices such as USB ethernet adapters.

I am confident that if Jeremy or the other networking gurus on this forum had any other suggestions, they would have pointed out anything I had overlooked. They are very good about that!

---

