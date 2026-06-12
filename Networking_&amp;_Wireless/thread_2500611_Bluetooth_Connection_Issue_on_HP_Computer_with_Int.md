---
title: "Bluetooth Connection Issue on HP Computer with Intel Killer Wi-Fi 6E AX1675 Network A"
date: 2024-09-06
forum: Networking &amp; Wireless
---

### Post by divyadarsi on 2024-09-06
Hello Everyone,


I am facing an issue with my HP computer running Ubuntu. I have installed an Intel Killer Wi-Fi 6E AX1675 network adapter (PCIe – 802.11ax with Bluetooth 5.3).


**Problem**:

I can connect to Wi-Fi without issues, but I'm having trouble with the Bluetooth functionality. Specifically:

[LIST]
[*]The Bluetooth toggle switch does not work. It shows **"No Bluetooth found. Plug in a dongle to use Bluetooth"**, even though I have a built-in Bluetooth adapter.
[*]I have tried pairing my AirPods (Bluetooth is on), but the system still does not recognize any Bluetooth device.
[/LIST]

**What I’ve Tried**:



[LIST]
[*]I checked my wired headset with a dongle, and it works fine.
[*]However, I still get the message that no Bluetooth is available and can't toggle it on/off.
[/LIST]

I would like to use wireless Bluetooth, and any assistance with resolving this issue would be greatly appreciated.

Thanks in advance for your help!

---

### Post by jeremy31 on 2024-09-06
Please post results from terminal for ```
lsusb; sudo dmesg|egrep -i 'blue|firm'
```

---

### Post by divyadarsi on 2024-09-06
Hello,

Please find the details

**divyad:~$ lsusb**
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0b0e:245d GN Netcom Jabra Link 370
Bus 001 Device 003: ID 0d62:3f41 Darfon Electronics Corp. HP Wired Desktop 320K Keyboard
Bus 001 Device 002: ID 03f0:584a HP, Inc HP 125 USB Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**divyad:~$ sudo dmesg|egrep -i 'blue|firm'**
[    0.442081] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    3.240881] iwlwifi 0000:04:00.0: loaded firmware version 86.fb5c9aeb.0 ty-a0-gf-a0-86.ucode op_mode iwlmvm
[    3.544257] i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/adls_dmc_ver2_01.bin (v2.1)
[    3.553253] i915 0000:00:02.0: [drm] GT0: GuC firmware i915/tgl_guc_70.bin version 70.5.1
[    3.553257] i915 0000:00:02.0: [drm] GT0: HuC firmware i915/tgl_huc.bin version 7.9.3
[  737.043391] Bluetooth: Core ver 2.22
[  737.043407] NET: Registered PF_BLUETOOTH protocol family
[  737.043408] Bluetooth: HCI device and connection manager initialized
[  737.043411] Bluetooth: HCI socket layer initialized
[  737.043412] Bluetooth: L2CAP socket layer initialized
[  737.043413] Bluetooth: SCO socket layer initialized
[  775.000711] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  775.000714] Bluetooth: BNEP filters: protocol multicast
[  775.000717] Bluetooth: BNEP socket layer initialized

---

### Post by jeremy31 on 2024-09-06
Can you post pictures of both sides of the wifi card and post?

---

### Post by divyadarsi on 2024-09-06
Hello,

Please find the Wificard attached

---

### Post by jeremy31 on 2024-09-06
There should have been a cord that is supposed to be connected from the wifi card to the motherboard for the bluetooth to work

---

### Post by divyadarsi on 2024-09-06
Hello,

Yes, You are Correct !! The Cord was missing. 

We are working to get it connected.

Thank you for your guidance.

---

