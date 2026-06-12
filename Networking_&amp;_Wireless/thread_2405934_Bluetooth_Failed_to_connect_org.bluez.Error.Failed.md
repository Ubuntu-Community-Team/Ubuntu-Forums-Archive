---
title: "Bluetooth Failed to connect: org.bluez.Error.Failed"
date: 2018-11-13
forum: Networking &amp; Wireless
---

### Post by thyk123 on 2018-11-13
i try to connect from Blueman and can't connected, so I tried via bluetoothctl, and show message Bluetooth Failed to connect: org.bluez.Error.Failed after attempting connection, I already install pulseaudio and module. please help

---

### Post by jeremy31 on 2018-11-13
Post results for ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'; pactl list short | grep blue
```

---

### Post by thyk123 on 2018-11-15
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000 [103c:1611]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip] [1814:539f]
	Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000 PCIe wireless card [103c:1637]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 148f:2000 Ralink Technology, Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1f75:0888 Innostor Technology Corporation IS888 SATA Storage Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    0.091153] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.123571] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[   30.544502] Bluetooth: Core ver 2.22
[   30.544555] Bluetooth: HCI device and connection manager initialized
[   30.544564] Bluetooth: HCI socket layer initialized
[   30.544569] Bluetooth: L2CAP socket layer initialized
[   30.544585] Bluetooth: SCO socket layer initialized
[   34.719910] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.719915] Bluetooth: BNEP filters: protocol multicast
[   34.719925] Bluetooth: BNEP socket layer initialized
[   35.591128] Bluetooth: RFCOMM TTY layer initialized
[   35.591145] Bluetooth: RFCOMM socket layer initialized
[   35.591158] Bluetooth: RFCOMM ver 1.11
[   40.065406] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   40.096284] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.40
9	module-bluetooth-policy		
24	module-bluetooth-discover		
25	module-bluez5-discover

---

