---
title: "Issue with bluetooth"
date: 2014-04-01
forum: Networking &amp; Wireless
---

### Post by jerome7 on 2014-04-01
Hello,
I bought a new PC (Toshiba Satellite PRO C50-A-1L6) and the bluetooth seems to be ok, but I can't connect with any devices. I tried with my phone or audio headset, but it didn't work...
All devices are "visible" and I launch a discover on the phone and on the PC, but any device don't sees the other...

The dmesg is
```
jerome@portabel:~$ dmesg | grep tooth
[    9.547727] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[    9.552202] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[    9.583761] Bluetooth: Core ver 2.16
[    9.583776] Bluetooth: HCI device and connection manager initialized
[    9.583784] Bluetooth: HCI socket layer initialized
[    9.583786] Bluetooth: L2CAP socket layer initialized
[    9.583790] Bluetooth: SCO socket layer initialized
[   13.627907] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.627910] Bluetooth: BNEP filters: protocol multicast
[   13.627917] Bluetooth: BNEP socket layer initialized
[   13.628974] Bluetooth: RFCOMM TTY layer initialized
[   13.628982] Bluetooth: RFCOMM socket layer initialized
[   13.628983] Bluetooth: RFCOMM ver 1.11
```

The rfkill :
```
jerome@portabel:~$ rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

I tried to launch a hcidump in the same time I launch a hcitool scan and this is the result
```
HCI sniffer - Bluetooth packet analyzer ver 2.5
device: hci0 snap_len: 1500 filter: 0xffffffffffffffff
> HCI Event: Command Status (0x0f) plen 4
    Inquiry (0x01|0x0001) status 0x00 ncmd 1
> HCI Event: Inquiry Complete (0x01) plen 1
    status 0x00
```

Can you help me ?
Thank you.

---

