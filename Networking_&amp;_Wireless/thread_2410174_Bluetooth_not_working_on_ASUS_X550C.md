---
title: "Bluetooth not working on ASUS X550C"
date: 2019-01-11
forum: Networking &amp; Wireless
---

### Post by macacol on 2019-01-11
[COLOR=#000000][FONT=monospace]I've been searching in this forum how to enable bluetooth in an ASUS X550C, but I haven't find the exact same problem, seems that everybody have different versions (X550CA, X550LC, etc)

I ran this command for you to check:

lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'[/FONT][/COLOR]
```
[FONT=monospace]03:00.0 [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work controller [0280]: Qualcomm Atheros AR9485 Wireless [/COLOR][COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [168c:0032] (rev 0[/COLOR]
1)
        Subsystem: AzureWave AR9485 Wireless [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [1a3b:2c97][/COLOR]
        Kernel driver in use: ath9k
        Kernel modules: ath9k
[COLOR=#18B2B2]--[/COLOR]
04:00.2 Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Giga[/COLOR]
bit Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [10ec:8168] (rev 0a)[/COLOR]
        Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [10[/COLOR]
43:200f]
        Kernel driver in use: r8169
        Kernel modules: r8169
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:5606 Realtek Semiconductor Corp.  
Bus 001 Device 003: ID 13d3:3362 IMC Networks Atheros AR3012 Bluetooth 4.0 Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc.  
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 045e:07a5 Microsoft Corp. Wireless Receiver 1461C
Bus 003 Device 004: ID 046d:0a38 Logitech, Inc. Headset H340
Bus 003 Device 003: ID 056e:0072 Elecom Co., Ltd Mouse
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:   Type: Primary  Bus: USB
        BD Address: 24:0A:64:89:B4:A6  ACL MTU: 1022:8  SCO MTU: 183:5
        DOWN  
        RX bytes:68 acl:0 sco:0 events:6 errors:0
        TX bytes:18 acl:0 sco:0 commands:11 errors:5
        Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x87
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3  
        Link policy:  
        Link mode: SLAVE ACCEPT  

[    0.040514] Spectre V2 : Enabling Restricted Speculation for [COLOR=#FF5454]**firm**[/COLOR][COLOR=#000000]ware calls[/COLOR]
[    0.204192] ACPI: [[COLOR=#FF5454]**Firm**[/COLOR][COLOR=#000000]ware Bug]: BIOS _OSI(Linux) query ignored[/COLOR]
[    2.710262] usb 1-1.1: Product: [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth USB Host Controller[/COLOR]
[    3.139419] psmouse serio4: elantech: assuming hardware version 4 (with [COLOR=#FF5454]**firm**[/COLOR][COLOR=#000000]ware version 0x361f03)[/COLOR]
[   52.074867] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: Core ver 2.22[/COLOR]
[   52.074889] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: HCI device and connection manager initialized[/COLOR]
[   52.074892] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: HCI socket layer initialized[/COLOR]
[   52.074894] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: L2CAP socket layer initialized[/COLOR]
[   52.074900] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: SCO socket layer initialized[/COLOR]
[   54.652053] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: hci0: command 0x0c14 tx timeout[/COLOR]
[   56.668051] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: hci0: command 0x0c25 tx timeout[/COLOR]
[   58.684056] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: hci0: command 0x0c38 tx timeout[/COLOR]
[   60.700059] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: hci0: command 0x0c39 tx timeout[/COLOR]
[   62.716059] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: hci0: command tx timeout[/COLOR]
[  137.279089] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: BNEP (Ethernet Emulation) ver 1.3[/COLOR]
[  137.279091] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: BNEP filters: protocol multicast[/COLOR]
[  137.279096] [COLOR=#FF5454]**Blue**[/COLOR][COLOR=#000000]tooth: BNEP socket layer initialized[/COLOR]
[/FONT]
```

Thanks for any help

---

### Post by macacol on 2019-01-19
Any help welcome

---

### Post by jeremy31 on 2019-01-19
Try blacklisting the modules
```
echo "blacklist ath3k" | sudo tee /etc/modprobe.d/bluetooth.conf
echo "blacklist btusb" | sudo tee -a /etc/modprobe.d/bluetooth.conf
```

Reboot and then do
```
sudo modprobe ath3k
sudo modprobe btusb
```

---

