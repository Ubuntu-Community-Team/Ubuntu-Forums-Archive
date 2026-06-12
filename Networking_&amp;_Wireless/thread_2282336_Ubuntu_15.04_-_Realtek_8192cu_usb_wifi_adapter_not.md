---
title: "Ubuntu 15.04 - Realtek 8192cu usb wifi adapter not working"
date: 2015-06-13
forum: Networking &amp; Wireless
---

### Post by amsplanner on 2015-06-13
After trying multiple solutions (most recently the pvaret driver fixes) offered in the forum my usb wifi adapter wont connect, or when it does it's extremely unstable. Oddly (odd to me, anyway) the modules I attempted to blacklist still appear in lsmod, and 8192cu does not. Very new to this, so possible (probable) that I missed a step in configuring the driver I suppose. I've attached the wireless-info.tar.gz file. Any help would be much appreciated!

---

### Post by mörgæs on 2015-06-13
Before proceeding I would begin with installing 15.04. 14.10 is out of support in a month.

---

### Post by amsplanner on 2015-06-14
Done. No change in wireless connection issue. The updated wireless-info is attached.

---

### Post by Pilot6 on 2015-06-14
You can install a working driver

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install [COLOR=#333333][FONT=Ubuntu]rtl8192cu-dkms

Packages are for 14.04 and 15.04.[/FONT][/COLOR]

---

### Post by Chrierton on 2015-06-17
> **Pilot6 said:**
> You can install a working driver

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install [COLOR=#333333][FONT=Ubuntu]rtl8192cu-dkms

Packages are for 14.04 and 15.04.[/FONT][/COLOR]

Thank you, this worked for me where other solutions didn't.

---

### Post by amsplanner on 2015-06-17
Unfortunately this didn't work for me. Still no wireless connection.

---

### Post by Pilot6 on 2015-06-18
> **amsplanner said:**
> Unfortunately this didn't work for me. Still no wireless connection.

You do not give enough information to help. Did the driver install? Did you have internet connection, when run the commands.
Ubuntu 14.10 is not supported directly from ppa. But you can download and install deb manually

---

### Post by Pilot6 on 2015-06-18
If you have 14.10, you can download and install the deb

[https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192cu-dkms_0.2_all.deb](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192cu-dkms_0.2_all.deb)

---

### Post by amsplanner on 2015-06-18
I have 15.04--per morgaes' suggestion above. (If I should close this thread and start a new one more accurately titled to reflect the update distro I'm  running, someone please let me know and I'll do that.) Yes, the driver installation completed without errors. My machine was connected via ethernet at the time of installation. Network manager recognizes my USB wifi adapter, and lists my wireless network, but will not connect. lsmod shows the module 8192cu as active. Do i need to take an additional step or two to blacklist the non-working module and activate the one I installed? Let me know if there is specific info that would be helpful. Noob here. Thanks!!

---

### Post by Pilot6 on 2015-06-18
> **amsplanner said:**
> I have 15.04--per morgaes' suggestion above. (If I should close this thread and start a new one more accurately titled to reflect the update distro I'm  running, someone please let me know and I'll do that.) Yes, the driver installation completed without errors. My machine was connected via ethernet at the time of installation. Network manager recognizes my USB wifi adapter, and lists my wireless network, but will not connect. lsmod shows the module 8192cu as active. Do i need to take an additional step or two to blacklist the non-working module and activate the one I installed? Let me know if there is specific info that would be helpful. Noob here. Thanks!!

You need to remove or blacklist that 8192cu module. rtl8192cu should not be blacklisted. And reinstall the driver from my ppa.

---

### Post by mörgæs on 2015-06-18
> **amsplanner said:**
> I have 15.04--per morgaes' suggestion above. (If I should close this thread and start a new one more accurately titled to reflect the update distro I'm  running, someone please let me know and I'll do that.) 

Are you able to edit the title of the thread?

---

### Post by amsplanner on 2015-06-19
Edited the blacklist.conf file so that 8192cu was listed ant that rtl8192cu was not. Reinstalled driver from ppa, which returned, in part "rtl8192cu-dkms is already the newest version." No wifi at all after reboot. But I then tried ```
sudo modprobe rtl8192cu
``` and then at least network manager recognized the wireless adapter; but still could not connect to wireless networks. Network manager only shows ethernet connection currently.

---

### Post by amsplanner on 2015-06-19
And in the "Thread Tools" I don't see an option to edit the title unfortunately.

---

### Post by Pilot6 on 2015-06-20
Please add output of

cat /etc/network/interfaces

---

### Post by amsplanner on 2015-06-20
Output is below ```
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by amsplanner on 2015-07-25
Any other thoughts on this? Still unable to use wireless adapter.

---

### Post by praseodym on 2015-07-25
Which device is it?

```
lspci -nnk
lsusb
```

---

### Post by amsplanner on 2015-07-26
```
$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 0a5c:2148 Broadcom Corp. BCM92046DG-CL1ROM Bluetooth 2.1 Adapter
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 2109:0812  
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 045: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 007 Device 016: ID 03f0:2504 Hewlett-Packard DeskJet F4200 series
Bus 007 Device 036: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 007 Device 046: ID 1058:1023 Western Digital Technologies, Inc. Elements SE
Bus 007 Device 002: ID 2109:2812  
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by amsplanner on 2015-07-26
```
$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex [1022:1410]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8526]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8470D] [1002:9996]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8526]
	Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8526]
	Kernel driver in use: snd_hda_intel
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: xhci_hcd
00:10.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 16)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
	Kernel driver in use: piix4_smbus
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8576]
	Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85fc]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) [1022:43a0]
	Kernel driver in use: pcieport
00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2) [1022:43a2]
	Kernel driver in use: pcieport
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0 [1022:1400]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1 [1022:1401]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2 [1022:1402]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3 [1022:1403]
	Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:859e]
	Kernel driver in use: r8169

```

---

### Post by praseodym on 2015-07-26
> ```
Bus 007 Device 036: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
```

8192cu should work.
```

sudo modprobe -rfv 8192cu rtl8192cu
sudo modprobe -v 8192cu
```
Check:
```
grep 8192 /etc/modprobe.d/*
cat /etc/modules
cat /etc/resolv.conf
ifconfig -a
iwconfig
iwlist chan
sudo iwlist scan
dmesg | egrep 'wlan|8192|firm'
route -n
modinfo 8192cu | egrep 'versi|filen'
locate 8192cu.ko | grep lib 
```

---

### Post by amsplanner on 2016-02-26
That worked! Thanks. (Apologies for the hiatus. Moved cross-country and put this system in storage for a while.) Back in action now.

---

