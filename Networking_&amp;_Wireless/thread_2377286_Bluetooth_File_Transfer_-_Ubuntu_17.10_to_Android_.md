---
title: "Bluetooth File Transfer - Ubuntu 17.10 to Android 8.0"
date: 2017-11-11
forum: Networking &amp; Wireless
---

### Post by andypi on 2017-11-11
I'm trying to transfer files to my phone (Nexus 6P - Android 8.0) from Ubuntu 17.10, but when I pair the laptop and phone, I don't think it's pairing in a way which permits file transfers. When I pair, my phone gives me a checkbox "Allow xx to access your contacts and call history", but there is no option to allow file transfers.

Then, when I attempt to transfer a file via Bluetooth from Ubuntu the transfer fails and I get the message "There was an error". My phone doesn't seem to recognise there's been any attempt to send a file.

Any ideas what's going on?

---

### Post by jeremy31 on 2017-11-11
Can you post the results from terminal for ```
lsusb; dmesg | egrep -i 'blue|firm'
```
I will try later with my Nexus 6P and 17.10 but I know I have done it with Ubuntu 16.04 and the Nexus

---

### Post by andypi on 2017-11-11
```

lsusb; dmesg | egrep -i 'blue|firm'
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
Bus 002 Device 007: ID 04f3:016f Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments Invensense Embedded MotionApp HID Sensor
Bus 002 Device 002: ID 8087:07dc Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.097575] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    8.818710] Bluetooth: Core ver 2.22
[    8.818726] Bluetooth: HCI device and connection manager initialized
[    8.818728] Bluetooth: HCI socket layer initialized
[    8.818730] Bluetooth: L2CAP socket layer initialized
[    8.818736] Bluetooth: SCO socket layer initialized
[    8.860578] Bluetooth: hci0: read Intel version: 370710018002030d00
[    8.862421] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    8.872918] iwlwifi 0000:01:00.0: loaded firmware version 17.459231.0 op_mode iwlmvm
[    9.021572] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    9.373495] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.373496] Bluetooth: BNEP filters: protocol multicast
[    9.373500] Bluetooth: BNEP socket layer initialized
[   23.557841] Bluetooth: RFCOMM TTY layer initialized
[   23.557847] Bluetooth: RFCOMM socket layer initialized
[   23.557852] Bluetooth: RFCOMM ver 1.11
[  688.575934] Bluetooth: hci0: read Intel version: 370710018002030d00
[  688.575943] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[  688.757988] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[59009.943864] Bluetooth: hci0: read Intel version: 370710018002030d00
[59009.943964] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[59010.099817] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated

```

---

### Post by jeremy31 on 2017-11-11
I am having issues getting it to work.  I would file a bug report at bugs.launchpad.net/ubuntu against package bluez

---

### Post by andypi on 2017-11-11
OK will do. Thanks very much for looking into it.

---

