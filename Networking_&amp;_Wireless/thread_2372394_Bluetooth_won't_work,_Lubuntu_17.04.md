---
title: "Bluetooth won't work, Lubuntu 17.04"
date: 2017-09-24
forum: Networking &amp; Wireless
---

### Post by hronsdag on 2017-09-24
Hi!

I am relatively new to Linux and Lubuntu and while installing an old Acer Aspire 7520 I ran in to a problem.

When I try to use blutooth I get the following error message:

"Connection to BlueZ failed
Bluez daemon is not running, blueman-manager cannot continue.
This probably means there were no Bluetooth adapters
detected or Bluetooth daemon was not started."

What is wrong and how do I fix it?

---

### Post by wildmanne39 on 2017-09-26
*Thread moved to **Networking & Wireless for better a better fit**.*

---

### Post by jeremy31 on 2017-09-26
Please post results from terminal for ```
lspci -nnk | grep -iA2 net; lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by hronsdag on 2017-09-29
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP67 Ethernet [10de:054c] (rev a2)
	Subsystem: Acer Incorporated [ALI] MCP67 Ethernet [1025:0126]
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
--
05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC [1468:0428]
	Kernel driver in use: ath5k
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    2.326300] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS

---

### Post by jeremy31 on 2017-09-29
There isn't a bluetooth adapter connected from the results

---

### Post by hronsdag on 2017-09-29
Ah!

That would explain things. :D

Old thing I rescued from my parents and I thougt it had bluetooth, but on further inspection it doesn't.

---

