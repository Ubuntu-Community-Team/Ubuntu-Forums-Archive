---
title: "Another problem with a DWA-542"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Guardian-Mage on 2008-06-29
Ok, I am using a Dlink DWA-542 Wireless N desktop card. It works fine in Vista Ultimate x64 under the same machine. I am using Ubuntu 8.04. I have installed Mad-Wifi per the instructions on their website, and NDIS-wrappers as well as the linux-restricted-modules.

No Luck.

Results of $ sudo lspci -v
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8276
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Unknown device 8276
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b880 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bc00 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe7ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] Vendor Specific Information

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe7f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Capabilities: [a0] Power Management version 2

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Capabilities: [a0] Power Management version 2

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at b080 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b400 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b480 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fe7ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] Vendor Specific Information

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Unknown device 8277

00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9880 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9480 [size=16]
	I/O ports at 9400 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: medium devsel, IRQ 5
	Memory at fe7ff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=16]
	I/O ports at a400 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870 (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Unknown device e620
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe8e0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at c000 [size=256]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
	Subsystem: PC Partner Limited Unknown device aa18
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8226
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at fe9c0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at fe9a0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [58] Express Endpoint IRQ 0

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Unknown device 824f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feafe000 (32-bit, non-prefetchable) [size=8K]
	Expansion ROM at feae0000 [disabled] [size=64K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint IRQ 1

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 824f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Capabilities: [68] Power Management version 2

05:00.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
	Subsystem: D-Link System Inc Unknown device 3a69
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] #80 [0000]
	Capabilities: [80] #00 [0000]

05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at febef800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: [50] Power Management version 2

```

Results of lspci -nn

```

00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IB (ICH9) LPC Interface Controller [8086:2918] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller [8086:2921] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3870 [1002:9501]
01:00.1 Audio device [0403]: ATI Technologies Inc Radeon HD 3870 Audio device [1002:aa18]
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
03:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
05:00.0 Network controller [0280]: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter [168c:0023] (rev 01)
05:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev c0)

```

Any help is much appreciated. (I am using an ethernet connection right now, but it is only temporary)

---

### Post by pytheas22 on 2008-06-29
Please post the output of these commands:

```
ndiswrapper -l
iwconfig
dmesg ###it will be long but it's useful
cat /etc/modprobe.d/blacklist
iwlist scanning
```

Also, you don't really describe what's wrong.  Is the card not working at all?  Can you see wireless networks but not connect?  Please describe more specifically the problem.

---

