---
title: "Targus Bluetooth mouse, Iogear headphones in Dapper"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by meyrd on 2006-11-05
I would like to get my Bluetooth working in Dapper.
I plug my Targus usb Bluetooth dongle into the usb port and the light on it comes on. I grep Bluetooth and then lsusb. I get the following:

david@david-laptop:~$ dmesg |grep Bluetooth
[17179590.180000] Bluetooth: Core ver 2.8
[17179590.180000] Bluetooth: HCI device and connection manager initialized
[17179590.180000] Bluetooth: HCI socket layer initialized
[17179590.292000] Bluetooth: HCI USB driver ver 2.9
[17179614.340000] Bluetooth: L2CAP ver 2.8
[17179614.340000] Bluetooth: L2CAP socket layer initialized
[17179614.344000] Bluetooth: RFCOMM socket layer initialized
[17179614.344000] Bluetooth: RFCOMM TTY layer initialized
[17179614.344000] Bluetooth: RFCOMM ver 1.7
david@david-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 005: ID 0a5c:4503 Broadcom Corp.
Bus 002 Device 004: ID 0a5c:4502 Broadcom Corp.
Bus 002 Device 003: ID 0a5c:2100 Broadcom Corp.
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp.
Bus 002 Device 001: ID 0000:0000
david@david-laptop:~$ hciconfig up
hci0:   Type: USB
        BD Address: 00:16:38:BF:E4:54 ACL MTU: 1017:8 SCO MTU: 64:8
        UP RUNNING
        RX bytes:117 acl:0 sco:0 events:16 errors:0
        TX bytes:315 acl:0 sco:0 commands:16 errors:0

I turn my Targus Bluetooth mouse on but I can't sync. The blue light on the  dongle stays on constant and the blue light on the mouse blinks during the sync process but they don't connect.

Any thoughts or help would be appreciated. When I get these to work I want to sync my Iogear Bluetooth headphones to work with my audio playlists as well.

Thanks,
:cool:

---

### Post by meyrd on 2006-11-05
I got it to work!
I turned the mouse on and hit the connect button on the bottom at the same time as running hcitool scan and it started up and is working great.
Now for the headphones....
I will post the gear I have to the thread for hardware that works.
meyrd

---

