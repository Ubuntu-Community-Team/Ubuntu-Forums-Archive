---
title: "Ubunto 16.04 Ethernet Connection issue with Gigabyte 990fx gaming motherboard"
date: 2017-12-20
forum: Networking &amp; Wireless
---

### Post by squeeky0123 on 2017-12-20
Hi, 

I have installed Ubunto 16.04 on a system with the Gigabyte 99fx-gaming mother board. I have already overcome the USB connection issue by enabling the IMMOU in the bios but once Ubunto finally installed, I found that i have not internet access. I have hardwired the cable into the modem and still nothing. There are error reports in my usb and ethernet controls. Can Anyone tell me if there is a driver set somewhere I can load to fix the issues?  I have run a check of the system and get these results: 

 ```
sudo lspci -v

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI]RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
            Subsystem:Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0port B)
            Flags: fastdevsel
            Capabilities:[f0] HyperTransport: MSI Mapping Enable+ Fixed+
            Capabilities:[c4] HyperTransport: Slave or Primary Interface
            Capabilities:[40] HyperTransport: Retry Mode
            Capabilities:[54] HyperTransport: UnitID Clumping
            Capabilities:[9c] HyperTransport: #1a
            Capabilities:[70] MSI: Enable- Count=1/4 Maskable- 64bit-
 
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990I/O Memory Management Unit (IOMMU)
            Subsystem:Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
            Flags: fastdevsel, IRQ 26
            Capabilities:[40] Secure device <?>
            Capabilities:[54] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities:[64] HyperTransport: MSI Mapping Enable+ Fixed+
 
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI]RD890 PCI to PCI bridge (PCI express gpp port B) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0, IRQ 27
            Bus:primary=00, secondary=01, subordinate=01, sec-latency=0
            I/O behindbridge: 0000e000-0000efff
            Memorybehind bridge: fea00000-feafffff
            Prefetchablememory behind bridge: 00000000d0000000-00000000dfffffff
            Capabilities:[50] Power Management version 3
            Capabilities:[58] Express Root Port (Slot+), MSI 00
            Capabilities:[a0] MSI: Enable- Count=1/1 Maskable- 64bit-
            Capabilities:[b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge(PCI express gpp port B)
            Capabilities:[b8] HyperTransport: MSI Mapping Enable+ Fixed+
            Capabilities:[100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
            Capabilities:[190] Access Control Services
            Kerneldriver in use: pcieport
            Kernelmodules: shpchp
 
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI]RD890 PCI to PCI bridge (PCI express gpp port F) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0, IRQ 24
            Bus:primary=00, secondary=02, subordinate=02, sec-latency=0
            Memorybehind bridge: fe900000-fe9fffff
            Capabilities:[50] Power Management version 3
            Capabilities:[58] Express Root Port (Slot+), MSI 00
            Capabilities:[a0] MSI: Enable- Count=1/1 Maskable- 64bit-
            Capabilities:[b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge(PCI express gpp port F)
            Capabilities:[b8] HyperTransport: MSI Mapping Enable+ Fixed+
            Capabilities:[100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
            Capabilities:[190] Access Control Services
            Kerneldriver in use: pcieport
            Kernelmodules: shpchp
 
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI]RD890 PCI to PCI bridge (PCI express gpp port H) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0, IRQ 24
            Bus:primary=00, secondary=03, subordinate=03, sec-latency=0
            Memorybehind bridge: fe800000-fe8fffff
            Capabilities:[50] Power Management version 3
            Capabilities:[58] Express Root Port (Slot+), MSI 00
            Capabilities:[a0] MSI: Enable- Count=1/1 Maskable- 64bit-
            Capabilities:[b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge(PCI express gpp port H)
            Capabilities:[b8] HyperTransport: MSI Mapping Enable+ Fixed+
            Capabilities:[100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
            Capabilities:[190] Access Control Services
            Kerneldriver in use: pcieport
            Kernelmodules: shpchp
 
00:11.0 SATA controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01[AHCI 1.0])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 19
            I/O ports atf040 [size=8]
            I/O ports atf030 [size=4]
            I/O ports atf020 [size=8]
            I/O ports atf010 [size=4]
            I/O ports atf000 [size=16]
            Memory atfeb0b000 (32-bit, non-prefetchable) [size=1K]
            Capabilities:[70] SATA HBA v1.0
            Capabilities:[a4] PCI Advanced Features
            Kerneldriver in use: ahci
            Kernelmodules: ahci
 
00:12.0 USB controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 18
            Memory atfeb0a000 (32-bit, non-prefetchable) [size=4K]
            Kerneldriver in use: ohci-pci
 
00:12.2 USB controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 17
            Memory atfeb09000 (32-bit, non-prefetchable) [size=256]
            Capabilities:[c0] Power Management version 2
            Capabilities:[e4] Debug port: BAR=1 offset=00e0
            Kerneldriver in use: ehci-pci
 
00:13.0 USB controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 18
            Memory atfeb08000 (32-bit, non-prefetchable) [size=4K]
            Kerneldriver in use: ohci-pci
 
00:13.2 USB controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 17
            Memory atfeb07000 (32-bit, non-prefetchable) [size=256]
            Capabilities:[c0] Power Management version 2
            Capabilities:[e4] Debug port: BAR=1 offset=00e0
            Kerneldriver in use: ehci-pci
 
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00SMBus Controller (rev 42)
            Subsystem:Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller
            Flags:66MHz, medium devsel
            Kerneldriver in use: piix4_smbus
            Kernelmodules: i2c_piix4, sp5100_tco
 
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI]SBx00 Azalia (Intel HDA) (rev 40)
            Subsystem:Gigabyte Technology Co., Ltd SBx00 Azalia (Intel HDA)
            Flags: busmaster, slow devsel, latency 32, IRQ 16
            Memory atfeb00000 (64-bit, non-prefetchable) [size=16K]
            Capabilities:[50] Power Management version 2
            Kerneldriver in use: snd_hda_intel
            Kernelmodules: snd_hda_intel
 
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI]SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
            Subsystem:Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
            Flags: busmaster, 66MHz, medium devsel, latency 0
 
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI]SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
            Flags: busmaster, VGA palette snoop, 66MHz, medium devsel, latency 64
            Bus:primary=00, secondary=04, subordinate=04, sec-latency=64
 
00:14.5 USB controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 18
            Memory atfeb06000 (32-bit, non-prefetchable) [size=4K]
            Kerneldriver in use: ohci-pci
 
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI]SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0, IRQ 16
            Bus:primary=00, secondary=05, subordinate=05, sec-latency=0
            I/O behindbridge: 0000d000-0000dfff
            Memorybehind bridge: fe700000-fe7fffff
            Capabilities:[50] Power Management version 3
            Capabilities:[58] Express Root Port (Slot-), MSI 00
            Capabilities:[a0] MSI: Enable- Count=1/1 Maskable- 64bit+
            Capabilities:[b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI toPCI bridge (PCIE port 0)
            Capabilities:[b8] HyperTransport: MSI Mapping Enable+ Fixed+
            Capabilities:[100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
            Kerneldriver in use: pcieport
            Kernelmodules: shpchp
 
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI]SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0, IRQ 16
            Bus:primary=00, secondary=06, subordinate=06, sec-latency=0
            Memorybehind bridge: fe600000-fe6fffff
            Capabilities:[50] Power Management version 3
            Capabilities:[58] Express Root Port (Slot-), MSI 00
            Capabilities:[a0] MSI: Enable- Count=1/1 Maskable- 64bit+
            Capabilities:[b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI toPCI bridge (PCIE port 1)
            Capabilities:[b8] HyperTransport: MSI Mapping Enable+ Fixed+
            Capabilities:[100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
            Kerneldriver in use: pcieport
            Kernelmodules: shpchp
 
00:16.0 USB controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 18
            Memory atfeb05000 (32-bit, non-prefetchable) [size=4K]
            Kerneldriver in use: ohci-pci
 
00:16.2 USB controller: Advanced Micro Devices, Inc.[AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
            Subsystem:Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 17
            Memory atfeb04000 (32-bit, non-prefetchable) [size=256]
            Capabilities:[c0] Power Management version 2
            Capabilities:[e4] Debug port: BAR=1 offset=00e0
            Kerneldriver in use: ehci-pci
 
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 15h Processor Function 0
            Flags: fastdevsel
            Capabilities:[80] HyperTransport: Host or Secondary Interface
 
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 15h Processor Function 1
            Flags: fastdevsel
 
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 15h Processor Function 2
            Flags: fastdevsel
 
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 15h Processor Function 3
            Flags: fastdevsel
            Capabilities:[f0] Secure device <?>
            Kerneldriver in use: k10temp
            Kernelmodules: k10temp
 
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 15h Processor Function 4
            Flags: fastdevsel
            Kerneldriver in use: fam15h_power
            Kernelmodules: fam15h_power
 
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 15h Processor Function 5
            Flags: fastdevsel
 
01:00.0 VGA compatible controller: Advanced Micro Devices,Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X] (prog-if 00 [VGA controller])
            Subsystem:XFX Pine Group Inc. Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
            Flags: busmaster, fast devsel, latency 0, IRQ 40
            Memory atd0000000 (64-bit, prefetchable) [size=256M]
            Memory atfea00000 (64-bit, non-prefetchable) [size=256K]
            I/O ports ate000 [size=256]
            ExpansionROM at 000c0000 [disabled] [size=128K]
            Capabilities:[48] Vendor Specific Information: Len=08 <?>
            Capabilities:[50] Power Management version 3
            Capabilities:[58] Express Legacy Endpoint, MSI 00
            Capabilities:[a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities:[100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
            Capabilities:[150] Advanced Error Reporting
            Capabilities:[270] #19
            Capabilities:[2b0] Address Translation Service (ATS)
            Capabilities:[2c0] #13
            Capabilities:[2d0] #1b
            Kerneldriver in use: radeon
            Kernelmodules: radeon
 
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI]Tahiti XT HDMI Audio [Radeon HD 7970 Series]
            Subsystem:XFX Pine Group Inc. Tahiti XT HDMI Audio [Radeon HD 7970 Series]
            Flags: busmaster, fast devsel, latency 0, IRQ 42
            Memory atfea60000 (64-bit, non-prefetchable) [size=16K]
            Capabilities:[48] Vendor Specific Information: Len=08 <?>
            Capabilities:[50] Power Management version 3
            Capabilities:[58] Express Legacy Endpoint, MSI 00
            Capabilities:[a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities:[100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
            Capabilities:[150] Advanced Error Reporting
            Kerneldriver in use: snd_hda_intel
            Kernelmodules: snd_hda_intel
 
02:00.0 USB controller: VIA Technologies, Inc. VL80x xHCI USB3.0 Controller (rev 03) (prog-if 30 [XHCI])
            Subsystem:VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller
            Flags: busmaster, fast devsel, latency 0, IRQ 29
            Memory atfe900000 (32-bit, non-prefetchable) [size=4K]
            Capabilities:[80] Power Management version 3
            Capabilities:[90] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities:[c4] Express Endpoint, MSI 00
            Capabilities:[100] Advanced Error Reporting
            Kerneldriver in use: xhci_hcd
 
03:00.0 USB controller: ASMedia Technology Inc. Device 1343(prog-if 30 [XHCI])
            Subsystem:Gigabyte Technology Co., Ltd Device 5007
            Flags: busmaster, fast devsel, latency 0, IRQ 30
            Memory atfe800000 (64-bit, non-prefetchable) [size=32K]
            Capabilities:[50] MSI: Enable- Count=1/8 Maskable- 64bit+
            Capabilities:[68] MSI-X: Enable+ Count=8 Masked-
            Capabilities:[78] Power Management version 3
            Capabilities:[80] Express Endpoint, MSI 00
            Capabilities:[100] Virtual Channel
            Capabilities:[200] Advanced Error Reporting
            Capabilities:[280] #19
            Capabilities:[300] Latency Tolerance Reporting
            Kerneldriver in use: xhci_hcd
 
05:00.0 Ethernet controller: Qualcomm Atheros Killer E2400Gigabit Ethernet Controller (rev 10)
            Subsystem:Gigabyte Technology Co., Ltd Killer E2400 Gigabit Ethernet Controller
            Flags: busmaster, fast devsel, latency 0, IRQ 43
            Memory atfe700000 (64-bit, non-prefetchable) [size=256K]
            I/O ports atd000 [size=128]
            Capabilities:[40] Power Management version 3
            Capabilities:[58] Express Endpoint, MSI 00
            Capabilities:[c0] MSI: Enable+ Count=1/16 Maskable+ 64bit+
            Capabilities:[d8] MSI-X: Enable- Count=16 Masked-
            Capabilities:[100] Advanced Error Reporting
            Capabilities:[180] Device Serial Number ff-94-2a-87-1c-1b-0d-ff
            Kerneldriver in use: alx
            Kernelmodules: alx
 
06:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0Host Controller (rev 01) (prog-if 30 [XHCI])
            Subsystem:VIA Technologies, Inc. VL805 USB 3.0 Host Controller
            Flags: fastdevsel, IRQ 17
            Memory atfe600000 (64-bit, non-prefetchable) [size=4K]
            Capabilities:[80] Power Management version 3
            Capabilities:[90] MSI: Enable- Count=1/4 Maskable- 64bit+
            Capabilities:[c4] Express Endpoint, MSI 00
            Capabilities:[100] Advanced Error Reporting
```

---

### Post by chili555 on 2017-12-21
Here is your ethernet device:
> 05:00.0 Ethernet controller: Qualcomm Atheros Killer E2400Gigabit Ethernet Controller (rev 10)
Subsystem:Gigabyte Technology Co., Ltd Killer E2400 Gigabit Ethernet Controller
<snip>
Capabilities:[180] Device Serial Number ff-94-2a-87-1c-1b-0d-ff
Kerneldriver in use: alx
Kernelmodules: alxAs you can see, there is a driver present: alx. Is an interface created?```
ifconfig
```Are there any clues in the log?```
dmesg | grep -e alx -e 05:00
dmesg | grep -e eth -e enp
```

---

### Post by jeremy31 on 2017-12-21
I wonder if the bug is still in the alx driver where it helps to set the MTU to 8192?

---

### Post by squeeky0123 on 2017-12-24
> **chili555 said:**
> Here is your ethernet device:
As you can see, there is a driver present: alx. Is an interface created?```
ifconfig
```Are there any clues in the log?```
dmesg | grep -e alx -e 05:00
dmesg | grep -e eth -e enp
```


Here is the results of the ```
ifconfig
``` I have also found that when my IMMOU is disabled the Ethernet connects but usb connections don't so i can either have internet or keyboard and mouse. 
 
```
ifconfig
enp5s0    Linkencap:Ethernet  HWaddr1c:1b:0d:94:2a:87  
          inet6 addr:fe80::8cb:c627:a53b:4c09/64 Scope:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RXbytes:37406 (37.4 KB)  TX bytes:0 (0.0 B)
          Interrupt:16
 
lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:::1/128 Scope:Host
          UP LOOPBACKRUNNING  MTU:65536  Metric:1
          RXpackets:2668 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:2668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1
          RXbytes:198071 (198.0 KB)  TX bytes:198071(198.0 KB)

```

---

### Post by QIII on 2017-12-24
Hello!

The Gigabyte 990FX motherboards are known for their issues with IOMMU and USB 3.0 ports.  If you disable IOMMU on the motherboard and then give control to the OS, you can often get around this ill behavior.

If you still have IOMMU disabled in BIOS, then use a USB 2.0 port to connect your keyboard and mouse temporarily.

Modify the line ```
GRUB_CMDLINE_LINUX=""
``` in /etc/default/grub

to read

```
GRUB_CMDLINE_LINUX="iommu=soft"
```.

This gives the OS control over IOMMU.

Reboot with your keyboard and mouse in a USB 3.0 port and let us know how that goes.

Side note:  It's Ubuntu, not Ubunto.

---

