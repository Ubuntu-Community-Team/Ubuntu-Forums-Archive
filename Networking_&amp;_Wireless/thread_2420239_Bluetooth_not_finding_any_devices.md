---
title: "Bluetooth not finding any devices"
date: 2019-06-01
forum: Networking &amp; Wireless
---

### Post by arci996 on 2019-06-01
Hello, I'm writing here because I can't manage to pair my headphones since bluetooth doesn't find any device when scannig (tried with different devices to no avail). I have a Lenovo B50-10 that uses a Realtek RTL8723BE as its network/bluetooth adapter, wifi works fine, the bluetooth adapter is detected by the OS but when I search for devices no results show up so I can't pair my headphones (Sony WH1000xm3, don't know if it's relevant). I'm running KDE Neon but I'm posting here since the community seems more active and, as I understand it, it shouldn't make much of a difference, if it's against some rule I apologize.

Looking at other discussions on this topic it seems this should be useful:
```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 0a)
        Subsystem: Lenovo RTL810xE PCI Express Fast Ethernet controller [17aa:3830]
        Kernel driver in use: r8169
        Kernel modules: r8169
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
        Subsystem: XAVi Technologies Corp. RTL8723BE PCIe Wireless Network Adapter [1b9a:2485]
        Kernel driver in use: rtl8723be
        Kernel modules: rtl8723be
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b49f Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 174f:1169 Syntek 
Bus 002 Device 007: ID 2a70:4ee7  
Bus 002 Device 002: ID 06a3:0ccb Saitek PLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:   Type: Primary  Bus: USB
        BD Address: B0:C0:90:0A:31:C6  ACL MTU: 820:8  SCO MTU: 255:16
        UP RUNNING PSCAN ISCAN 
        RX bytes:44747 acl:0 sco:0 events:8011 errors:0
        TX bytes:54408 acl:0 sco:0 commands:6687 errors:0
        Features: 0xff 0xff 0xff 0xfe 0xdb 0xff 0x7b 0x87
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'lorenzo-Lenovo-B50-10'
        Class: 0x1c010c
        Service Classes: Rendering, Capturing, Object Transfer
        Device Class: Computer, Laptop
        HCI Version: 4.0 (0x6)  Revision: 0xb
        LMP Version: 4.0 (0x6)  Subversion: 0x8723
        Manufacturer: Realtek Semiconductor Corporation (93)

[    0.020000] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.068376] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.307873] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    4.315707] [Firmware Bug]: No valid trip found
[    5.797325] usb 2-4: Product: Bluetooth Radio 
[   10.362217] Bluetooth: Core ver 2.22
[   10.362274] Bluetooth: HCI device and connection manager initialized
[   10.362282] Bluetooth: HCI socket layer initialized
[   10.362286] Bluetooth: L2CAP socket layer initialized
[   10.362304] Bluetooth: SCO socket layer initialized
[   11.123070] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[   12.131727] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.131730] Bluetooth: BNEP filters: protocol multicast
[   12.131737] Bluetooth: BNEP socket layer initialized
[   20.311727] Bluetooth: RFCOMM TTY layer initialized
[   20.311743] Bluetooth: RFCOMM socket layer initialized
[   20.311753] Bluetooth: RFCOMM ver 1.11


```

I hope you can help me and I thank you in advance.

---

### Post by LwIh%*7 on 2019-06-02
Could this help:

[https://medium.com/@overcode/fixing-bluetooth-in-ubuntu-pop-os-18-04-d4b8dbf7ddd6](https://medium.com/@overcode/fixing-bluetooth-in-ubuntu-pop-os-18-04-d4b8dbf7ddd6)

---

