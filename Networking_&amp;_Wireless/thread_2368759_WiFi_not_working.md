---
title: "WiFi not working"
date: 2017-08-14
forum: Networking &amp; Wireless
---

### Post by CloudStrife9197 on 2017-08-14
Just installed ubuntu for the first time.And the problem is it's not showing wifi connection.
Checked iwconfig and it's showing...
enp3s0  no wireless extensions
lo   no wireless extension 
Biggest problem is i don't have access to an Ethernet cable so,someone please help

---

### Post by praseodym on 2017-08-14
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
```

---

### Post by CloudStrife9197 on 2017-08-14
Bus 002 Device 003: ID 04f2:b509 chicony electronics co.,Ltd
Bus 002 Device 002: ID 0438:7900 Advanced micro devices,Inc.
Bus 002 Device 001: ID 1d6b:0002 Linus foundation 2.0 root hub
Bus 001 Device 004: ID 0a5c:216d Broadcom corp.
Bus 001 Device 003: ID 046d:c52f logitech,inc.unifying receiver
Bus 001 Device 002: ID 0438:7900 advanced micro devices,inc.
Bus 001 Device 001: ID 1d6b:0002 Linus foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linus foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linus foundation 2.0 root hub

---

### Post by praseodym on 2017-08-14
Ok, so lets see

```
lspci -nnk
```

---

### Post by CloudStrife9197 on 2017-08-14
```
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1566]
	
Subsystem: Hewlett-Packard Company Device [103c:80cc]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (rev 45)
	Subsystem: Hewlett-Packard Company Mullins [Radeon R4/R5 Graphics] [103c:80cc]
	Kernel driver in use: radeon
	Kernel modules: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio [1002:9840]
	Subsystem: Hewlett-Packard Company Kabini HDMI/DP Audio [103c:80cc]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:156b]
00:02.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
	DeviceName: CX20752 HD AUDIO CODEC
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.5 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:08.0 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:1537]
	Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1537]
	Kernel driver in use: ccp
	Kernel modules: ccp
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 11)
	Subsystem: Hewlett-Packard Company FCH USB XHCI Controller [103c:80cc]
	Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7804] (rev 39)
	Subsystem: Hewlett-Packard Company FCH SATA Controller [AHCI mode] [103c:80cc]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 39)
	Subsystem: Hewlett-Packard Company FCH USB EHCI Controller [103c:80cc]
	Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 39)
	Subsystem: Hewlett-Packard Company FCH USB EHCI Controller [103c:80cc]
	Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 42)
	Subsystem: Hewlett-Packard Company FCH SMBus Controller [103c:80cc]
	Kernel modules: i2c_piix4, sp5100_tco
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 02)
	Subsystem: Hewlett-Packard Company FCH Azalia Controller [103c:80cc]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
	Subsystem: Hewlett-Packard Company FCH LPC Bridge [103c:80cc]
00:14.7 SD Host controller [0805]: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller [1022:7813] (rev 01)
	Subsystem: Hewlett-Packard Company FCH SD Flash Controller [103c:80cc]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci_pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1580]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1581]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1582]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1583]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1584]
	Kernel driver in use: fam15h_power
	Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1585]
01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330] [1002:6660] (rev ff)
	Kernel driver in use: radeon
	Kernel modules: radeon
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	DeviceName: NAMI
	Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
	Kernel modules: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80cc]
	Kernel driver in use: r8169
	Kernel modules: r8169
```

---

### Post by wildmanne39 on 2017-08-14
Can you use your cell phone to tether to the internet to install a driver for your wifi? if not:

Broadcom STA 43 wireless
Your Broadcom 14e4:4365 uses bcmwl-kernel-source. It and its dependency dkms are on the installation DVD or USB. Insert the install media and navigate to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop. Do the same with pool > main > d > dkms. Now we install the deb files. Open a terminal and:
```
cd ~/Desktop
sudo dpkg -i *.deb
sudo modprobe wl
```
it should be working.

---

### Post by CloudStrife9197 on 2017-08-15
First two commands ran fine...but in the last one,it's saying could not insert 'wl':required key not available

---

### Post by jeremy31 on 2017-08-15
Go into BIOS and disable Secure Boot, then it should work

---

### Post by genericvii143 on 2017-08-15
If what the forum MOD say doesn't work please  type in the terminal  "sudo rfkill list" and lets see what is in there and  if you go to the driver manager as well  show use what is it said sometimes could be a easy fix.

---

