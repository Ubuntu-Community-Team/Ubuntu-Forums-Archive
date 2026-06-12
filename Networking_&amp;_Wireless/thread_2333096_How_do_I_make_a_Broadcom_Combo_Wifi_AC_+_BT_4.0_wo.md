---
title: "How do I make a Broadcom Combo Wifi AC + BT 4.0 work in Ubuntu?"
date: 2016-08-06
forum: Networking &amp; Wireless
---

### Post by Marcelo Ruiz on 2016-08-06
Hi, 

I have a AzureWave Broadcom BCM94352HMB/BCM94352 802.11/ac/867Mbps WLAN + BT4.0 Half Mini PCI-E Card **[14E4:43B1]** . 
The wifi works fine after installing bcmwl-kernel--source, but the Bluetooth part of the card is not recognized by Ubuntu. I tried upgrading the kernel to **Linux 4.4.14-040414-generic** but it did not help.

My computer (Toshiba **Qosmio X500** - PM55 chipset) has already a bluetooth device (Ver 2.11 + EDR) but its range is extremely limited and I would like to use the capabilities of the combo card.

The output of **lspci -nnk | grep -iA2 net; lsusb; lsmod | grep blue; dmesg | egrep -i 'blue|firm'** is:

```
0a:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: AzureWave BCM4352 802.11ac Wireless Network Adapter [1a3b:2123]
	Kernel driver in use: wl
	Kernel modules: bcma, wl
0b:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: Toshiba America Info Systems AR8131 Gigabit Ethernet [1179:ff50]
	Kernel driver in use: atl1c
	Kernel modules: atl1c
Bus 002 Device 004: ID 0930:020f Toshiba Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
toshiba_bluetooth      16384  0
bluetooth             520192  39 bnep,btbcm,btrtl,btusb,rfcomm,btintel
[    0.697606] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    7.543219] Bluetooth: Core ver 2.21
[    7.543513] Bluetooth: HCI device and connection manager initialized
[    7.543659] Bluetooth: HCI socket layer initialized
[    7.543799] Bluetooth: L2CAP socket layer initialized
[    7.543945] Bluetooth: SCO socket layer initialized
[   11.100614] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[   13.506940] Bluetooth: hci0 command 0x0c14 tx timeout
[   19.248417] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.248421] Bluetooth: BNEP filters: protocol multicast
[   19.248427] Bluetooth: BNEP socket layer initialized
[   62.464950] Bluetooth: RFCOMM TTY layer initialized
[   62.464960] Bluetooth: RFCOMM socket layer initialized
[   62.464967] Bluetooth: RFCOMM ver 1.11
```

This is the output of **lsusb**:

Bus 002 Device 004: ID 0930:020f Toshiba Corp. 
Bus 002 Device 003: ID 04f2:b130 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

There is a similar question here: [HTML]http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu[/HTML] but the solution did not work for me. Also, I am not sure as to where to get the hex file for this particular card.

Does anyone know how to make it work?

Thanks!

---

### Post by wildmanne39 on 2016-08-06
*Thread moved to **Networking & Wireless**.*

---

