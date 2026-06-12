---
title: "Lenovo Thinkcentre M53 - Bluetooth not detecting devices"
date: 2015-09-01
forum: Networking &amp; Wireless
---

### Post by jamarsh123 on 2015-09-01
Ubuntu 14.04 installed on Thinkcentre m53. Bluetooth seems to work - able to turn off and on - but does not detect devices. The hardware is default, preinstalled, no added usb. This is a dual boot with Windows 7; Bluetooth works in Windows.

lspci returns:
```
00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter


```

---

### Post by Hadaka on 2015-09-01
hi,did you run the updates after you loaded Ubuntu?
if not..please do..
```
sudo apt-get updates
```
boot
iif you still have no bluetooth go here
follow the directions,post your wireless-info-text file.
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
thanks

---

### Post by jeremy31 on 2015-09-01
```
[COLOR=#111111][FONT=Consolas]sudo add-apt-repository ppa:hanipouspilot/rtlwifi
[/FONT][/COLOR]sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware rtl8723au-bt-dkms
```
Reboot

---

### Post by jamarsh123 on 2015-09-01
Thanks for the information. I followed the instructions and the Bluetooth is fully functional.

---

### Post by george-panainte on 2015-09-03
> **jeremy31 said:**
> ```
[COLOR=#111111][FONT=Consolas]sudo add-apt-repository ppa:hanipouspilot/rtlwifi
[/FONT][/COLOR]sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware rtl8723au-bt-dkms
```
Reboot

also helped me on Ubuntu 15.04 on my HP ProBook 470 g2

---

