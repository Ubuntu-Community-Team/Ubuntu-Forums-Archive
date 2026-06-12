---
title: "bluetooth stopped working Ubuntu 14.04"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by raffi_1970 on 2016-01-29
Any suggestions?
I'm running 14.04 on an ASUS X550.

It has been working more or less fine. Once it gave me trouble with my Photive headset. So, I uninstalled the headset and re-paired it. But now, it won't even see the headset. Also, it pairs with my Android phone but you can't really send stuff back and forth between the two.

Thanks~

---

### Post by raffi_1970 on 2016-01-29
when I run lsusb, i get

Bus 002 Device 002: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


when i run hciconfig

hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1A:7D:DA:71:05  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN INQUIRY 
	RX bytes:2285 acl:0 sco:0 events:335 errors:0
	TX bytes:2763 acl:0 sco:0 commands:286 errors:1


output from hciconfig -a hci0

Type: BR/EDR  Bus: USB
	BD Address: 00:1A:7D:DA:71:05  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN INQUIRY 
	RX bytes:2285 acl:0 sco:0 events:335 errors:0
	TX bytes:2763 acl:0 sco:0 commands:285 errors:1
	Features: 0xff 0xff 0x8f 0xfe 0xdb 0xff 0x5b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Connection timed out (110)

---

### Post by raffi_1970 on 2016-01-29
I ran this

uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i [COLOR=#417394]bluetooth[/COLOR]; dmesg | grep -i firmware; lsmod | grep [COLOR=#417394]bluetooth

output:    Linux raffi-X550EA 3.16.0-59-generic #79~14.04.1-Ubuntu SMP Mon Jan 18 15:41:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave Device [1a3b:1186]
	Kernel driver in use: ath9k
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169
Bus 002 Device 002: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   13.940675] Bluetooth: Core ver 2.19
[   13.940748] Bluetooth: HCI device and connection manager initialized
[   13.940772] Bluetooth: HCI socket layer initialized
[   13.940782] Bluetooth: L2CAP socket layer initialized
[   13.940827] Bluetooth: SCO socket layer initialized
[   17.781201] Bluetooth: RFCOMM TTY layer initialized
[   17.781233] Bluetooth: RFCOMM socket layer initialized
[   17.781253] Bluetooth: RFCOMM ver 1.11
[   18.103547] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.103559] Bluetooth: BNEP filters: protocol multicast
[   18.103581] Bluetooth: BNEP socket layer initialized
[ 4250.417987] Bluetooth: hci0 command 0x0c01 tx timeout
[ 9519.590790] Bluetooth: hci0 command 0x0c14 tx timeout
[ 9842.287579] Bluetooth: hci0 command 0x0402 tx timeout
[ 9897.375823] Bluetooth: hci0 command 0x0405 tx timeout
[ 9937.390893] Bluetooth: hci0 command 0x0408 tx timeout
[11245.611549] init: bluetooth main process ended, respawning
[11251.799574] init: bluetooth main process ended, respawning
[    0.415870] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.533388] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    3.371473] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   13.643453] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   15.006447] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
bluetooth             446409  22 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth





[/COLOR]

---

