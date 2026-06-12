---
title: "Problem with USB Bluetooth 3.0 Broadcom"
date: 2017-04-11
forum: Networking &amp; Wireless
---

### Post by darkozzie on 2017-04-11
Hello everyone!!
It's my first time here, I hope to be a long time with Ubuntu.
I have Ubuntu 16.10 and I have been testing everything I have found on the internet for the bluetooth to work. I bought it online in China. It is a Broadcom USB Bluetooth 3.0. It  worked well on windows 10. And it also worked fine on Ubuntu 12.10 (I  tried on various linux distros), but now on 16.10 it does nothing. It appears that there are no devices.
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'; uname -a
```

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Lenovo AR8152 v2.0 Fast Ethernet [17aa:3979]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo AR9285 Wireless Network Adapter (PCI-Express) [17aa:30a1]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
Bus 002 Device 006: ID 5986:0292 Acer, Inc 
Bus 002 Device 005: ID 0781:556b SanDisk Corp. 
Bus 002 Device 007: ID 04f3:0230 Elan Microelectronics Corp. 3D Optical Mouse
Bus 002 Device 003: ID 0a5c:2190 Broadcom Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.163395] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.335626] pci 0000:01:00.0: [Firmware Bug]: VPD access disabled
[    3.445271] usb 2-1.1: Product: Bluetooth V3.0 Device
[   14.578985] Bluetooth: Core ver 2.21
[   14.579011] Bluetooth: HCI device and connection manager initialized
[   14.580989] Bluetooth: HCI socket layer initialized
[   14.580993] Bluetooth: L2CAP socket layer initialized
[   14.581000] Bluetooth: SCO socket layer initialized
[   28.726871] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.726873] Bluetooth: BNEP filters: protocol multicast
[   28.726881] Bluetooth: BNEP socket layer initialized
Linux darkland 4.8.0-46-generic #49-Ubuntu SMP Fri Mar 31 13:57:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

I tried also to install the windows driver with ndiswrapper, but I did not work either. It must be because I am very noob.
I hope you can help me and especially, not back to güindow$ ... I use the bluetooth for music and for my cellphone.
PS: Sorry for my English, not very good :P

---

### Post by jeremy31 on 2017-04-11
Hopefully ndiswrapper doesn't interfere as it usually only works for wifi, check
```
modprobe -c | grep 2190
```
Post results

---

