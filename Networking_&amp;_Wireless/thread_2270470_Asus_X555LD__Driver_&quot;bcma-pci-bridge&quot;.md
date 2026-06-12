---
title: "Asus X555LD  Driver &quot;bcma-pci-bridge&quot;"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by onofrio-cannone on 2015-03-23
Don't Works WIFI and BLUETOOTH

this is a List: 

dozeen@dozeen-X555LD:~$```
lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
    Kernel driver in use: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0a03] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:201f]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
    Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:201f]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
00:1f.6 Signal processing controller [1180]: Intel Corporation Lynx Point-LP Thermal [8086:9c24] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16cd]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6675]
    Kernel driver in use: bcma-pci-bridge
04:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)
    Kernel driver in use: nouveau
```


How activate it?

---

### Post by jeremy31 on 2015-03-23
```
sudo apt-get install bcmwl-kernel-source
``` Should get the wifi working.  For the bluetooth, post the results of ```
lsusb
```

---

### Post by wildmanne39 on 2015-03-24
Please use code tags.
you can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

