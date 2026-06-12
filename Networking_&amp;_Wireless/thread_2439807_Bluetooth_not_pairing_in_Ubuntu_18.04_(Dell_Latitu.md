---
title: "Bluetooth not pairing in Ubuntu 18.04 (Dell Latitude 7370)"
date: 2020-04-01
forum: Networking &amp; Wireless
---

### Post by ubuntophe on 2020-04-01
I just bought a secondhand Dell Latitude 7370 and installed Ubuntu  18.04 LTS. I'm very new with linux. My bluetooth recognises new devices  but does not pair (not with headphones, not with andoid phones). The  bluetooth "connection" button for a device in the settings (see image)  comes back automaticaly in unpaired position. My question is also on [askubuntu]("https://askubuntu.com/questions/1222960/bluetooth-not-pairing-in-ubuntu-18-04-dell-latitude-7370")

[URL="https://i.stack.imgur.com/Q2mh4.png"]printscreen bluetooth settings
[/URL]
  Output ```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```

  [HTML]6d:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Wireless 8260 [8086:0150]
    Kernel driver in use: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:5768 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0a5c:5832 Broadcom Corp. 
Bus 001 Device 003: ID 04f3:2335 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   23.069600] Bluetooth: Core ver 2.22
[   23.069627] Bluetooth: HCI device and connection manager initialized
[   23.070445] Bluetooth: HCI socket layer initialized
[   23.070447] Bluetooth: L2CAP socket layer initialized
[   23.070454] Bluetooth: SCO socket layer initialized
[   23.250769] Bluetooth: hci0: Firmware revision 0.0 build 176 week 45 2017
[   23.276708] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.276710] Bluetooth: BNEP filters: protocol multicast
[   23.276715] Bluetooth: BNEP socket layer initialized
[   47.156693] Bluetooth: RFCOMM TTY layer initialized
[   47.156700] Bluetooth: RFCOMM socket layer initialized
[   47.156705] Bluetooth: RFCOMM ver 1.11
[ 2809.123397] Bluetooth: hci0: HCI reset during shutdown failed
[    0.223112] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.370907] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    3.511195] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_27.bin (v1.27)
[   22.067513] iwlwifi 0000:6d:00.0: loaded firmware version 36.e91976c0.0 op_mode iwlmvm
[   23.250769] Bluetooth: hci0: Firmware revision 0.0 build 176 week 45 2017
bluetooth             573440  39 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth
[/HTML]  
Output [HTML]rfkill list all[/HTML]

  [HTML]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[/HTML]  
Output for [HTML]systemctl status bluetooth.service[/HTML]

  [HTML]    &#9679; bluetooth.service - Bluetooth service
       Loaded: loaded (/lib/systemd/system/bluetooth.service; disabled; vendor preset: enabled)
       Active: active (running) since Tue 2020-03-31 15:34:56 CEST; 2h 43min ago
         Docs: man:bluetoothd(8)
     Main PID: 1152 (bluetoothd)
       Status: "Running"
        Tasks: 1 (limit: 4915)
       CGroup: /system.slice/bluetooth.service
               &#9492;&#9472;1152 /usr/lib/bluetooth/bluetoothd

mar 31 17:39:35 ubuntophe bluetoothd[1152]: a2dp-sink profile connect failed for 00:02:72:EC:8C:E2: Protocol not available
mar 31 18:23:50 ubuntophe bluetoothd[1152]: Failed to set mode: Blocked through rfkill (0x12)
mar 31 18:27:02 ubuntophe bluetoothd[1152]: Failed to set mode: Blocked through rfkill (0x12)
mar 31 18:27:17 ubuntophe bluetoothd[1152]: a2dp-sink profile connect failed for 00:02:72:EC:8C:E2: Protocol not available
[/HTML]  Thank you very much for any help with that.

---

