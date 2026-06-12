---
title: "selecting which bluetooth device"
date: 2022-01-17
forum: Networking &amp; Wireless
---

### Post by buill on 2022-01-17
hi i have a latitude e6420 with built in bluetooth 4.0 but it has insufficiant range so i bought a bluetooth 5.0 usb bluetooth but am unable to get it working lsusb sees it as "Realtek Semiconductor Corp." but when i launch bluetooth manager it uses the built in bluetooth 4.0 and if i dissconnect it with the switch on the side of the laptop then the manager tells me to enable bluetooth. how can i tell ubuntu to use the usb not the builth in bluetooth? -i cant remove the bluetooth physically as the bluetooth and wifi card are 1. thanks and sorry if this is in the wrong section.

output from bt-adapter -l only list the builth in bluetooth
Available adapters:
admin-Lat (9C:B7:0D:AA:5E:40)

output from ~$ hciconfig --all
hci1:    Type: Primary  Bus: USB
    BD Address: 9C:B7:0D:AA:5E:40  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:755 acl:0 sco:0 events:60 errors:0
    TX bytes:4895 acl:0 sco:0 commands:60 errors:0
    Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'med1a'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x1000
    LMP Version: 4.0 (0x6)  Subversion: 0x220e
    Manufacturer: Broadcom Corporation (15)

hci0:    Type: Primary  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:21 acl:0 sco:0 events:2 errors:0
    TX bytes:6 acl:0 sco:0 commands:2 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 



kind regards buill

---

### Post by buill on 2022-01-17
in case it of use to others you have to download and copy config files to directory here is download links and tutorial to do so

[https://linuxreviews.org/Realtek_RTL8761B](https://linuxreviews.org/Realtek_RTL8761B)

---

