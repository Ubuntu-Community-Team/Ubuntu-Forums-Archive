---
title: "Again PCI BCM4306 wireless card"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by darkrad on 2006-11-09
Hello,
tonight i did the dist-upgrade to get latest ubuntu build.
Obvioulsy, as expected, rebooting it neither internet or X server works ](*,) 
The card info are:

[I]# Chipset: Broadcom Corporation BCM4306 802.11g (rev 3)
# pciid: 14e4:4320 (rev 3) [/I]

I followed tutorials like:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /home/dave/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper
```
Or i even tried to download from sourgeforce the sources of ndiswrapper version 1.26 and 1.17, but the result is the same.
When i do:
```
sudo ndiswrapper -i BCMWL5.INF
```
the driver get installed just fine, and if i do
```
ndiswrapper -l
```
it answers with driver installed, hardware present, so the drivers are fine.
The problem is that when i do:
```
sudo modprobe ndiswrapper
```
after the:
```
sudo depmod -a
```
i get something like:
```
[17179600.604000] ndiswrapper (NdisWriteErrorLogEntry:237): log: C000138D, count: 1, return_address: c8ab9be3
[17179600.604000] ndiswrapper (NdisWriteErrorLogEntry:240): code: 259
```
and if i type:
```
dmesg
```
the end of the file is something like:
```
[17179578.744000] SCSI subsystem initialized
[17179578.840000] Initializing USB Mass Storage driver...
[17179578.840000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179578.840000] usbcore: registered new driver usb-storage
[17179578.840000] USB Mass Storage support registered.
[17179578.844000] usb-storage: device found at 2
[17179578.844000] usb-storage: waiting for device to settle before scanning
[17179583.844000] usb-storage: device scan complete
[17179583.852000]   Vendor: Eutron    Model: Picodisk Tech 2   Rev: 1.00
[17179583.852000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179595.916000] parport_pc: VIA 686A/8231 detected
[17179595.916000] parport_pc: probing current configuration
[17179595.916000] parport_pc: Current parallel port base: 0x378
[17179595.916000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[17179596.012000] parport_pc: VIA parallel port: io=0x378, irq=7
[17179596.024000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179596.096000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179596.576000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179596.576000] PCI: setting IRQ 11 as level-triggered
[17179596.576000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179597.036000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.080000] Floppy drive(s): fd0 is 1.44M
[17179597.096000] FDC 0 is a post-1991 82077
[17179597.104000] agpgart: Detected VIA Apollo Pro 133 chipset
[17179597.108000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179597.816000] input: PC Speaker as /class/input/input1
[17179598.260000] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[17179598.720000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179598.876000] sda: Write Protect is off
[17179598.876000] sda: Mode Sense: 0b 00 00 08
[17179598.876000] sda: assuming drive cache: write through
[17179598.972000] ts: Compaq touchscreen protocol output
[17179599.412000] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[17179599.488000] sda: Write Protect is off
[17179599.488000] sda: Mode Sense: 0b 00 00 08
[17179599.488000] sda: assuming drive cache: write through
[17179599.488000]  sda: sda1
[17179599.536000] sd 0:0:0:0: Attached scsi removable disk sda
[17179599.596000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179600.128000] Intel ISA PCIC probe: not found.
[17179600.336000] lp0: using parport0 (interrupt-driven).
[17179600.504000] ndiswrapper version 1.26 loaded (preempt=no,smp=yes)
[17179600.596000] ndiswrapper: driver bcmwl5 (Broadcom,07/17/2003, 3.30.15.0) loaded
[17179600.596000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179600.604000] ndiswrapper (NdisWriteErrorLogEntry:237): log: C000138D, count: 1, return_address: c8ab9be3
[17179600.604000] ndiswrapper (NdisWriteErrorLogEntry:240): code: 259
[17179600.604000] ndiswrapper (miniport_init:269): couldn't initialize device: C0000001
[17179600.604000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[17179600.604000] unregister_netdevice: device eth%d/c4611000 never was registered
[17179600.604000] ndiswrapper (miniport_halt:326): device c4611400 is not initialized - not halting
[17179600.604000] ndiswrapper: device eth%d removed
[17179600.604000] ACPI: PCI interrupt for device 0000:00:0d.0 disabled
[17179600.604000] ndiswrapper: probe of 0000:00:0d.0 failed with error -22
[17179600.608000] usbcore: registered new driver ndiswrapper
```
and then if i type again:
```
sudo modprobe ndiswrapper
```
i get no output and anyway the card doesn't work since if i do:
```
iwconfig
```
all devices says "no wireless".

Obviously before the dist-upgrade the pci wireless network card worked ](*,) 
Any help please?

---

