---
title: "How to enable Creative BT-W3 USB Bluetooth Dongle"
date: 2022-11-17
forum: Networking &amp; Wireless
---

### Post by gocanal on 2022-11-17
Hello,
I am trying to configure the Creative BT-W3 USB Bluetooth Dongle but the system can not detect the bluetooth. I read somewhere saying that we need HCI USB Bluetooth driver, how to configure the kernel if so ?

Here is some info (I am using a Raspberry Pi 4B, with Ubuntu 22.04):

> dmesg | grep -i bluetooth
[   40.220835] Bluetooth: Core ver 2.22
[   40.220920] Bluetooth: HCI device and connection manager initialized
[   40.220934] Bluetooth: HCI socket layer initialized
[   40.220944] Bluetooth: L2CAP socket layer initialized
[   40.220959] Bluetooth: SCO socket layer initialized
[   40.233673] Bluetooth: HCI UART driver ver 2.3
[   40.233685] Bluetooth: HCI UART protocol H4 registered
[   40.233740] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   40.233887] Bluetooth: HCI UART protocol Broadcom registered
[   40.386388] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.386398] Bluetooth: BNEP filters: protocol multicast
[   40.386414] Bluetooth: BNEP socket layer initialized
[ 5859.069602] Bluetooth: RFCOMM TTY layer initialized
[ 5859.069622] Bluetooth: RFCOMM socket layer initialized
[ 5859.069642] Bluetooth: RFCOMM ver 1.11

> lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 041e:3270 Creative Technology, Ltd
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> hciconfig -a
hci0:   Type: Primary  Bus: UART
        BD Address: E4:5F:01:CB:E0:01  ACL MTU: 1021:8  SCO MTU: 64:1
        UP RUNNING
        RX bytes:382170 acl:154 sco:0 events:44258 errors:0
        TX bytes:76956200 acl:86824 sco:0 commands:374 errors:0
        Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH SNIFF
        Link mode: SLAVE ACCEPT
        Name: 'name'
        Class: 0x0c041c
        Service Classes: Rendering, Capturing
        Device Class: Audio/Video, Portable Audio
        HCI Version: 5.0 (0x9)  Revision: 0x156
        LMP Version: 5.0 (0x9)  Subversion: 0x6119
        Manufacturer: Cypress Semiconductor Corporation (305)

The USB dongle is recognized :
> cat /proc/asound/cards
 0 [b1                   ]: bcm2835_hdmi - bcm2835 HDMI 1
                               bcm2835 HDMI 1
 1 [Headphones     ]: bcm2835_headpho - bcm2835 Headphones
                               bcm2835 Headphones
 5 [BTW3              ]: USB-Audio - Creative BT-W3
                               Creative Technology Ltd Creative BT-W3 at usb-0000:01:00.0-1.4, full speed


Additional info:
> systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2022-11-17 09:27:56 UTC; 15h ago
     Docs: man:bluetoothd(8)
 Main PID: 13646 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 2128)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;13646 /usr/lib/bluetooth/bluetoothd


Nov 17 09:27:56 room bluetoothd[13646]: Bluetooth daemon 5.50
Nov 17 09:27:56 room  bluetoothd[13646]: Unknown key AutoConnectTimeout for group General in
Nov 17 09:27:56 room systemd[1]: Started Bluetooth service.
Nov 17 09:27:56 room bluetoothd[13646]: Starting SDP server
Nov 17 09:27:56 room bluetoothd[13646]: Bluetooth management interface 1.18 initialized
Nov 17 09:27:56 room bluetoothd[13646]: Sap driver initialization failed.
Nov 17 09:27:56 room bluetoothd[13646]: sap-server: Operation not permitted (1)
Nov 17 09:27:56 room bluetoothd[13646]: Failed to set privacy: Rejected (0x0b)
Nov 17 09:27:56 room bluetoothd[13646]: Endpoint registered: sender=:1.61 path=/MediaEndpoi
Nov 17 09:27:56 room bluetoothd[13646]: Endpoint registered: sender=:1.61 path=/MediaEndpoi




The kernel is  5.10.92-v7l+ (I also tested on another Pi : [COLOR=#22231F][FONT=&amp]5.15.0-1017-raspi)

many thanks !

[/FONT][/COLOR]

---

### Post by jeremy31 on 2022-11-18
You might just need to follow these instructions [https://askubuntu.com/a/1404378/300665](https://askubuntu.com/a/1404378/300665)

---

### Post by gocanal on 2022-11-18
Thank you for the link. I installed and rebooted, still not detected.

---

### Post by jeremy31 on 2022-11-19
It looks like it works as hciconfig shows the status as up but it also looks to be limited to audio/video

---

