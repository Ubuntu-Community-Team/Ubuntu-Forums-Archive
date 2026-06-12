---
title: "Ubuntu 17.10 bluetooth not working"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by irakliy01 on 2017-11-01
I wanted to connect my dualshock 4 to computer. Everything was ok, I connected it, but had some problems with its functionality. So, I downloaded ds4drv and connected dualshock to computer using this ds4drv. It worked fine and I've been playing games for an hour-two. After that I rebooted computer and tried to connect it again, but bluetooth didn't detect the device. Moreover, it still doesn't detect **any** device, not just dualshock. What have I done wrong and how do I fix it?

```

lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'


07:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e071]
    Kernel driver in use: wl
--
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b3aa Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 03eb:8812 Atmel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[  186.404233] Bluetooth: Core ver 2.22
[  186.404342] Bluetooth: HCI device and connection manager initialized
[  186.404346] Bluetooth: HCI socket layer initialized
[  186.404349] Bluetooth: L2CAP socket layer initialized
[  186.404355] Bluetooth: SCO socket layer initialized
[  186.529974] Bluetooth: hci0: BCM: chip id 70
[  186.530921] Bluetooth: hci0: BCM: features 0x06
[  186.546813] Bluetooth: hci0: irakliy01-desktop
[  186.546817] Bluetooth: hci0: BCM (001.001.011) build 0000
[  186.547295] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[  186.547298] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[  186.563323] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  186.563326] Bluetooth: BNEP filters: protocol multicast
[  186.563330] Bluetooth: BNEP socket layer initialized
[  188.572093] Bluetooth: hci0 command 0x1003 tx timeout
[  188.572182] Bluetooth: hci0 sending frame failed (-19)
[  190.588078] Bluetooth: hci0 command 0x1001 tx timeout
[  190.588122] Bluetooth: hci0 sending frame failed (-19)
[  192.604058] Bluetooth: hci0 command 0x1009 tx timeout
[  198.498824] Bluetooth: hci0: BCM: chip id 70
[  198.499850] Bluetooth: hci0: BCM: features 0x06
[  198.515789] Bluetooth: hci0: irakliy01-desktop
[  198.515801] Bluetooth: hci0: BCM (001.001.011) build 0000
[  198.515843] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[  198.515848] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[  200.540019] Bluetooth: hci0 command 0x1003 tx timeout
[  200.750724] Bluetooth: RFCOMM TTY layer initialized
[  200.750729] Bluetooth: RFCOMM socket layer initialized
[  200.750734] Bluetooth: RFCOMM ver 1.11
[ 1435.484358] Bluetooth: hci0: BCM: chip id 70
[ 1435.485333] Bluetooth: hci0: BCM: features 0x06
[ 1435.501395] Bluetooth: hci0: irakliy01-desktop
[ 1435.501407] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 1435.501447] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 1435.501452] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 1437.522172] Bluetooth: hci0 command 0x1003 tx timeout
[ 1706.066039] Bluetooth: hci0: BCM: chip id 70
[ 1706.067041] Bluetooth: hci0: BCM: features 0x06
[ 1706.083090] Bluetooth: hci0: irakliy01-desktop
[ 1706.083107] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 1706.083176] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 1706.083184] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found



```

---

