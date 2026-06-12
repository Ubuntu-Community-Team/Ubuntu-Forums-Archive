---
title: "Tp_link Bluetooth USB adapter working but not working on Ubuntu 21.10"
date: 2021-10-20
forum: Networking &amp; Wireless
---

### Post by gwendydd on 2021-10-20
I have just bought a Tp-link bluetooth 5.0 usb adapter (UB500), I've checked and its chip is Realtek RTL8761B
It works just fine on Windows 10, but I'm having problems on Ubuntu. 
I'm running Ubuntu 21.10 and I've just upgraded to the latest stable kernel version: 5.14.14
Before upgrading I tried [this solution]("https://linuxreviews.org/Realtek_RTL8761B") but with no success.

Now the problem I'm experiencing is that **the adapter seems to be correctly installed and properly working, however scanning does not pick up any bluetooth device**. I've tried two headsets (that I know are properly working) and my phone, with no success. When performing a scan on my phone, the computer doesn't show up, even if I've set it to visible.

I can't figure out what the problem is.

```
dmesg |grep -i bluetooth
[    3.596913] Bluetooth: Core ver 2.22
[    3.596935] NET: Registered PF_BLUETOOTH protocol family
[    3.596936] Bluetooth: HCI device and connection manager initialized
[    3.596939] Bluetooth: HCI socket layer initialized
[    3.596941] Bluetooth: L2CAP socket layer initialized
[    3.596945] Bluetooth: SCO socket layer initialized
[   93.519895] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   93.519899] Bluetooth: BNEP filters: protocol multicast
[   93.519903] Bluetooth: BNEP socket layer initialized
[  144.060814] Bluetooth: RFCOMM TTY layer initialized
[  144.060821] Bluetooth: RFCOMM socket layer initialized
[  144.060825] Bluetooth: RFCOMM ver 1.11
```
```
hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: E8:48:B8:C8:20:00  ACL MTU: 1021:6  SCO MTU: 255:12
    UP RUNNING 
    RX bytes:4264 acl:0 sco:0 events:560 errors:0
    TX bytes:9000 acl:0 sco:0 commands:490 errors:0
    Features: 0xff 0xff 0xff 0xfe 0xdb 0xfd 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'gaia-ubuntu-desktop'
    Class: 0x7c0104
    Service Classes: Rendering, Capturing, Object Transfer, Audio, Telephony
    Device Class: Computer, Desktop workstation
    HCI Version: 5.1 (0xa)  Revision: 0xb
    LMP Version: 5.1 (0xa)  Subversion: 0x8761
    Manufacturer: Realtek Semiconductor Corporation (93)
```
```
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```
```
lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 003 Device 004: ID 046d:0826 Logitech, Inc. HD Webcam C525
Bus 003 Device 003: ID 04b8:013d Seiko Epson Corp. Epson Perfection V39
Bus 003 Device 002: ID 0c76:2068 JMTek, LLC. USB MIC-SG01
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 2357:0604 TP-Link TP%Link UB500 Adapter
Bus 001 Device 002: ID 062a:3633 MosArt Semiconductor Corp. Full-Speed Mouse
Bus 001 Device 004: ID 145f:0176 Trust Isla Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by gwendydd on 2021-10-26
Solved the problem thanks to this answer: [https://askubuntu.com/a/1371453/1492321](https://askubuntu.com/a/1371453/1492321)

---

