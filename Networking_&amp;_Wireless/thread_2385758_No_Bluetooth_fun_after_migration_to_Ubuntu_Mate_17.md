---
title: "No Bluetooth fun after migration to Ubuntu Mate 17.10 (Intel AC8260)"
date: 2018-02-24
forum: Networking &amp; Wireless
---

### Post by inputouput117 on 2018-02-24
Dell XPS 9550
I upgraded to 32GB of RAM and replaced the flakey default wireless card with an Intel 8260.

I then wiped Windows 10 and installed Ubuntu Mate 17.10.

Since I made the full switch to Ubuntu, nothing on Bluetooth is functional... FWIW WiFi *does* work reliably.

At first 2/3 of my usual devices were discoverable: a Bluetooth speaker and my keyboard, but pairing was very difficult. The keyboard would work for a bit then stop. My mouse would not even appear as discoverable.

Now nothing shows up as discoverable at all. I am not sure what actions affected this change other than downloading some driver from Intel's website and putting a file in /lib/firmware, and a few reboots.

This is using the default Bluetooth Manager in task bar, and also using bluetoothctl for manual checks.

I'm not afraid of digging deep into the command line, I used to roll my own kernels in the 2.x days, but I'd rather avoid that if possible. The issue is that I haven't looked under the hood of Linux internals in a long time and have very little experience with bluetooth in general.

Can anyone help?

```
[    0.120000] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.946545] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_26.bin (v1.26)
[   20.930891] Bluetooth: Core ver 2.22
[   20.930901] Bluetooth: HCI device and connection manager initialized
[   20.930903] Bluetooth: HCI socket layer initialized
[   20.930904] Bluetooth: L2CAP socket layer initialized
[   20.930907] Bluetooth: SCO socket layer initialized
[   20.939392] Bluetooth: HCI UART driver ver 2.3
[   20.939394] Bluetooth: HCI UART protocol H4 registered
[   20.939395] Bluetooth: HCI UART protocol BCSP registered
[   20.939421] Bluetooth: HCI UART protocol LL registered
[   20.939422] Bluetooth: HCI UART protocol ATH3K registered
[   20.939423] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   20.939458] Bluetooth: HCI UART protocol Intel registered
[   20.939484] Bluetooth: HCI UART protocol Broadcom registered
[   20.939485] Bluetooth: HCI UART protocol QCA registered
[   20.939486] Bluetooth: HCI UART protocol AG6XX registered
[   20.939487] Bluetooth: HCI UART protocol Marvell registered
[   20.991805] Bluetooth: hci0: Firmware revision 0.0 build 118 week 50 2016
[   21.019069] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-33.ucode failed with error -2
[   21.019082] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-32.ucode failed with error -2
[   21.025567] iwlwifi 0000:02:00.0: loaded firmware version 31.560484.0 op_mode iwlmvm
[   21.843545] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.843547] Bluetooth: BNEP filters: protocol multicast
[   21.843549] Bluetooth: BNEP socket layer initialized
[   42.501172] Bluetooth: RFCOMM TTY layer initialized
[   42.501177] Bluetooth: RFCOMM socket layer initialized
[   42.501181] Bluetooth: RFCOMM ver 1.11
[ 1020.201574] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-33.ucode failed with error -2
[ 1020.201582] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-32.ucode failed with error -2
[ 1020.202598] iwlwifi 0000:02:00.0: loaded firmware version 31.560484.0 op_mode iwlmvm
[ 1041.031959] Bluetooth: Failed to disable LE scan: status 0x0c
```

---

