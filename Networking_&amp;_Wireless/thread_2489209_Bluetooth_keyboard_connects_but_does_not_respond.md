---
title: "Bluetooth keyboard connects but does not respond"
date: 2023-07-21
forum: Networking &amp; Wireless
---

### Post by mikeubell on 2023-07-21
I am running 5.19.0-46-generic on an XDO pico-pc.  I have a wireless folding keyboard from XDO which works when connected to my Mac or iPad.  When I pair it with Ubuntu I see the keyboard Not Set Up.  Clicking on that it connects but no keystrokes make to any app (e.g. Terminal).  If I double click on Connected I get a window showing the keyboard paired, its address and an option to go to Keyboard Settings.

Given other threads in the forum I tried this:
```
# lsusb;dmesg | egrep -i 'blue|firm';hiconfig -aBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    3.868440] Bluetooth: Core ver 2.22
[    3.868982] NET: Registered PF_BLUETOOTH protocol family
[    3.868985] Bluetooth: HCI device and connection manager initialized
[    3.868992] Bluetooth: HCI socket layer initialized
[    3.868995] Bluetooth: L2CAP socket layer initialized
[    3.869004] Bluetooth: SCO socket layer initialized
[    3.907053] iwlwifi 0000:01:00.0: loaded firmware version 29.4063824552.0 7265D-29.ucode op_mode iwlmvm
[    4.038864] Bluetooth: hci0: Legacy ROM 2.5 revision 1.0 build 3 week 17 2014
[    4.040748] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    4.119822] iwlwifi 0000:01:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    4.393896] Bluetooth: hci0: Intel BT fw patch 0x32 completed & activated
[    4.534940] i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/glk_dmc_ver1_04.bin (v1.4)
[    5.442763] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.442770] Bluetooth: BNEP filters: protocol multicast
[    5.442784] Bluetooth: BNEP socket layer initialized
[    6.652376] Bluetooth: RFCOMM TTY layer initialized
[    6.652391] Bluetooth: RFCOMM socket layer initialized
[    6.652406] Bluetooth: RFCOMM ver 1.11
[  256.019351] Bluetooth: hci0: Opcode 0x 401 failed: -16
[  392.420177] Bluetooth: hci0: Opcode 0x 401 failed: -16
[  632.809300] Bluetooth: hci0: Opcode 0x 401 failed: -16
[ 3582.862848] Bluetooth: hci0: Opcode 0x 401 failed: -16
[ 3587.103834] Bluetooth: hci0: Opcode 0x 401 failed: -16
[ 3682.210971] Bluetooth: hci0: Opcode 0x 401 failed: -16
Command 'hiconfig' not found, did you mean:
  command 'hciconfig' from snap bluez (5.48-4)

```

Any suggestions on next steps?

---

