---
title: "ubuntu  freezes often"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by kumaresan89 on 2009-10-01
hi i am new to ubuntu and i installed  ubuntu 9.04 
it freezes very often. Even Xp doesnt hang this much in my system is there any solution for this 
thanks..

System configuration:
intel D946 motherboard
intel core 2 duo processor 
1 GB RAM

---

### Post by pawhtiobo on 2009-10-01
Hi :)

It freezes randomly or when you are doing a specific task?

see ya...

---

### Post by kumaresan89 on 2009-10-01
it freezes mostly when i am using netbeans ,firefox and opera

---

### Post by pawhtiobo on 2009-10-01
Hi :)

What kind of computer is this, a laptop or desktop? Have you checked the CPU temperatures and CPU usage when those applications are open.

See ya,

---

### Post by ukripper on 2009-10-01
Can you post output of the following commands after running in terminal:

```
lspci
```

```
sudo dmesg | tail -n 40
```

---

### Post by kumaresan89 on 2009-10-01
it is a desktop.CPU usage is is around 50% 
i dont know how to check CPU temperatures

---

### Post by ukripper on 2009-10-01
> **kumaresan89 said:**
> it is a desktop.CPU usage is is around 50% 
i dont know how to check CPU temperatures

You can check temperature using below command in terminal

```
cat /proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by kumaresan89 on 2009-10-01
> **ukripper said:**
> Can you post output of the following commands after running in terminal:

```
lspci
``````
sudo dmesg | tail -n 40
```

for lspci
```

00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
```

and for sudo dmesg | tail -n 40

[code][    9.436696] intel_rng: you are certain that your system has a functional
[    9.436697] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    9.506577] Linux agpgart interface v0.103
[    9.540353] agpgart-intel 0000:00:00.0: Intel 946GZ Chipset
[    9.541099] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    9.544965] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    9.638929] ppdev: user-space parallel port driver
[   10.263703] iTCO_vendor_support: vendor-support=0
[   10.265308] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.265423] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   10.265480] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.295396] psmouse serio1: ID: 10 00 64<6>HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.585414] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.896399] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   10.992229] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input6
[   11.004244] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input7
[   11.016228] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input8
[   11.028227] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input9
[   11.040234] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input10
[   11.052246] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input11
[   11.064232] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input12
[   11.076229] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[   11.270100] lp0: using parport0 (interrupt-driven).
[   11.346425] Adding 2000052k swap on /dev/sda10.  Priority:-1 extents:1 across:2000052k 
[   11.897831] EXT3 FS on sda9, internal journal
[   13.563552] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   14.037653] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.040624] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   14.052965] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.692228] NET: Registered protocol family 24
[   15.462238] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.399226] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.399229] Bluetooth: BNEP filters: protocol multicast
[   17.422574] Bridge firewalling registered
[   19.227775] [drm] Initialized drm 1.1.0 20060810
[   19.243375] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.243382] pci 0000:00:02.0: setting latency timer to 64
[   19.246051] pci 0000:00:02.0: irq 27 for MSI/MSI-X
[   19.246096] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   24.224120] eth0: no IPv6 routers present [code/]

---

### Post by kumaresan89 on 2009-10-01
> **ukripper said:**
> You can check temperature using below command in terminal

```
cat /proc/acpi/thermal_zone/THRM/temperature
```

it shows error message 
```
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory
```

---

### Post by ukripper on 2009-10-01
> **kumaresan89 said:**
> 
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)


There is a bug reported on launchpad in regards to your Intel graphics card - Check here [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367263](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367263)

You may have to either switch to ubuntu 8.04 or wait for 9.10 to comeout next month with new kernel. Many intel based cards are currently having such problems of freezing on 9.04.

I'd suggest you use 8.04 until 9.10 is out

---

