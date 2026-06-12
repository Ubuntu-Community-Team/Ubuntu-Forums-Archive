---
title: "Qualcomm Atheros can't find network again, this time on 16.04"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2016-06-16
Hi all, I'm the person from [http://ubuntuforums.org/showthread.php?t=2316533](http://ubuntuforums.org/showthread.php?t=2316533) with the Acer Aspire R5-471T laptop and bitterly uncooperative Qualcomm Atheros QCA6174 wireless network adapter. My installation of 14.04 had numerous other problems, and eventually at the urging of others I upgraded to 16.04. This fixed numerous things, but the wireless solutions from before no longer seem to work. I've gone through all of the steps in that thread, and also tried the 16.04 answer here without success:

[http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in)

Some maybe relevant information follows:
```
$ dmesg | grep ath
[    2.047110] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.291700] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    4.669999] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00088-QCARMSWPZ-1 fwapi 5 bdapi 2 htt-ver 3.14 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[    4.670003] ath10k_pci 0000:01:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.743313] ath: EEPROM regdomain: 0x6c
[    4.743317] ath: EEPROM indicates we should expect a direct regpair map
[    4.743319] ath: Country alpha2 being used: 00
[    4.743320] ath: Regpair used: 0x6c
[    4.776117] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0

$ ls /lib/firmware/ath10k/QCA6174/hw3.0
board-2.bin  firmware-4.bin  notice_ath10k_firmware-4.txt
board.bin    firmware-5.bin  notice_ath10k_firmware-5.txt
```

Thank you

---

### Post by jeremy31 on 2016-06-16
Lets remove existing firmware ```
sudo rm -r /lib/firmware/ath10k/
```
Then we get the latest linux-firmware from Ubuntu
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```

Post the results for ```
modinfo ath10k_pci
```

---

### Post by jdkcarlson on 2016-06-17
Okay, done. Except I moved the old /lib/firmware/ath10k to something called OLDath10k rather than killing it in case it somehow is not worthless now. Here's modinfo:

```
:~/Desktop$ modinfo ath10k_pci
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
alias:          pci:v0000168Cd00000042sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000040sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000041sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)
```

**Update**: Networks are visible again.

Thank you! Again.

---

