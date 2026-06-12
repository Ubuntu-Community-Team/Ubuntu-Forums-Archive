---
title: "eth0 no longer showing up on network list"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by sutabi on 2007-08-09
When I goto System->Network my eth0 connect is gone, no longer shwoing up. Only thin that shows up is "Modem connection"

$ lspci
Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

$ sudo lshw -class network
```

*- nework UNCLAIMED
            description: Ethernet controller
            product: 82557/8/9 [Ethernet Pro 100]
            vendor: Intel Corporation
            physical id: 3
            bus info: pci&00:03.0
            version: 0c
            width: 32 bits
            clock: 33Mhz
            capabilities: cap_list
            configuration latency=66 maxlatency=56 mingnt=8
            resources: iomemory:f4120000-f4120ffff ioport:1800-183f iomemory:f4100000-f411ffff irq:11

```

---

### Post by kevdog on 2007-08-10
Its not showing up because there is no driver associated with the card.  Thats strange.  Might have to google around and find the driver module associated with your card.  Also check synaptic for restriced packages to see if an intel (ipw) driver is offered.

---

### Post by noob12 on 2007-08-10
sutabi:  What release are you running?  I'd expect this to be claimed by the e100.  This should be there in Feisty.

Can you **modinfo e100** and do you see a description of the driver?  If so, try doing a manual modprobe from the command line.

```

sudo modprobe -v e100 debug=16

```

---

### Post by sutabi on 2007-08-10
xubuntu 7.04

I tried sudo modprobe -v e100 debug=16 with no luck :\


```

sutabi@sutabi-laptop:~$ modinfo e100
filename:       /lib/modules/2.6.20-15-generic/kernel/drivers/net/e100.ko
version:        3.5.17-k2-NAPI
license:        GPL
author:         Copyright(c) 1999-2006 Intel Corporation
description:    Intel(R) PRO/100 Network Driver
srcversion:     0CD865BFF609882A5CB906D
alias:          pci:v00008086d000027DCsv*sd*bc02sc00i*
alias:          pci:v00008086d0000245Dsv*sd*bc02sc00i*
alias:          pci:v00008086d00002459sv*sd*bc02sc00i*
alias:          pci:v00008086d00002449sv*sd*bc02sc00i*
alias:          pci:v00008086d00001229sv*sd*bc02sc00i*
alias:          pci:v00008086d00001209sv*sd*bc02sc00i*
alias:          pci:v00008086d00001095sv*sd*bc02sc00i*
alias:          pci:v00008086d00001094sv*sd*bc02sc00i*
alias:          pci:v00008086d00001093sv*sd*bc02sc00i*
alias:          pci:v00008086d00001092sv*sd*bc02sc00i*
alias:          pci:v00008086d00001091sv*sd*bc02sc00i*
alias:          pci:v00008086d0000106Bsv*sd*bc02sc00i*
alias:          pci:v00008086d0000106Asv*sd*bc02sc00i*
alias:          pci:v00008086d00001069sv*sd*bc02sc00i*
alias:          pci:v00008086d00001068sv*sd*bc02sc00i*
alias:          pci:v00008086d00001067sv*sd*bc02sc00i*
alias:          pci:v00008086d00001066sv*sd*bc02sc00i*
alias:          pci:v00008086d00001065sv*sd*bc02sc00i*
alias:          pci:v00008086d00001064sv*sd*bc02sc00i*
alias:          pci:v00008086d00001059sv*sd*bc02sc00i*
alias:          pci:v00008086d00001057sv*sd*bc02sc00i*
alias:          pci:v00008086d00001056sv*sd*bc02sc00i*
alias:          pci:v00008086d00001055sv*sd*bc02sc00i*
alias:          pci:v00008086d00001054sv*sd*bc02sc00i*
alias:          pci:v00008086d00001053sv*sd*bc02sc00i*
alias:          pci:v00008086d00001052sv*sd*bc02sc00i*
alias:          pci:v00008086d00001051sv*sd*bc02sc00i*
alias:          pci:v00008086d00001050sv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Esv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Dsv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Csv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Bsv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Asv*sd*bc02sc00i*
alias:          pci:v00008086d00001039sv*sd*bc02sc00i*
alias:          pci:v00008086d00001038sv*sd*bc02sc00i*
alias:          pci:v00008086d00001034sv*sd*bc02sc00i*
alias:          pci:v00008086d00001033sv*sd*bc02sc00i*
alias:          pci:v00008086d00001032sv*sd*bc02sc00i*
alias:          pci:v00008086d00001031sv*sd*bc02sc00i*
alias:          pci:v00008086d00001030sv*sd*bc02sc00i*
alias:          pci:v00008086d00001029sv*sd*bc02sc00i*
depends:        mii
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           eeprom_bad_csum_allow:Allow bad eeprom checksums (int)
```

---

### Post by noob12 on 2007-08-10
OK.  You do have e100.  What would be helpful to see is the output of the command and the tail of dmesg after the modprobe.

Try the modprobe command I suggested earlier again, but this time show us the output from the command line and also please run
```

dmesg | tail -100

```
and include that.   The driver should be putting messages there that should tell us why it's not claiming the device.

---

### Post by sutabi on 2007-08-12
```
sutabi@sutabi-laptop:~$ sudo modprobe -v e100 debug=16
Password:
sutabi@sutabi-laptop:~$ dmesg | tail -100
[   29.052000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   29.240000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   29.240000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   29.240000] PCI: Enabling device 0000:06:00.0 (0000 -> 0003)
[   29.240000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   29.240000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   29.240000] acx: found ACX100-based wireless network card at 0000:06:00.0, irq:11, phymem1:0x2C010000, phymem2:0x2C000000, mem1:0xd09ca000, mem1_size:4096, mem2:0xd0a80000, mem2_size:65536
[   29.244000] acx: loading firmware for acx100 chipset with radio ID 15
[   29.320000] acx: firmware image 'acx/default/tiacx100c15' was not provided. Check your hotplug scripts
[   29.328000] acx: firmware image 'acx/default/tiacx100' was not provided. Check your hotplug scripts
[   29.328000] acx: reset_dev() FAILED
[   29.328000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[   29.344000] acx_pci: probe of 0000:06:00.0 failed with error -5
[   29.344000] usbcore: registered new interface driver acx_usb
[   29.436000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   29.472000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[   29.480000] pnp: Device 00:0e activated.
[   29.480000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   29.480000] nsc-ircc, chip->init
[   29.480000] nsc-ircc, Found chip at base=0x02e
[   29.480000] nsc-ircc, driver loaded (Dag Brattli)
[   29.480000] IrDA: Registered device irda0
[   29.480000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   29.588000] cs: IO port probe 0x100-0x3af: clean.
[   29.700000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   29.700000] cs: IO port probe 0x820-0x8ff: clean.
[   29.700000] cs: IO port probe 0xc00-0xcf7: clean.
[   29.700000] cs: IO port probe 0xa00-0xaff: clean.
[   29.700000] cs: IO port probe 0x100-0x3af: clean.
[   29.700000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   29.700000] cs: IO port probe 0x820-0x8ff: clean.
[   29.704000] cs: IO port probe 0xc00-0xcf7: clean.
[   29.704000] cs: IO port probe 0xa00-0xaff: clean.
[   29.852000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   30.420000] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1807kHz
[   30.760000] lp0: using parport0 (interrupt-driven).
[   30.832000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   30.972000] ndiswrapper: driver netswl23 (SAMSUNG,08/07/2003,1.2.2) loaded
[   30.988000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   30.988000] ndiswrapper: using IRQ 11
[   30.988000] ndiswrapper (miniport_init:275): couldn't initialize device: C0000001
[   30.988000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[   30.988000] unregister_netdevice: device eth%d/c1347000 never was registered
[   30.988000] ndiswrapper (miniport_halt:339): device c1347400 is not initialized - not halting
[   30.988000] ndiswrapper: device eth%d removed
[   30.988000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[   30.988000] ndiswrapper: probe of 0000:06:00.0 failed with error -22
[   30.988000] usbcore: registered new interface driver ndiswrapper
[   31.056000] Adding 746980k swap on /dev/disk/by-uuid/5ffaf768-20a7-49ef-b9aa-58841442c356.  Priority:-1 extents:1 across:746980k
[   31.140000] EXT3 FS on hda1, internal journal
[   33.056000] NET: Registered protocol family 17
[   39.464000] ACPI: AC Adapter [AC] (on-line)
[   39.664000] ACPI: Battery Slot [BAT0] (battery present)
[   39.792000] input: Power Button (FF) as /class/input/input4
[   39.800000] ACPI: Power Button (FF) [PWRF]
[   39.872000] input: Lid Switch as /class/input/input5
[   39.872000] ACPI: Lid Switch [LID]
[   39.908000] input: Sleep Button (CM) as /class/input/input6
[   39.908000] ACPI: Sleep Button (CM) [SLPB]
[   40.012000] Using specific hotkey driver
[   40.108000] ACPI: ACPI Dock Station Driver 
[   40.208000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   40.208000] ibm_acpi: http://ibm-acpi.sf.net/
[   40.476000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   40.560000] pcc_acpi: loading...
[   49.224000] ppdev: user-space parallel port driver
[   59.172000] IBM machine detected. Enabling interrupts during APM calls.
[   59.172000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   59.172000] apm: overridden by ACPI.
[   59.496000] Non-volatile memory driver v1.2
[   59.632000] input: /usr/sbin/thinkpad-keys as /class/input/input7
[   59.792000] ondemand governor failed to load due to too long transition latency
[  337.028000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  337.196000] usb 1-1: configuration #1 chosen from 1 choice
[  337.592000] usbcore: registered new interface driver libusual
[  337.624000] Initializing USB Mass Storage driver...
[  337.624000] scsi0 : SCSI emulation for USB Mass Storage devices
[  337.624000] usbcore: registered new interface driver usb-storage
[  337.624000] USB Mass Storage support registered.
[  337.624000] usb-storage: device found at 2
[  337.624000] usb-storage: waiting for device to settle before scanning
[  342.624000] usb-storage: device scan complete
[  342.628000] scsi 0:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
[  345.224000] ready
[  345.228000] SCSI device sda: 2037760 512-byte hdwr sectors (1043 MB)
[  345.232000] sda: Write Protect is off
[  345.232000] sda: Mode Sense: 03 00 00 00
[  345.232000] sda: assuming drive cache: write through
[  345.244000] SCSI device sda: 2037760 512-byte hdwr sectors (1043 MB)
[  345.244000] sda: Write Protect is off
[  345.244000] sda: Mode Sense: 03 00 00 00
[  345.244000] sda: assuming drive cache: write through
[  345.244000]  sda: sda1
[  345.252000] sd 0:0:0:0: Attached scsi removable disk sda
[  345.292000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  461.916000] NET: Registered protocol family 10
[  461.916000] lo: Disabled Privacy Extensions
[  521.256000] usb 1-1: USB disconnect, address 2
[  521.260000] Buffer I/O error on device sda1, logical block 499
[  521.260000] lost page write due to I/O error on sda1

```

---

### Post by noob12 on 2007-08-12
Are you running the 64 bit kernel by any chance?   I notice output from ndiswrapper and also a driver called acx which both look unhappy.  Had you done something with these?   Can you include the output from this
```

uname -r

ndiswrapper -l

cat /etc/modprobe.d/blacklist

cat /etc/modules

```

Did your problems with the wired ethernet begin after you had installed these other drivers?

I don't see anything indicating e100 loaded when we last tried to manually load it.  Maybe it is because it was already loaded; we'll try removing and reloading it this time.  Sorry.

```

sudo modprobe -r e100
sudo modprobe e100 debug=15

```

Please resend the output of 
```

dmesg | tail -100

```
after this.

---

### Post by sutabi on 2007-08-15
Okay I went ahead and posted the results. I am running the 32 bit version. Sorry for the delay >.<



```

sutabi@sutabi-laptop:~$ uname -r
2.6.20-15-generic
sutabi@sutabi-laptop:~$ ndiswrapper -l
netswl23 : driver installed
        device (104C:8400) present (alternate driver: acx)
sutabi@sutabi-laptop:~$ cat /etc/blacklist
cat: /etc/blacklist: No such file or directory
sutabi@sutabi-laptop:~$ cat /etc modules
cat: /etc: Is a directory
cat: modules: No such file or directory
sutabi@sutabi-laptop:~$ sudo modprobe -r e100
Password:
sutabi@sutabi-laptop:~$ sudo modprobe e100 debug=15
sutabi@sutabi-laptop:~$ dmesg | tail -100
[   31.644000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   31.680000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[   31.848000] pnp: Device 00:0e activated.
[   31.848000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   31.848000] nsc-ircc, chip->init
[   31.848000] nsc-ircc, Found chip at base=0x02e
[   31.848000] nsc-ircc, driver loaded (Dag Brattli)
[   31.848000] IrDA: Registered device irda0
[   31.848000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   32.404000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   32.440000] cs: IO port probe 0x100-0x3af: clean.
[   32.440000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   32.440000] cs: IO port probe 0x820-0x8ff: clean.
[   32.444000] cs: IO port probe 0xc00-0xcf7: clean.
[   32.444000] cs: IO port probe 0xa00-0xaff: clean.
[   32.444000] cs: IO port probe 0x100-0x3af: clean.
[   32.444000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   32.444000] cs: IO port probe 0x820-0x8ff: clean.
[   32.444000] cs: IO port probe 0xc00-0xcf7: clean.
[   32.444000] cs: IO port probe 0xa00-0xaff: clean.
[   32.468000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   32.468000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   32.972000] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1864kHz
[   32.984000] PCI: Enabling device 0000:06:00.0 (0000 -> 0003)
[   32.984000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   32.984000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   32.984000] acx: found ACX100-based wireless network card at 0000:06:00.0, irq:11, phymem1:0x2C010000, phymem2:0x2C000000, mem1:0xd0850000, mem1_size:4096, mem2:0xd0b60000, mem2_size:65536
[   32.984000] acx: loading firmware for acx100 chipset with radio ID 15
[   33.112000] acx: firmware image 'acx/default/tiacx100c15' was not provided. Check your hotplug scripts
[   33.120000] acx: firmware image 'acx/default/tiacx100' was not provided. Check your hotplug scripts
[   33.120000] acx: reset_dev() FAILED
[   33.120000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[   33.136000] acx_pci: probe of 0000:06:00.0 failed with error -5
[   33.136000] usbcore: registered new interface driver acx_usb
[   33.420000] lp0: using parport0 (interrupt-driven).
[   33.484000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   33.620000] ndiswrapper: driver netswl23 (SAMSUNG,08/07/2003,1.2.2) loaded
[   33.640000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   33.640000] ndiswrapper: using IRQ 11
[   33.640000] ndiswrapper (miniport_init:275): couldn't initialize device: C0000001
[   33.640000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[   33.640000] unregister_netdevice: device eth%d/c82d5000 never was registered
[   33.640000] ndiswrapper (miniport_halt:339): device c82d5400 is not initialized - not halting
[   33.640000] ndiswrapper: device eth%d removed
[   33.640000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[   33.640000] ndiswrapper: probe of 0000:06:00.0 failed with error -22
[   33.640000] usbcore: registered new interface driver ndiswrapper
[   33.708000] Adding 746980k swap on /dev/disk/by-uuid/5ffaf768-20a7-49ef-b9aa-58841442c356.  Priority:-1 extents:1 across:746980k
[   33.792000] EXT3 FS on hda1, internal journal
[   35.652000] NET: Registered protocol family 17
[   42.032000] ACPI: AC Adapter [AC] (on-line)
[   42.228000] ACPI: Battery Slot [BAT0] (battery present)
[   42.356000] input: Power Button (FF) as /class/input/input4
[   42.364000] ACPI: Power Button (FF) [PWRF]
[   42.432000] input: Lid Switch as /class/input/input5
[   42.432000] ACPI: Lid Switch [LID]
[   42.464000] input: Sleep Button (CM) as /class/input/input6
[   42.464000] ACPI: Sleep Button (CM) [SLPB]
[   42.572000] Using specific hotkey driver
[   42.672000] ACPI: ACPI Dock Station Driver 
[   42.768000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   42.768000] ibm_acpi: http://ibm-acpi.sf.net/
[   43.032000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   43.112000] pcc_acpi: loading...
[   51.640000] ppdev: user-space parallel port driver
[   61.640000] IBM machine detected. Enabling interrupts during APM calls.
[   61.640000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   61.640000] apm: overridden by ACPI.
[   61.928000] Non-volatile memory driver v1.2
[   62.068000] input: /usr/sbin/thinkpad-keys as /class/input/input7
[   62.228000] ondemand governor failed to load due to too long transition latency
[  223.696000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  223.864000] usb 1-1: configuration #1 chosen from 1 choice
[  224.260000] usbcore: registered new interface driver libusual
[  224.320000] Initializing USB Mass Storage driver...
[  224.320000] scsi0 : SCSI emulation for USB Mass Storage devices
[  224.320000] usbcore: registered new interface driver usb-storage
[  224.320000] USB Mass Storage support registered.
[  224.320000] usb-storage: device found at 2
[  224.320000] usb-storage: waiting for device to settle before scanning
[  229.320000] usb-storage: device scan complete
[  229.324000] scsi 0:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
[  231.444000] ready
[  231.448000] SCSI device sda: 2037760 512-byte hdwr sectors (1043 MB)
[  231.452000] sda: Write Protect is off
[  231.452000] sda: Mode Sense: 03 00 00 00
[  231.452000] sda: assuming drive cache: write through
[  231.464000] SCSI device sda: 2037760 512-byte hdwr sectors (1043 MB)
[  231.464000] sda: Write Protect is off
[  231.464000] sda: Mode Sense: 03 00 00 00
[  231.464000] sda: assuming drive cache: write through
[  231.464000]  sda: sda1
[  231.472000] sd 0:0:0:0: Attached scsi removable disk sda
[  231.512000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  658.880000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[  658.880000] e100: Copyright(c) 1999-2006 Intel Corporation
[  658.884000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  658.968000] e100: 0000:00:03.0: e100_eeprom_load: EEPROM corrupted
[  658.968000] ACPI: PCI interrupt for device 0000:00:03.0 disabled
[  658.968000] e100: probe of 0000:00:03.0 failed with error -11

```

---

### Post by noob12 on 2007-08-15
I must have been tired because there were several typos in the commands I asked you to type.  
I went back and corrected those.

Luckily we got enough right that we've got our culprit:
> 
[  658.880000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[  658.880000] e100: Copyright(c) 1999-2006 Intel Corporation
[  658.884000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[COLOR="Red"][  658.968000] e100: 0000:00:03.0: e100_eeprom_load: EEPROM corrupted
[  658.968000] ACPI: PCI interrupt for device 0000:00:03.0 disabled
[  658.968000] e100: probe of 0000:00:03.0 failed with error -11[/COLOR]


This is why e100 isn't able to initialize and claim that interface.

First try this
```

sudo modprobe -r e100
sudo modprobe e100 eeprom_bad_csum_allow=1

```

See if your ethernet interface comes back to life.  Check **lshw -C network** and **ifconfig -a** and send the results.

If it works for you, we can set this up as an option that will be used automatically at boot.   You may also be able to repair the EEPROM using a tool from Intel.

---

### Post by sutabi on 2007-08-15
THANK YOU SOOOOOooOoOOoOOo Much!!!

Works like a charm here is the output:
```

sutabi@sutabi-laptop:~$ sudo lshw -C network
  *-network               
       description: Texas InstrumentS
       physical id: 0
       version: ACX100 CaraBus Model Board
       slot: Socket 1
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth1
       version: 0c
       serial: 02:00:47:91:4f:11
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:f4120000-f4120fff ioport:1800-183f iomemory:f4100000-f411ffff irq:11
  *-network UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64
       resources: ioport:3000-301f iomemory:2c010000-2c010fff iomemory:2c000000-2c00ffff irq:11
sutabi@sutabi-laptop:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 02:00:47:91:4F:11  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::47ff:fe91:4f11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:793470 (774.8 KiB)  TX bytes:37959 (37.0 KiB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20913 (20.4 KiB)  TX bytes:20913 (20.4 KiB)


```

---

### Post by noob12 on 2007-08-15
OK.  If you experience the same problem on reboots, then here is what you can do to use this option permanently

```

echo "options e100 eeprom_bad_csum_allow=1" | sudo tee -a /etc/modprobe.d/options

sudo /usr/sbin/update-initramfs -u

```

---

