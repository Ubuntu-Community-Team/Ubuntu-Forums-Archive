---
title: "bluetooth on Lubuntu 16.04 Thinkpad X1 Carbon"
date: 2017-09-16
forum: Networking &amp; Wireless
---

### Post by pastknz on 2017-09-16
Hi there,

I am on Lubuntu 16.04 and the Blueman BT manager can't detect any BT adapters.

However according to Lenovo specs my model (3444-2HU) does have a "Bluetooth 4.0 wireless".

```

pastk@pastk-ThinkPad-X1-Carbon:~$ uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
4.10.0-33-generic
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b315 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 96)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:c220]
    Kernel driver in use: iwlwifi
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.233833] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.326696] pnp 00:01: [Firmware Bug]: PNP resource [mem 0xfed10000-0xfed13fff] covers only part of 0000:00:00.0 Intel MCH; extending to [mem 0xfed10000-0xfed17fff]
[    3.960823] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    4.155754] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[12584.000732] Bluetooth: Core ver 2.22
[12584.000760] Bluetooth: HCI device and connection manager initialized
[12584.000910] Bluetooth: HCI socket layer initialized
[12584.000912] Bluetooth: L2CAP socket layer initialized
[12584.000918] Bluetooth: SCO socket layer initialized
[12697.282831] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[12697.282832] Bluetooth: BNEP filters: protocol multicast
[12697.282835] Bluetooth: BNEP socket layer initialized

```

Thanks a lot for your help!

Cheers!
Konstantin

---

### Post by mörgæs on 2017-09-17
Hi, welcome to the fora.

When I see messages like yours about a firmware bug I generally try the latest Buntu and update the BIOS. 'Generally' means that I don't have any special knowledge about your Bluetooth adapter.

---

### Post by jeremy31 on 2017-09-17
I see no bluetooth controller in those results, as the Intel 6205 doesn't offer bluetooth [http://ark.intel.com/products/59471/Intel-Centrino-Advanced-N-6205-Dual-Band](http://ark.intel.com/products/59471/Intel-Centrino-Advanced-N-6205-Dual-Band)

---

