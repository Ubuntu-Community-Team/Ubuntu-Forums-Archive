---
title: "Problem connecting with bluetooth"
date: 2018-11-14
forum: Networking &amp; Wireless
---

### Post by trenien2 on 2018-11-14
As it says in the title, I have a bluetooth speaker that pairs without problem with my laptop (thinkpad x260), but there seem to be no way to connect to it. Blueman gives the exact following message :
'*device added successfuly, but failed to connect*'

Each time I try to do it, it pairs, seems to connect for a couple of seconds and then fails. The most infuriating thing is that a few years back I could connect with no problem, then with 14.04, it became somewhat of a pain (I had to erase and redo the setting process), and now I just can't connect to it.
Any solution for that ?

Looking around, I've seen that at least a few other people have the same problem, and according to the instructions given, here is the result of of the following command :

[B] lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i  'blue|firm'; pactl list short | grep blue 

[/B]```

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet  Connection I219-V [8086:1570] (rev 21) 
        Subsystem: Lenovo Ethernet Connection I219-V [17aa:2233] 
        Kernel driver in use: e1000e 
        Kernel modules: e1000e 
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A  PCI Express Card Reader [10ec:522a] (rev 01) 
-- 
04:00.0 Network controller [0280]: Intel Corporation Wireless 8260  [8086:24f3] (rev 3a) 
        Subsystem: Intel Corporation Wireless 8260 [8086:1130] 
        Kernel driver in use: iwlwifi 
        Kernel modules: iwlwifi 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 002: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
[    0.028000] Spectre V2 : Enabling Restricted Speculation for firmware  calls 
[    0.053352] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored 
[    2.135392] [drm] Finished loading DMC firmware  i915/skl_dmc_ver1_26.bin (v1.26) 
[    3.220632] psmouse serio2: trackpoint: IBM TrackPoint firmware:  0x0e, buttons: 3/3 
[    5.787320] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio  is unblocked 
[    5.821419] Bluetooth: Core ver 2.22 
[    5.821434] Bluetooth: HCI device and connection manager initialized 
[    5.821436] Bluetooth: HCI socket layer initialized 
[    5.821438] Bluetooth: L2CAP socket layer initialized 
[    5.821443] Bluetooth: SCO socket layer initialized 
[    5.848905] Bluetooth: hci0: Firmware revision 0.0 build 176 week 45 2017 
[    5.874921] iwlwifi 0000:04:00.0: loaded firmware version 34.0.1  op_mode iwlmvm 
[    6.740835] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[    6.740836] Bluetooth: BNEP filters: protocol multicast 
[    6.740839] Bluetooth: BNEP socket layer initialized 
[   37.550482] Bluetooth: RFCOMM TTY layer initialized 
[   37.550487] Bluetooth: RFCOMM socket layer initialized 
[   37.550492] Bluetooth: RFCOMM ver 1.11 
[   76.023242] Bluetooth: hci0: last event is not cmd complete (0x0f) 
8       module-bluetooth-policy 
9       module-bluetooth-discover 
10      module-bluez5-discover 


```

---

