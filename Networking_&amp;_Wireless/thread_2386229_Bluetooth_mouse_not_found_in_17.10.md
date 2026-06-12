---
title: "Bluetooth mouse not found in 17.10"
date: 2018-03-02
forum: Networking &amp; Wireless
---

### Post by lucemferre on 2018-03-02
Hi,

My MX Anywhere 2 is not found by my computer. It does detect my smartphone and headphones. Any ideas on what might be wrong?

Info that might be relevant:

Output of rfkill list:

```
0: phy0: Wireless LAN  
    Soft blocked: no  
    Hard blocked: no  
1: hci0: Bluetooth  
    Soft blocked: no  
    Hard blocked: no  
2: hp-wifi: Wireless LAN  
    Soft blocked: no  
    Hard blocked: no  
3: hp-bluetooth: Bluetooth  
    Soft blocked: no  
    Hard blocked: no
```  

lspci -knn | grep Net -A2; lsusb:

```
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)  
    Subsystem: Hewlett-Packard Company 82579LM Gigabit Network Connection (Lewisville) [103c:161c]  
    Kernel driver in use: e1000e  
    Kernel modules: e1000e  
    --  
25:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)  
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]  
    Kernel driver in use: iwlwifi  
Bus 002 Device 004: ID 03f0:231d Hewlett-Packard Broadcom 2070 Bluetooth Combo  
Bus 002 Device 003: ID 1bcf:2805 Sunplus Innovation Technology Inc.   
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
```

dmesg | grep Blue:

```
[   13.278105] Bluetooth: Core ver 2.22  
[   13.278124] Bluetooth: HCI device and connection manager initialized  
[   13.278127] Bluetooth: HCI socket layer initialized  
[   13.278129] Bluetooth: L2CAP socket layer initialized  
[   13.278135] Bluetooth: SCO socket layer initialized  
[   25.231678] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
[   25.231679] Bluetooth: BNEP filters: protocol multicast  
[   25.231682] Bluetooth: BNEP socket layer initialized  
[   61.677491] Bluetooth: RFCOMM TTY layer initialized  
[   61.677512] Bluetooth: RFCOMM socket layer initialized  
[   61.677525] Bluetooth: RFCOMM ver 1.11  
```

---

