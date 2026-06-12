---
title: "Wireless setting on Vaio"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Brangwolf on 2008-11-11
Hey guys :) 

It's been couple of days now I've been trying to get this thing working. I've tried almost anything but still no success. 

I have a Sony Vaio VGN-FW139e, with Intel WiFi Link 5100 and a killswitch.

I have the card shown in System>Hardware drivers, but it's status is deactivated. However, I cannot see it in any network settings. Neither System>network, or ifconfig, or iwconfig. What is wrong?

I am using linux kernel version 2.6.24-21-generic
and Ubuntu 8.04.

Sorry for noob explanation, still new, but try to learn fast :)

---

### Post by iponeverything on 2008-11-11
> **Brangwolf said:**
> Hey guys :) 

It's been couple of days now I've been trying to get this thing working. I've tried almost anything but still no success. 

I have a Sony Vaio VGN-FW139e, with Intel WiFi Link 5100 and a killswitch.

I have the card shown in System>Hardware drivers, but it's status is deactivated. However, I cannot see it in any network settings. Neither System>network, or ifconfig, or iwconfig. What is wrong?

I am using linux kernel version 2.6.24-21-generic
and Ubuntu 8.04.

Sorry for noob explanation, still new, but try to learn fast :)


try:

sudo modprobe ath9k

also send the output "lspci"

---

### Post by Brangwolf on 2008-11-11
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
06:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
0a:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

---

### Post by iponeverything on 2008-11-11
Download the driver from here:

[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

Try to follow the instructions to build and install the module.  If you run into problems post back here and someone will help you. I check back tomorrow and help you out if your still stuck.

Just found this:

[http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/)

grab:
	linux-headers-2.6.27-1-generic_2.6.27-1.1_i386.deb
	linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb

ath9k has been merged with this kernel.

Install them with:

```
sudo dpkg -i linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb linux-headers-2.6.27-1-generic_2.6.27-1.1_i386.deb
```

If you run into problems booting this kernel, choose the original one from your grub menu.

---

