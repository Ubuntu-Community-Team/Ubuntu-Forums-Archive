---
title: "Need help getting bluetooth to work"
date: 2019-03-04
forum: Networking &amp; Wireless
---

### Post by ubuqtu2 on 2019-03-04
[COLOR=#242729][FONT=Arial]I have a nuvision [/FONT][/COLOR][COLOR=#242729][FONT=Arial]TM800W610L [/FONT][/COLOR][COLOR=#242729][FONT=Arial]tablet I can't figure out how to get bluetooth to work. It appears to me that may have to do with the Bluetooth Address? Anyone know any solutions as I'm new to ubuntu and linux in general. Here's all the information I could gather.

[/FONT][/COLOR]```
hci0:   Type: Primary  Bus: UART
    BD Address: AA:AA:AA:AA:AA:AA  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:7742 acl:0 sco:0 events:661 errors:0
    TX bytes:11959 acl:0 sco:0 commands:606 errors:0
    Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'poketab'
    Class: 0x1c0104
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Desktop workstation
    HCI Version: 4.1 (0x7)  Revision: 0x0
    LMP Version: 4.1 (0x7)  Subversion: 0x2122
    Manufacturer: Broadcom Corporation (15)

~$ bluetoothd -v
5.50


~$ lspci -knn | grep Net -A3; lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0101:0007  
Bus 001 Device 003: ID 1a2c:0002 China Resource Semico Co., Ltd 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

~$ dmesg | grep -i blue
[    5.411742] Bluetooth: Core ver 2.22
[    5.411794] Bluetooth: HCI device and connection manager initialized
[    5.411803] Bluetooth: HCI socket layer initialized
[    5.411807] Bluetooth: L2CAP socket layer initialized
[    5.411823] Bluetooth: SCO socket layer initialized
[    5.482040] Bluetooth: HCI UART driver ver 2.3
[    5.482045] Bluetooth: HCI UART protocol H4 registered
[    5.482047] Bluetooth: HCI UART protocol BCSP registered
[    5.482127] Bluetooth: HCI UART protocol LL registered
[    5.482130] Bluetooth: HCI UART protocol ATH3K registered
[    5.482132] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    5.482253] Bluetooth: HCI UART protocol Intel registered
[    5.483251] Bluetooth: HCI UART protocol Broadcom registered
[    5.483305] Bluetooth: HCI UART protocol QCA registered
[    5.483308] Bluetooth: HCI UART protocol AG6XX registered
[    5.483310] Bluetooth: HCI UART protocol Marvell registered
[    5.522391] Bluetooth: hci0: BCM: failed to write clock (-56)
[    5.522401] Bluetooth: hci0: Failed to set baudrate
[    5.647291] Bluetooth: hci0: BCM: chip id 94
[    5.651881] Bluetooth: hci0: BCM: features 0x2e
[    5.675326] Bluetooth: hci0: 4343A0
[    5.675337] Bluetooth: hci0: BCM4343A0 (001.001.034) build 0000
[    5.763779] bluetooth hci0: Direct firmware load for brcm/BCM4343A0.hcd failed with error -2
[    5.763789] Bluetooth: hci0: BCM: Patch brcm/BCM4343A0.hcd not found
[    9.769036] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.769040] Bluetooth: BNEP filters: protocol multicast
[    9.769050] Bluetooth: BNEP socket layer initialized
[   13.773243] audit: type=1400 audit(1551680978.039:62): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1344 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   13.775195] audit: type=1400 audit(1551680978.039:63): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1344 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   13.921521] audit: type=1400 audit(1551680978.187:64): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1386 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   14.085860] audit: type=1400 audit(1551680978.351:65): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1423 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   14.087265] audit: type=1400 audit(1551680978.351:66): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1423 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   19.789900] Bluetooth: RFCOMM TTY layer initialized
[   19.789917] Bluetooth: RFCOMM socket layer initialized
[   19.789935] Bluetooth: RFCOMM ver 1.11
```

---

