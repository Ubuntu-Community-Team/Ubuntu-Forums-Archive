---
title: "USB headset not detected after upgrades (10.04)"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by movicont on 2010-08-24
I'm using a Plantronics headset, and after upgrading a couple of packages, it has stopped working. I checked in 'System->Preferences->Sound' and the hardware tab is empty. However, doing lsusb gives:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 005 Device 002: ID 0d8c:000e C-Media Electronics, Inc. Audio Adapter (Planet UP-100, Genius G-Talk)**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

where the bolded is my headset.

Here's the output from lspci -v:

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Device 01f1
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Dell Device 01f1
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at eff8 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Dell Device 01f1
	Flags: bus master, fast devsel, latency 0
	Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f20 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f00 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 80000000-801fffff
	Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe600000-fe7fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 6f40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: fe500000-fe5fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Dell Device 01f1
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=32]
	Memory at fe9fb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Device 01f1
	Flags: medium devsel, IRQ 10
	Memory at fe9fb700 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fe5fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Dell Device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at fe5fd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Device 0007
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb


```

Output from dpkg -l | grep "alsa"
```

ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                   1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                               0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                                 4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                            0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                         0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu3                                 Simple DirectMedia Layer (with X11 and ALSA 

```

Any help in getting my headset detected/working again would be appreciated!

---

### Post by movicont on 2010-08-24
Bump. Help?

---

### Post by khelben1979 on 2010-08-24
Did the Ubuntu upgrade packages contain a kernel upgrade? Also, have you tried if an reboot or changing USB port solves the problem?

---

### Post by movicont on 2010-08-24
Yeah, I think one of the upgrade packages did have a kernel upgrade. (That's what the linux headers stuff is for right?)

I've already rebooted multiple times and I just tried different usb ports as well. None of them worked.

---

### Post by movicont on 2010-08-24
Ooh, wait, I figured it out now--I just reverted back to the old kernel. Thanks for your help! :)

---

### Post by khelben1979 on 2010-08-25
Good that you got it working! I recommend you click in the thread tools tab and mark the thread as solved.

---

