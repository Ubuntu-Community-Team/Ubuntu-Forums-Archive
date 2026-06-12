---
title: "Lubuntu 20.04 bluetooth devices not detected"
date: 2020-05-20
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2020-05-20
Hello,

On a new install of Lubuntu 20.04 LTS my bluetooth devices are not detected either with BlueDevil Wizard or with Blueman bluetooth manager. Neither is my laptop visible to my phone, although in Blueman I have selected "Always visible".

Yes, my devices are turned on. Yes, my laptop has bluetooth capability. Yes, my wireless connection is working.

Please help me solve this problem. What info do you need to help me and how do I get it?

Many thanks.

---

### Post by rdh61 on 2020-05-21
No takers, really? Come on guys, there must be some Ubuntu magician/guru out there who has come up against this kind of thing before... Please...

---

### Post by rdh61 on 2020-05-21
Perhaps this will help:

```
robert@roberts-work-laptop:~$ lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
        Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
        Kernel driver in use: wl
        Kernel modules: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
        Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5002]
        Kernel driver in use: r8169
        Kernel modules: r8169
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 04f2:b2fa Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.124958] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.157797] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   15.750839] thinkpad_acpi: ThinkPad firmware release H9EC07WW doesn't match the known patterns
[   15.769421] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   17.269630] Bluetooth: Core ver 2.22
[   17.269658] Bluetooth: HCI device and connection manager initialized
[   17.269662] Bluetooth: HCI socket layer initialized
[   17.269665] Bluetooth: L2CAP socket layer initialized
[   17.269668] Bluetooth: SCO socket layer initialized
[   17.669590] Bluetooth: hci0: BCM: chip id 70
[   17.670569] Bluetooth: hci0: BCM: features 0x06
[   17.686559] Bluetooth: hci0: BCM43142A
[   17.687571] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[   17.819714] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[   17.819719] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[   19.835869] Bluetooth: hci0: command 0x1003 tx timeout
[   19.836568] Bluetooth: hci0: unexpected event for opcode 0x1003
[   30.367262] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.367264] Bluetooth: BNEP filters: protocol multicast
[   30.367268] Bluetooth: BNEP socket layer initialized
[   33.499880] Bluetooth: hci0: command 0x1003 tx timeout
[   33.501492] Bluetooth: hci0: unexpected event for opcode 0x1003
[   58.390099] Bluetooth: RFCOMM TTY layer initialized
[   58.390107] Bluetooth: RFCOMM socket layer initialized
[   58.390116] Bluetooth: RFCOMM ver 1.11
robert@roberts-work-laptop:~$
```

---

### Post by rdh61 on 2020-05-22
Wondering why no replies (except my own!). I have looked at other people's questions about bluetooth problems and it seems few people find help here. Does nobody in here know anything about bluetooth?

---

### Post by rdh61 on 2020-05-22
For anyone else in the same situation...

 I needed to download a driver.
  The solution is here:

  [https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware)

---

### Post by VMC on 2020-05-31
It appears that github is specific to Broadcom, as also per your listing.

---

