---
title: "Broadcom BCM4312"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by dtwilder on 2013-10-01
I'm having similar problems but no luck yet. I'm totally new to ubuntu.

When I type lspci -nnk | grep -iA2 net    in the cmd prompt I get:

0200.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL 8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
Subsystem: Dell Device [1028:02c6]
Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
Kernel driver in use: b43-pci-bridge


I can't seem to find a way to make this work. Any help is greatly appreciated.

Doug

---

### Post by varunendra on 2013-10-02
> **dtwilder said:**
> 03:00.0 Network controller [0280]: Broadcom Corporation **BCM4312 802.11b/g LP-PHY [14e4:4315]** (rev 01)
Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
Kernel driver in use: b43-pci-bridge

Welcome to the forums Doug !

While being connected to the internet, please do -
```
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -rv b43
sudo modprobe -v b43
```

If you can't connect via cable or any other way, manually download the linux-firmware-nonfree package from here : [http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download)

Copy it to your Ubuntu desktop and double-click to install it. Then either reboot or run the last two commands from above. Let us know there is still problem.

---

