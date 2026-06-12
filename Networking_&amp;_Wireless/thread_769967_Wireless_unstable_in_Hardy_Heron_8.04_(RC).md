---
title: "Wireless unstable in Hardy Heron 8.04 (RC)"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by prismpirate on 2008-04-27
Just upgraded to Hardy Heron 8.04(RC), and enjoying it so far. However, wireless has been very buggy. When the usage of the internet surpasses surfing the net (e.g Downloading files, apt-get ), the internet connection cuts off, and I have to manually reset the connection.

When 
```

lspci -v | less

```
 is pasted into the terminal, I get:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 03)
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, fast devsel, latency 0
        Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
:00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 03)
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, fast devsel, latency 0
        Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
:
  Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f0800000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: f0300000-f03fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	    I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f0500000-f05fffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: 0000000088100000-00000000881fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f0804c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
        Memory behind bridge: f0400000-f04fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHC
I Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
        I/O ports at 1c00 [size=8]
        I/O ports at 18d4 [size=4]
        I/O ports at 18d8 [size=8]
        I/O ports at 18d0 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f0804000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: NEC Corporation Unknown device 8875
        Flags: medium devsel, IRQ 10
        Memory at 88200000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c20 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 218
 Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
        Subsystem: Intel Corporation Turbo Memory Controller
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f0500000 (32-bit, non-prefetchable) [size=1K]
        I/O ports at 2000 [size=128]
        [virtual] Expansion ROM at 88000000 [disabled] [size=64K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, fast devsel, latency 0, IRQ 217
        Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 3000 [size=256]
        [virtual] Expansion ROM at 88100000 [disabled] [size=128K]
        Capabilities: <access denied>

06:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
 Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 168, IRQ 19
        Memory at f0404000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 8c000000-8ffff000 (prefetchable)
        Memory window 1: 90000000-93fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00004000-000040ff
        16-bit legacy interface ports at 0001

06:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: NEC Corporation Unknown device 8875
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at f0406000 (32-bit, non-prefetchable) [size=2K]
        Memory at f0400000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: NEC Corporation Unknown device 8875
  Flags: bus master, medium devsel, latency 57, IRQ 16
        Memory at f0405000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Unknown device 5678:1234
        Flags: bus master, medium devsel, latency 57, IRQ 16
        Memory at f0406800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>


```


When 
```

lshw -C network

```
is pasted into the terminal, I get
```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:1b:c0:a5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 00:1b:24:37:f9:ba
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair

```

Anyone who can help?

---

