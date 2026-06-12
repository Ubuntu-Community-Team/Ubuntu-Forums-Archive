---
title: "My laptop wireless works ok with windows but not Ubuntu"
date: 2019-02-02
forum: Networking &amp; Wireless
---

### Post by t5404tmz on 2019-02-02
I need help getting my wireless working with Ubuntu.

What information do I need to post here, and what are the commands I need to execute.

---

### Post by praseodym on 2019-02-02
Please run the wireless script from the sticky thread and show the outputs. Does LAN work?

---

### Post by t5404tmz on 2019-02-02
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs. Does LAN work?

No lan connection.

Here is some relevant info:

ubuntu-mate@ubuntu-mate:~$ uname -rv
 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:37:27 UTC 2018
 
 
 ubuntu-mate@ubuntu-mate:~$ lspci -knn | grep -EiA2 net
 00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
     Subsystem: Dell 82567LM Gigabit Network Connection [1028:0233]
     Kernel driver in use: e1000e
     Kernel modules: e1000e
 --
 0c:00.0 Network controller [0280]: Broadcom Limited BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
     Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card [1028:000d]
     Kernel driver in use: b43-pci-bridge
 
 
 ubuntu-mate@ubuntu-mate:~$ dmesg|grep -Ei 'wlan|firmw|dhc'
 [    0.048125] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
 [    0.244893] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
 [    0.276368] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
 [    8.378799] sdhci: Secure Digital Host Controller Interface driver
 [    8.378800] sdhci: Copyright(c) Pierre Ossman
 [    8.396453] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 21)
 [    8.413156] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
 [    8.743226] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
 [   24.150243] dell_wmi: firmware scancode 0x200 maps to unrecognized keycode 0xffff
 [   24.538502] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
 [   24.597716] b43 ssb0:0: Direct firmware load for b43/ucode16_mimo.fw failed with error -2
 [   24.597730] b43 ssb0:0: Direct firmware load for b43/ucode16_mimo.fw failed with error -2
 [   24.597754] b43 ssb0:0: Direct firmware load for b43-open/ucode16_mimo.fw failed with error -2
 [   24.597766] b43 ssb0:0: Direct firmware load for b43-open/ucode16_mimo.fw failed with error -2
 [   24.597768] b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found
 [   24.597769] b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found
 [   24.597770] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
 ubuntu-mate@ubuntu-mate:~$ 
 
 
 ubuntu-mate@ubuntu-mate:~$ sudo rfkill list
 0: dell-wifi: Wireless LAN
     Soft blocked: no
     Hard blocked: no
 1: dell-bluetooth: Bluetooth
     Soft blocked: no
     Hard blocked: no
 2: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no
 ubuntu-mate@ubuntu-mate:~$

---

### Post by praseodym on 2019-02-02
Go to "Additional drivers" in the update section, activate the STA driver and reboot. Deactivate SecureBoot

---

### Post by t5404tmz on 2019-02-02
> **praseodym said:**
> Go to "Additional drivers" in the update section, activate the STA driver and reboot. Deactivate SecureBoot

During my first attempt I got a system error but the wireless started working.  My session got hung for some reason so I rebooted and my second attempt to activate the STA driver succeeded without error.  Thanks!

Should I post the error message?  I had to take 6 screenshots because the message window did not allow copying to the clipboard.

---

### Post by praseodym on 2019-02-03
Does it work now?

---

