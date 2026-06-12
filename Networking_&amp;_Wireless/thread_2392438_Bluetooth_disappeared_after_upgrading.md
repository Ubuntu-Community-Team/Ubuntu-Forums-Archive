---
title: "Bluetooth disappeared after upgrading"
date: 2018-05-21
forum: Networking &amp; Wireless
---

### Post by biosthezerg2 on 2018-05-21
Hi,
I've recently upgraded my Ubuntu 16.04 and after a restart, my Bluetooth stopped working. It's a MSI GE63VR 7RF laptop and up until earlier today everything worked fine. Anybody would know what could have gone wrong? Here are some listings:

```
 dmesg | grep -i blue
[    2.745296] Bluetooth: Core ver 2.22
[    2.745304] Bluetooth: HCI device and connection manager initialized
[    2.745306] Bluetooth: HCI socket layer initialized
[    2.745307] Bluetooth: L2CAP socket layer initialized
[    2.745310] Bluetooth: SCO socket layer initialized
[    2.752199] Bluetooth: HCI UART driver ver 2.3
[    2.752201] Bluetooth: HCI UART protocol H4 registered
[    2.752201] Bluetooth: HCI UART protocol BCSP registered
[    2.752210] Bluetooth: HCI UART protocol LL registered
[    2.752210] Bluetooth: HCI UART protocol ATH3K registered
[    2.752211] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    2.752228] Bluetooth: HCI UART protocol Intel registered
[    2.752236] Bluetooth: HCI UART protocol Broadcom registered
[    2.752236] Bluetooth: HCI UART protocol QCA registered
[    2.752237] Bluetooth: HCI UART protocol AG6XX registered
[    2.752237] Bluetooth: HCI UART protocol Marvell registered
[    9.225294] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.225295] Bluetooth: BNEP filters: protocol multicast
[    9.225297] Bluetooth: BNEP socket layer initialized

```

```

lspci
00:00.0 Host bridge: Intel Corporation Device 5910 (rev 05)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 05)
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #7 (rev f1)
00:1c.7 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #8 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Device a171 (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1ba1 (rev a1)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
03:00.0 USB controller: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5250 PCI Express Card Reader (rev 01)
05:00.0 Ethernet controller: Qualcomm Atheros Device e0b1 (rev 10)

```

```

lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0451:8140 Texas Instruments, Inc. 
Bus 002 Device 002: ID 0451:8140 Texas Instruments, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 1038:1122 SteelSeries ApS 
Bus 001 Device 008: ID 0451:ca01 Texas Instruments, Inc. 
Bus 001 Device 006: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 004: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 007: ID 5986:0547 Acer, Inc 
Bus 001 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I've seen somewhere on the internet that it could be a firmware issue, this is the only line which seems even remotely relevant:
```

sudo grep -i firmware /var/log/syslog*
...
/var/log/syslog:May 21 13:31:10 synthesia-GE63VR-7RF fwupd[2119]: (fwupd:2119): Fu-WARNING **: disabling plugin because: failed to coldplug raspberrypi: Raspberry PI firmware updating not supported, no /boot/start.elf
...

```

Thanks!

---

### Post by biosthezerg2 on 2018-05-24
Bump

---

