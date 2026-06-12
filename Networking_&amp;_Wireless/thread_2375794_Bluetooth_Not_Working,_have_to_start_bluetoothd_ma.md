---
title: "Bluetooth Not Working, have to start bluetoothd manually"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by zwolfe21 on 2017-10-27
I have to start bluetoothd manually upon booth in a terminal otherwise  bluetooth panel will just state that it is off. Once bluetoothd is  started manually, it works fine and I can connect and use devices. Does  anyone have any ideas?

From hciconfig -a after starting bluetoothd 

```
hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 48:45:20:C6:87:1F  ACL MTU: 1021:5  SCO MTU: 96:6
    UP RUNNING PSCAN ISCAN 
    RX bytes:161053 acl:7430 sco:0 events:569 errors:0
    TX bytes:14985 acl:82 sco:0 commands:337 errors:0
    Features: 0xff 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'BlueZ 5.47'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.2 (0x8)  Revision: 0x1000
    LMP Version: 4.2 (0x8)  Subversion: 0x1000
    Manufacturer: Intel Corp. (2)


```

From dmesg|grep -i bluetooth after bluetoothd is started

```
dmesg|grep -i bluetooth
[    3.277148] Bluetooth: Core ver 2.22
[    3.277161] Bluetooth: HCI device and connection manager initialized
[    3.277164] Bluetooth: HCI socket layer initialized
[    3.277166] Bluetooth: L2CAP socket layer initialized
[    3.277170] Bluetooth: SCO socket layer initialized
[    3.285074] Bluetooth: HCI UART driver ver 2.3
[    3.285075] Bluetooth: HCI UART protocol H4 registered
[    3.285076] Bluetooth: HCI UART protocol BCSP registered
[    3.285076] Bluetooth: HCI UART protocol ATH3K registered
[    3.285077] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.285109] Bluetooth: HCI UART protocol Intel registered
[    3.285136] Bluetooth: HCI UART protocol Broadcom registered
[    3.285137] Bluetooth: HCI UART protocol QCA registered
[    3.285137] Bluetooth: HCI UART protocol AG6XX registered
[    3.285138] Bluetooth: HCI UART protocol Marvell registered
[    3.405976] Bluetooth: hci0: read Intel version: 370810011003110e25
[    3.405977] Bluetooth: hci0: Intel device is already patched. patch num: 25
[ 1315.390487] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 1315.390490] Bluetooth: BNEP filters: protocol multicast
[ 1315.390495] Bluetooth: BNEP socket layer initialized
[ 1315.400617] Bluetooth: RFCOMM TTY layer initialized
[ 1315.400624] Bluetooth: RFCOMM socket layer initialized
[ 1315.400631] Bluetooth: RFCOMM ver 1.11
[ 1429.673156] hid-generic 0005:046D:B018.0006: input,hidraw3: BLUETOOTH HID v0.09 Keyboard [MX Anywhere 2] on 48:45:20:C6:87:1F


```

---

