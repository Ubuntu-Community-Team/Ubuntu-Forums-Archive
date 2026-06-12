---
title: "hcitool"
date: 2018-05-11
forum: Networking &amp; Wireless
---

### Post by idkwhatimdoing1.0 on 2018-05-11
Hi, I am trying to see the active devices around me. My Bluetooth is on and everything is working. However when I do hcitool scan it just says scanning... and then nothing shows up and all it does is just open a new line to enter. This does the same thing for inq (inquiring). DOes anyone have any idea how to fix this? even the hcitool lescan doesn't work... And i don't know what to do. My hci0 is up as well.

---

### Post by jeremy31 on 2018-05-11
Post results from terminal for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by idkwhatimdoing1.0 on 2018-05-11
```
root@havefun:~# hcitool scan
Scanning ...
root@havefun:~# hcitool scan
Scanning ...
root@havefun:~# lsusb; dmesg | egrep -i 'blue|firm'
Bus 002 Device 003: ID 0a5c:21e1 Broadcom Corp. HP Portable SoftSailing
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0461:4dfe Primax Electronics, Ltd 
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. VFS491
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.068814] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   19.132671] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   19.203858] iwlwifi 0000:25:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   19.203867] iwlwifi 0000:25:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   19.930181] iwlwifi 0000:25:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   20.934117] Bluetooth: Core ver 2.22
[   20.934131] Bluetooth: HCI device and connection manager initialized
[   20.934133] Bluetooth: HCI socket layer initialized
[   20.934135] Bluetooth: L2CAP socket layer initialized
[   20.934139] Bluetooth: SCO socket layer initialized
[   25.321094] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.321095] Bluetooth: BNEP filters: protocol multicast
[   25.321098] Bluetooth: BNEP socket layer initialized
[   59.101429] Bluetooth: RFCOMM TTY layer initialized
[   59.101434] Bluetooth: RFCOMM socket layer initialized
[   59.101439] Bluetooth: RFCOMM ver 1.11
[  136.196417] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  351.157828] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  362.798741] Bluetooth: hci0: last event is not cmd complete (0x0f)
```

---

