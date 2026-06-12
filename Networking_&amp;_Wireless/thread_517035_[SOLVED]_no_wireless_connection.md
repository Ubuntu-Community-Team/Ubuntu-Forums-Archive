---
title: "[SOLVED] no wireless connection"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by maxi123 on 2007-08-04
i finally got my windows/ubuntu dual-boot going but i dont get any wireless connection on my ubuntu side... i dont even see the wireless light on.. i own a gateway MX 7525..

please help thanks

---

### Post by noob12 on 2007-08-04
Start by showing us precisely what you have.  Post the output to
```

lspci --n

lshw -C network

```

---

### Post by maxi123 on 2007-08-04
lspci: invalid option -- -
Usage: lspci [<switches>]
-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging





lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 10
       serial: 00:03:25:33:36:52
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 multicast=yes
       resources: iomemory:c0100000-c0103fff ioport:a000-a0ff irq:22
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@03:07.0
       logical name: eth0
       version: 02
       serial: 00:c0:a8:a9:e0:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0201fff irq:16

thanks for the reply

---

### Post by noob12 on 2007-08-04
Had meant to say **lspci -nn**, but I've got enough info from the lshw.

You have a BCM4318 [AirForce One 54g] 802.11g

I would suggest that you try to follow the instructions in this thread [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
Several users have been successful with that.

Also, it appears that the device might be disabled right now.  Check that the hardware switch is enabled and that you have set wireless to be enabled on startup in the BIOS.  Otherwise you may have trouble getting things working.

If you have problems, post back on this thread and I'll try to help you out.

---

### Post by maxi123 on 2007-08-04
im really new to this :P 

how do i make sure the hardware switch is on??

when i log on my windows the wireless light is on and it works just fine so im thinking its turned on...

would like to make sure though

thanks

---

### Post by noob12 on 2007-08-04
Usually if there is a switch it is a slider on the side of the laptop, or  FN + a specific F key.  

Your laptop should come with instructions for this and also for how to go into the BIOS setup.  It is usually by hitting DEL or an F key like F12 while the computer is just coming up.  Check settings there to make sure wireless is enabled by default on startup.

Can you post the output of ```
dmesg
```  and of the following command ```
cat /sys/class/net/*/driver/rf_kill
```.  One or both of these should tell us if the kill switch is on.

It could just be that the interface has to be brought up.  We'll try that in a minute.

---

### Post by maxi123 on 2007-08-04
i got this huge output with the first command... also i do have an FN key but when i try enabling the wireless it wont do anything (the litte wireless light doesnt go on)

[    5.496000] ide1 at 0x170-0x177,0x376 on irq 15

[    5.500000] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 23 (level, low) -> IRQ 20

[    5.552000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[c0203000-c02037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[    5.564000] SCSI subsystem initialized

[    5.568000] libata version 2.20 loaded.

[    5.572000] hda: max request size: 128KiB

[    5.580000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)

[    5.584000] hda: cache flushes supported

[    5.584000]  hda: hda1 hda2 hda3 hda4

[    5.668000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)

[    5.668000] Uniform CD-ROM driver Revision: 3.20

[    6.020000] Attempting manual resume

[    6.020000] swsusp: Resume From Partition 3:3

[    6.020000] PM: Checking swsusp image.

[    6.020000] PM: Resume from disk failed.

[    6.052000] kjournald starting.  Commit interval 5 seconds

[    6.052000] EXT3-fs: mounted filesystem with ordered data mode.

[    6.828000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00032521500171d2]

[   18.220000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   18.224000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   18.656000] ieee80211_crypt: registered algorithm 'NULL'

[   18.688000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device

[   18.752000] Yenta: CardBus bridge found at 0000:03:05.0 [107b:0506]

[   18.752000] Yenta: Using CSCINT to route CSC interrupts to PCI

[   18.752000] Yenta: Routing CardBus interrupts to PCI

[   18.752000] Yenta TI: socket 0000:03:05.0, mfunc 0x01001002, devctl 0x44

[   18.752000] ieee80211: 802.11 data/management/control stack, git-1.1.13

[   18.752000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

[   18.788000] Linux agpgart interface v0.102 (c) Dave Jones

[   18.828000] input: PC Speaker as /class/input/input2

[   18.860000] bcm43xx driver

[   18.996000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16

[   18.996000] Socket status: 30000006

[   18.996000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07

[   18.996000] pcmcia: parent PCI bridge I/O window: 0xb000 - 0xbfff

[   18.996000] cs: IO port probe 0xb000-0xbfff: clean.

[   18.996000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff

[   18.996000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff

[   19.000000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17

[   19.008000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 22

[   19.008000] PCI: Setting latency timer of device 0000:02:00.0 to 64

[   19.008000] sky2 0000:02:00.0: v1.13 addr 0xc0100000 irq 22 Yukon-FE (0xb7) rev 1

[   19.008000] sky2 eth0: addr 00:03:25:33:36:52

[   19.008000] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 22 (level, low) -> IRQ 16

[   19.024000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17

[   19.104000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[   19.116000] sky2 eth1: enabling interface

[   19.116000] sky2 eth1: ram buffer 4K

[   19.136000] MC'97 0 converters and GPIO not ready (0x1)

[   19.192000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[   19.196000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008

[   19.200000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[   19.236000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

[   19.332000] cs: IO port probe 0x100-0x3af: clean.

[   19.336000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7

[   19.336000] cs: IO port probe 0x820-0x8ff: clean.

[   19.336000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf

[   19.336000] cs: IO port probe 0xa00-0xaff: clean.

[   19.476000] fuse init (API version 7.8)

[   19.536000] lp: driver loaded but no devices found

[   19.576000] Adding 979956k swap on /dev/disk/by-uuid/6f4f0cb1-fd83-4f7a-ae06-58aa5a650996.  Priority:-1 extents:1 across:979956k

[   19.780000] EXT3 FS on hda4, internal journal

[   20.416000] NET: Registered protocol family 17

[   22.784000] NTFS driver 2.1.28 [Flags: R/O MODULE].

[   22.868000] NTFS volume version 3.1.

[   26.984000] No dock devices found.

[   27.064000] Using specific hotkey driver

[   27.116000] ACPI: Battery Slot [BAT0] (battery present)

[   27.128000] ACPI: AC Adapter [AC] (on-line)

[   27.184000] input: Power Button (FF) as /class/input/input4

[   27.188000] ACPI: Power Button (FF) [PWRF]

[   27.208000] input: Power Button (CM) as /class/input/input5

[   27.212000] ACPI: Power Button (CM) [PWRB]

[   27.236000] input: Sleep Button (CM) as /class/input/input6

[   27.240000] ACPI: Sleep Button (CM) [SLPB]

[   27.264000] input: Lid Switch as /class/input/input7

[   27.264000] ACPI: Lid Switch [LID]

[   27.284000] ibm_acpi: ec object not found

[   27.328000] pcc_acpi: loading...

[   27.520000] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 4000+ processors (version 2.00.00)

[   27.520000] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x8

[   27.520000] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xa

[   27.520000] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xc

[   27.520000] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xe

[   27.520000] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x10

[   27.520000] powernow-k8:    5 : fid 0x8 (1600 MHz), vid 0x12

[   27.520000] powernow-k8:    6 : fid 0x0 (800 MHz), vid 0x18

[   30.032000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[   30.748000] [drm] Initialized drm 1.1.0 20060810

[   30.764000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 22

[   30.764000] [drm] Initialized radeon 1.25.0 20060524 on minor 0

[   31.960000] ppdev: user-space parallel port driver

[   32.228000] [drm] Setting GART location based on new memory map

[   32.228000] [drm] Loading R300 Microcode

[   32.228000] [drm] writeback test succeeded in 1 usecs

[   32.844000] apm: BIOS not found.

[   32.988000] Bluetooth: Core ver 2.11

[   32.988000] NET: Registered protocol family 31

[   32.988000] Bluetooth: HCI device and connection manager initialized

[   32.988000] Bluetooth: HCI socket layer initialized

[   33.012000] Bluetooth: L2CAP ver 2.8

[   33.012000] Bluetooth: L2CAP socket layer initialized

[   33.148000] Bluetooth: RFCOMM socket layer initialized

[   33.148000] Bluetooth: RFCOMM TTY layer initialized

[   33.148000] Bluetooth: RFCOMM ver 1.8

[   34.228000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[   50.520000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[   51.116000] NET: Registered protocol family 10

[   51.116000] lo: Disabled Privacy Extensions

[   51.116000] ADDRCONF(NETDEV_UP): eth1: link is not ready

[   58.264000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[   82.832000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  106.076000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  129.320000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  152.556000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  275.796000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  399.036000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  414.296000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  522.276000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  645.532000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  768.776000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  892.016000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[  893.268000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1015.308000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1138.556000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1261.796000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1351.240000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1385.044000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1465.476000] APIC error on CPU0: 00(40)

[ 1475.996000] APIC error on CPU0: 40(40)

[ 1483.492000] APIC error on CPU0: 40(40)

[ 1507.328000] APIC error on CPU0: 40(40)

[ 1508.264000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1531.496000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1554.772000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1578.004000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1601.256000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1721.348000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1721.380000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1722.064000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1784.496000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1807.752000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1822.196000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1830.976000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1854.220000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 1977.456000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2054.176000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2100.688000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2223.936000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2278.164000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2347.176000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2470.412000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2593.720000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2698.144000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2717.188000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2840.440000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2930.128000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2963.684000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 2979.928000] APIC error on CPU0: 40(40)

[ 3044.724000] APIC error on CPU0: 40(40)

[ 3086.936000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3110.212000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3233.448000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3356.764000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3400.096000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3480.016000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3481.240000] APIC error on CPU0: 40(40)

[ 3503.404000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3513.672000] APIC error on CPU0: 40(40)

[ 3527.328000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3628.956000] APIC error on CPU0: 40(40)

[ 3650.664000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3661.048000] APIC error on CPU0: 40(40)

[ 3736.368000] APIC error on CPU0: 40(40)

[ 3757.056000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3774.016000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3897.264000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 3914.468000] APIC error on CPU0: 40(40)

[ 3936.124000] APIC error on CPU0: 40(40)

[ 4020.588000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4055.672000] APIC error on CPU0: 40(40)

[ 4094.524000] APIC error on CPU0: 40(40)

[ 4144.020000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4230.008000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4267.288000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4390.528000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4513.752000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4636.984000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4693.980000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4760.232000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 4883.472000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5006.736000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5035.960000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5130.044000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5253.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5314.944000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5376.504000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5499.744000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5622.996000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5646.236000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5646.552000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5649.540000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5649.664000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5694.952000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5714.532000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5737.764000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5760.980000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5769.040000] usb 3-3: new high speed USB device using ehci_hcd and address 2

[ 5769.172000] usb 3-3: configuration #1 chosen from 2 choices

[ 5769.528000] usbcore: registered new interface driver libusual

[ 5769.552000] Initializing USB Mass Storage driver...

[ 5769.552000] scsi0 : SCSI emulation for USB Mass Storage devices

[ 5769.552000] usbcore: registered new interface driver usb-storage

[ 5769.552000] USB Mass Storage support registered.

[ 5769.552000] usb-storage: device found at 2

[ 5769.552000] usb-storage: waiting for device to settle before scanning

[ 5774.552000] usb-storage: device scan complete

[ 5774.552000] scsi 0:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0

[ 5774.660000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)

[ 5774.660000] sda: Write Protect is off

[ 5774.660000] sda: Mode Sense: 68 00 00 08

[ 5774.660000] sda: assuming drive cache: write through

[ 5774.664000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)

[ 5774.664000] sda: Write Protect is off

[ 5774.664000] sda: Mode Sense: 68 00 00 08

[ 5774.664000] sda: assuming drive cache: write through

[ 5774.668000]  sda: sda1 sda2

[ 5774.672000] sd 0:0:0:0: Attached scsi removable disk sda

[ 5774.688000] sd 0:0:0:0: Attached scsi generic sg0 type 0

[ 5784.204000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5809.300000] APIC error on CPU0: 40(40)

[ 5884.772000] APIC error on CPU0: 40(40)

[ 5907.552000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 5991.540000] APIC error on CPU0: 40(40)

[ 6030.860000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6071.704000] usb 3-3: USB disconnect, address 2

[ 6119.864000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6154.200000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6242.904000] usb 3-4: new high speed USB device using ehci_hcd and address 3

[ 6243.036000] usb 3-4: configuration #1 chosen from 2 choices

[ 6243.040000] scsi1 : SCSI emulation for USB Mass Storage devices

[ 6243.040000] usb-storage: device found at 3

[ 6243.040000] usb-storage: waiting for device to settle before scanning

[ 6243.168000] usb 3-4: USB disconnect, address 3

[ 6260.780000] usb 3-4: new high speed USB device using ehci_hcd and address 4

[ 6260.932000] usb 3-4: configuration #1 chosen from 2 choices

[ 6260.932000] scsi2 : SCSI emulation for USB Mass Storage devices

[ 6260.932000] usb-storage: device found at 4

[ 6260.932000] usb-storage: waiting for device to settle before scanning

[ 6265.932000] usb-storage: device scan complete

[ 6265.932000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0

[ 6265.936000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)

[ 6265.936000] sda: Write Protect is off

[ 6265.936000] sda: Mode Sense: 68 00 00 08

[ 6265.936000] sda: assuming drive cache: write through

[ 6265.940000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)

[ 6265.940000] sda: Write Protect is off

[ 6265.940000] sda: Mode Sense: 68 00 00 08

[ 6265.940000] sda: assuming drive cache: write through

[ 6265.940000]  sda: sda1 sda2

[ 6265.944000] sd 2:0:0:0: Attached scsi removable disk sda

[ 6265.944000] sd 2:0:0:0: Attached scsi generic sg0 type 0

[ 6277.396000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6327.572000] usb 3-4: USB disconnect, address 4

[ 6400.944000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6446.808000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6471.172000] APIC error on CPU0: 40(40)

[ 6524.184000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6647.852000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6692.328000] APIC error on CPU0: 40(40)

[ 6771.064000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6847.780000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6885.208000] APIC error on CPU0: 40(40)

[ 6894.520000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 6931.660000] APIC error on CPU0: 40(40)

[ 7017.884000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7125.752000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7141.152000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7202.116000] APIC error on CPU0: 40(40)

[ 7264.472000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7387.820000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7440.724000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7511.076000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7634.320000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7654.712000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7711.504000] APIC error on CPU0: 40(40)

[ 7757.576000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7880.804000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 7925.692000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8004.188000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8042.180000] APIC error on CPU0: 40(40)

[ 8127.468000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8250.736000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8319.668000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8373.996000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8497.304000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8620.560000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8633.648000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8743.976000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8867.256000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8879.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 8893.216000] APIC error on CPU0: 40(40)

[ 8990.524000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9095.612000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9113.768000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9237.004000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9360.236000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9483.464000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9496.596000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9549.572000] APIC error on CPU0: 40(40)

[ 9606.696000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9729.920000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9761.576000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9853.156000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[ 9976.384000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[10038.796000] APIC error on CPU0: 40(40)

[10099.620000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[10177.548000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[10212.436000] APIC error on CPU0: 40(40)

[10222.840000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[10296.528000] usb 3-4: new high speed USB device using ehci_hcd and address 5

[10296.660000] usb 3-4: configuration #1 chosen from 2 choices

[10296.664000] scsi3 : SCSI emulation for USB Mass Storage devices

[10296.664000] usb-storage: device found at 5

[10296.664000] usb-storage: waiting for device to settle before scanning

[10301.664000] usb-storage: device scan complete

[10301.664000] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0

[10301.668000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)

[10301.668000] sda: Write Protect is off

[10301.668000] sda: Mode Sense: 68 00 00 08

[10301.668000] sda: assuming drive cache: write through

[10301.672000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)

[10301.672000] sda: Write Protect is off

[10301.672000] sda: Mode Sense: 68 00 00 08

[10301.672000] sda: assuming drive cache: write through

[10301.672000]  sda: sda1 sda2

[10301.676000] sd 3:0:0:0: Attached scsi removable disk sda

[10301.676000] sd 3:0:0:0: Attached scsi generic sg0 type 0

[10324.732000] APIC error on CPU0: 40(40)

[10346.444000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


maxi@maxi-laptop:~$ cat /sys/class/net/*/driver/rf_kill

cat: /sys/class/net/*/driver/rf_kill: No such file or directory

---

### Post by noob12 on 2007-08-04
As you might guess, this means the driver is failing to load the firmware.

> 
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


So don't expect it to work in its present condition.

The link I posted earlier will guide you through installing the firmware as well
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Try the instructions there.  If you have trouble we can troubleshoot that or we can setup ndiswrapper and the Windows driver.

---

### Post by maxi123 on 2007-08-04
on the procedure on that thread i have to be connected to the internet on my laptop.. this should work by connecting the ethernet cable from my modem to the back of the laptop... so did that and it connects to the network but i cant load up any websites 

thanks for your help again :)

---

### Post by noob12 on 2007-08-04
What was the modem connected to before?

---

### Post by maxi123 on 2007-08-04
it was connected to the router thats connected to my desktop.. which is where im posting this from

---

### Post by noob12 on 2007-08-04
Yes.  It will be much easier if you can plug in to the router.  Do you have additional ports and an ethernet cable so that you can plug your laptop into that router?  

If you lack another cable, can you temporarily unplug the ethernet cable from the desktop and plug it into the laptop so that the laptop is connected to the router.

---

### Post by maxi123 on 2007-08-04
okay i unplugged it from the back of my desktop and its working now :D im gonna go ahead and see if i can do the procedure thanks :)

---

### Post by noob12 on 2007-08-04
OK.  I have to checkout for the night, it's 1am here (Pacific Time).  Will be online in my morning.

---

### Post by maxi123 on 2007-08-04
thanks a lot for the link i followed the steps and i got my wireless going =D

---

### Post by noob12 on 2007-08-04
Great.  Post a new thread if you need any more help.

---

