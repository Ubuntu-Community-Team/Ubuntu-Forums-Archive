---
title: "Trouble with Bluetooth"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by cracker on 2006-12-14
I have a USB Bluetooth adapter and a Motorola Razr V3, and I'm trying to get connected so I can get the pictures off my phone. I followed the instructions here, though most of this was already set up out of the box: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Here is the adapter in lsusb:
```
Bus 001 Device 004: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
```

The problem I'm having is that the phone won't show up. This is what happens when I have the 'Find Me' on my phone running:
```
ryan@ryana64:~$ sudo hidd --search
Searching ...
ryan@ryana64:~$ 
```

After the time has passed and it is no longer discoverable, here is what happens:
```
ryan@ryana64:~$ sudo hidd --search
Searching ...
        No devices in range or visible
ryan@ryana64:~$ 
```

So it is obviously finding my phone, but not handling it correctly. Does anyone have any ideas?\

EDIT: Here's some more info for you:
```
ryan@ryana64:~$ sudo hciconfig
hci0:   Type: USB
        BD Address: 00:11:67:0B:D9:91 ACL MTU: 678:8 SCO MTU: 64:10
        UP RUNNING PSCAN ISCAN 
        RX bytes:995 acl:0 sco:0 events:61 errors:0
        TX bytes:709 acl:0 sco:0 commands:41 errors:0

ryan@ryana64:~$ dmesg | grep Bluetooth
[17179597.216000] Bluetooth: Core ver 2.8
[17179597.216000] Bluetooth: HCI device and connection manager initialized
[17179597.216000] Bluetooth: HCI socket layer initialized
[17179597.256000] Bluetooth: L2CAP ver 2.8
[17179597.256000] Bluetooth: L2CAP socket layer initialized
[17179597.256000] Bluetooth: RFCOMM socket layer initialized
[17179597.256000] Bluetooth: RFCOMM TTY layer initialized
[17179597.256000] Bluetooth: RFCOMM ver 1.7
[17440327.916000] Bluetooth: HCI USB driver ver 2.9
[17440650.372000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1


```

---

