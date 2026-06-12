---
title: "wifi adaptor not found ubuntu 18.04 dual booted with Windows 7"
date: 2018-07-16
forum: Networking &amp; Wireless
---

### Post by brat4 on 2018-07-16
[COLOR=#000000]hello![/COLOR]
[COLOR=#000000]i have just set up ubuntu 18.04 lts as a dual boot along with windows 7.I am unable to connect to the wifi. The system shows no wifi adaptor found. However it worked fine in windows.
[/COLOR][COLOR=#000000]lspci gives the following result

[/COLOR]rahul@rahul-Inspiron-3542:~$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 07)
08:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)





[COLOR=#000000]
[/COLOR]

---

### Post by stoogiebuncho on 2018-07-16
What do you get from ```
lspci -nnk | grep 0280 -A2
```

---

### Post by brat4 on 2018-07-17
rahul@rahul-Inspiron-3542:~$ lspci -nnk | grep 0280 -A2
.libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with '&#8220;options'
06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020c]
    Kernel driver in use: ath9k

---

### Post by jeremy31 on 2018-07-17
See the wireless script link in my signature and post results

---

