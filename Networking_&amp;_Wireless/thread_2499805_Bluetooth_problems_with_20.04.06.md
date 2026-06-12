---
title: "Bluetooth problems with 20.04.06"
date: 2024-08-11
forum: Networking &amp; Wireless
---

### Post by islemci on 2024-08-11
When I enter bluetooth the bluetooth tab to connect my earbuds (Galaxy Buds2), I can't see any devices because they all are named "Unknown" and says "Not Set Up", and I can't click on them.

I have a Broadcom BCM4352 wireless card, I tried running: ```
sudo apt install --reinstall bcmwl-kernel-source
```

but I couldn't fix the problem. What do you think I should do?

---

### Post by jeremy31 on 2024-08-11
Post results from terminal for ```
lsusb; sudo dmesg|egrep -i 'blue|firm'
```

---

### Post by islemci on 2024-08-11
> **jeremy31 said:**
> Post results from terminal for ```
lsusb; sudo dmesg|egrep -i 'blue|firm'
```

```
musti@LenovoYoga3Pro:~$ lsusb; sudo dmesg|egrep -i 'blue|firm'
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 048d:8386 Integrated Technology Express, Inc. ITE Device(8386)
Bus 001 Device 003: ID 1bcf:2c43 Sunplus Innovation Technology Inc. Lenovo EasyCamera
Bus 001 Device 002: ID 0489:e07a Foxconn / Hon Hai BCM20702A0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.164684] DMAR: [Firmware Bug]: No firmware reserved region can cover this RMRR [0x000000009d800000-0x000000009fffffff], contact BIOS vendor for fixes
[    0.164694] DMAR: [Firmware Bug]: Your BIOS is broken; bad RMRR [0x000000009d800000-0x000000009fffffff]
[    0.166288] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    4.496479] Bluetooth: Core ver 2.22
[    4.502510] NET: Registered PF_BLUETOOTH protocol family
[    4.502513] Bluetooth: HCI device and connection manager initialized
[    4.502518] Bluetooth: HCI socket layer initialized
[    4.502521] Bluetooth: L2CAP socket layer initialized
[    4.502530] Bluetooth: SCO socket layer initialized
[    4.744688] Bluetooth: hci0: BCM: chip id 63
[    4.745700] Bluetooth: hci0: BCM: features 0x07
[    4.761689] Bluetooth: hci0: BCM20702A
[    4.761695] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[    4.763464] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
[    4.763473] Bluetooth: hci0: BCM: 'brcm/BCM20702A1-0489-e07a.hcd'
[    4.763477] Bluetooth: hci0: BCM: 'brcm/BCM-0489-e07a.hcd'
[    6.949130] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.949136] Bluetooth: BNEP filters: protocol multicast
[    6.949141] Bluetooth: BNEP socket layer initialized
[   13.792618] Bluetooth: RFCOMM TTY layer initialized
[   13.792629] Bluetooth: RFCOMM socket layer initialized
[   13.792638] Bluetooth: RFCOMM ver 1.11
[   35.566512] audit: type=1107 audit(1723403024.578:88): pid=671 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=1738 label="snap.bitwarden.bitwarden" peer_pid=664 peer_label="unconfined"
```

---

### Post by jeremy31 on 2024-08-11
In terminal ```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-0489-e07a.hcd
```
Reboot

---

### Post by islemci on 2024-08-11
Thank you so much, it solved my problem.

---

