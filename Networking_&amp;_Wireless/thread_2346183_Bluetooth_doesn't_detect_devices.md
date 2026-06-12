---
title: "Bluetooth doesn't detect devices"
date: 2016-12-12
forum: Networking &amp; Wireless
---

### Post by mroovkoyad on 2016-12-12
I am trying to pair Sony MDR-ZX550BN headset with Lenovo G580 laptop with Ubuntu 16.04. Laptop can't detect nor headset nor other devices (headset paired with smartfon works fine).

Many sources say that editing /etc/bluetooth/main.conf helps. I have done that, but nothing happened.

Other source said that disabling UEFI will solve the problem. But it didn't.

Blueman also detects nothing.

Is there any rescue for me except returning to Windows?

---

### Post by jeremy31 on 2016-12-12
Welcome to the forums
You could give us some info about your hardware
```
lsusb; lspci -nnk | grep -iA2 net; dmesg | egrep -i 'blue|firm'
```

---

### Post by mroovkoyad on 2016-12-12
Here is the result:
```
Bus 002 Device 003: ID 04f2:b2e1 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 12d1:14dc Huawei Technologies Co., Ltd. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo AR8162 Fast Ethernet [17aa:3979]
    Kernel driver in use: alx
    Kernel modules: alx
04:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
    Kernel driver in use: bcma-pci-bridge
[    0.134653] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.981741] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    4.522429] Bluetooth: Core ver 2.21
[    4.522448] Bluetooth: HCI device and connection manager initialized
[    4.522452] Bluetooth: HCI socket layer initialized
[    4.522455] Bluetooth: L2CAP socket layer initialized
[    4.522463] Bluetooth: SCO socket layer initialized
[    4.560719] Bluetooth: hci0: BCM: chip id 70
[    4.581134] Bluetooth: hci0: laptop
[    4.581140] Bluetooth: hci0: BCM (001.001.011) build 0000
[    4.588342] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    4.588348] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[    5.527776] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.527780] Bluetooth: BNEP filters: protocol multicast
[    5.527785] Bluetooth: BNEP socket layer initialized
[    7.540586] Bluetooth: RFCOMM TTY layer initialized
[    7.540594] Bluetooth: RFCOMM socket layer initialized
[    7.540600] Bluetooth: RFCOMM ver 1.11
```

---

### Post by mroovkoyad on 2016-12-12
Ok, so the solution is:

```
wget https://github.com/gnebehay/gnebehay.com/raw/master/contents/blog/lenovo-flexpad-bluetooth-debian/BCM43142A0-105b-e065.hcd
sudo cp BCM43142A0-105b-e065.hcd /lib/firmware/brcm/BCM.hcd
```

Then turn off and turn on (not restart).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1509803/comments/87](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1509803/comments/87)

---

