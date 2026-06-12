---
title: "Bluetooth woes - No adapters found!"
date: 2016-12-15
forum: Networking &amp; Wireless
---

### Post by iamunderstand on 2016-12-15
First time linux user here, just installed lubuntu a few days ago. Most things have gone well or been easily fixed with a quick google search so far, but I've come to a screeching halt at configuring bluetooth. I'm stuck.

From the taskbar I'll click the bluetooth icon -> setup new device
And I get a popup saying: Blueman Assistant: No adapters found

Running on an HP Pavillion dv5 Notebook.

---

### Post by DuckHook on 2016-12-16
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

### Post by jeremy31 on 2016-12-17
Welcome to the forums
Open a terminal window using CTRL + t and enter the following
```
uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
```

Post the results

---

### Post by iamunderstand on 2016-12-18
```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 10f1:1a16 Importek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:144e]
    Kernel driver in use: r8169
    Kernel modules: r8169
08:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z062.12 802.11bgn Wireless Half-size Mini PCIe Card [103c:3040]
    Kernel driver in use: ath9k
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.236171] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.596176] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.596393] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.603959] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-0f] only partially covers this bridge
[    2.459209] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   33.920675] Bluetooth: Core ver 2.21
[   33.920917] Bluetooth: HCI device and connection manager initialized
[   33.920922] Bluetooth: HCI socket layer initialized
[   33.920924] Bluetooth: L2CAP socket layer initialized
[   33.920931] Bluetooth: SCO socket layer initialized
[   34.004350] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.004352] Bluetooth: BNEP filters: protocol multicast
[   34.004357] Bluetooth: BNEP socket layer initialized

```

---

### Post by jeremy31 on 2016-12-18
There doesn't appear to be a bluetooth chipset in the computer

---

### Post by iamunderstand on 2016-12-19
That's strange, when I got the laptop and it had Windows installed I swear I saw the bluetooth speaker in my kitchen through spotify...

Well, I must be mistaken. Thanks for taking the time to point out such a simple oversight on my part.

---

