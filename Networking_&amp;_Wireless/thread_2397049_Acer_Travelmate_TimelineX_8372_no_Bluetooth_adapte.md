---
title: "Acer Travelmate TimelineX 8372 no Bluetooth adapter"
date: 2018-07-24
forum: Networking &amp; Wireless
---

### Post by ab2211 on 2018-07-24
I've done this [https://ubuntuforums.org/showthread.php?t=1867368](https://ubuntuforums.org/showthread.php?t=1867368). This makes the wireless wlan adapter work, but now Ubuntu doesn't find any bluetooth adapter...
Any ideas?

---

### Post by jeremy31 on 2018-07-24
Can you post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'; uname -a
```

---

### Post by ab2211 on 2018-07-25
01:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. T77H167.00 [105b:e034]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM57760 Gigabit Ethernet PCIe [14e4:1690] (rev 01)
    Subsystem: Acer Incorporated [ALI] NetXtreme BCM57760 Gigabit Ethernet PCIe [1025:043f]
    Kernel driver in use: tg3
    Kernel modules: tg3
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.052534] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[67865.267166] Bluetooth: Core ver 2.22
[67865.267203] Bluetooth: HCI device and connection manager initialized
[67865.267209] Bluetooth: HCI socket layer initialized
[67865.267211] Bluetooth: L2CAP socket layer initialized
[67865.267221] Bluetooth: SCO socket layer initialized
Linux ab2211-TravelMate-8372 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ab2211 on 2018-07-31
Bump.

---

### Post by QIII on 2018-07-31
Hello!

A bump after about 12 hours is more likely to succeed.  Waiting nearly a week and letting your thread drop off the radar leaves it where nobody will go searching for it.

Cheers!

---

### Post by jeremy31 on 2018-07-31
I don't see any sign of a bluetooth adapter in your results and I can't say it was caused by adding those modules to the blacklist

---

### Post by ab2211 on 2018-07-31
Ok, thanks! So I try to remove these lines and check again?!

---

### Post by jeremy31 on 2018-08-01
You could try that, reboot and see if any changes happen to ```
lsusb
```

---

### Post by ab2211 on 2018-08-19
I removed the code lines and now I have no wlan adapter, but bluetooth!

---

