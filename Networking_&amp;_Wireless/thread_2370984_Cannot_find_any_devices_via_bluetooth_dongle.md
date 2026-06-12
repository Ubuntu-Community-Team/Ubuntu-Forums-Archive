---
title: "Cannot find any devices via bluetooth dongle"
date: 2017-09-09
forum: Networking &amp; Wireless
---

### Post by mrakin88 on 2017-09-09
Hello everyone,

I spend about 2 hours trying to solve my problem and I would be so happy if anyone is able to help me.
I bought a new bluetooth keyboard and took my old MSI bluetooth USB dongle and connected it to my desktop PC running Xubuntu 16.04.
The fact is that I am not able to discover any device (telephone, keyboard, and some more devices, which I can see on my Windows laptop).

As I learned, these info might be useful as a starting point:
```
$ hcitool scan
Scanning ...
```
no devices found

```
$ lsusb
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```
```

$ hciconfig -a
hci0:   Type: BR/EDR  Bus: USB
        BD Address: 00:15:83:3D:0A:57  ACL MTU: 310:10  SCO MTU: 64:8
        UP RUNNING
        RX bytes:543 acl:0 sco:0 events:30 errors:0
        TX bytes:624 acl:0 sco:0 commands:27 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'marek-desktop'
        Class: 0x000104
        Service Classes: Unspecified
        Device Class: Computer, Desktop workstation
        HCI Version: 2.0 (0x3)  Revision: 0xc5c
        LMP Version: 2.0 (0x3)  Subversion: 0xc5c
        Manufacturer: Cambridge Silicon Radio (10)

```

Thanks for any hints and advices,
Marek

One more output:
```
$ dmesg | grep -i blue
[    5.584925] Bluetooth: Core ver 2.21
[    5.584945] Bluetooth: HCI device and connection manager initialized
[    5.584949] Bluetooth: HCI socket layer initialized
[    5.584951] Bluetooth: L2CAP socket layer initialized
[    5.584956] Bluetooth: SCO socket layer initialized
[    6.190013] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.190017] Bluetooth: BNEP filters: protocol multicast
[    6.190022] Bluetooth: BNEP socket layer initialized
```

---

