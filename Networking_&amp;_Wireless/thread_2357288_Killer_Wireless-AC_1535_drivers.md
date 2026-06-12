---
title: "Killer Wireless-AC 1535 drivers"
date: 2017-03-31
forum: Networking &amp; Wireless
---

### Post by pieter512 on 2017-03-31
Hello

I have a Dell XPS 15 9560 (2017 edition) with a Killer Wireless-AC 1535 Wi-Fi card. 5GHz works fine, and some newer 2.4GHz networks work as well, but I'm unable to connect to some older 2.4GHz access points. 
I'm running Ubuntu 16.04 (4.8.0-41-generic #44~16.04.1-Ubuntu).

These are the kernel messages:
```
[    4.676935] ath10k_pci 0000:02:00.0: enabling device (0000 -> 0002)[    4.678052] ath10k_pci 0000:02:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    4.977359] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
[    4.977364] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    4.977625] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.977626] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.978554] ath10k_pci 0000:02:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    4.978555] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.978920] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    5.041950] ath10k_pci 0000:02:00.0: board_file api 2 bmi_id N/A crc32 6fc88fe7
[    7.166740] ath10k_pci 0000:02:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    7.253446] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
```

The /lib/firmware/ath10k/QCA6174/hw3.0/ folder contains the following files:
```
total 1140
-rw-r--r-- 1 root root 337204 Dez  9 22:17 board-2.bin
-rw-r--r-- 1 root root   8124 Dez  1 22:24 board.bin
-rw-r--r-- 1 root root 733784 Dez  1 22:24 firmware-4.bin
-rw-r--r-- 1 root root  79689 Dez  1 22:24 notice_ath10k_firmware-4.txt
```

How can I get my Wi-Fi to work?

Thanks in advance!
Pieter

---

### Post by jeremy31 on 2017-03-31
*Thread moved to **Networking & Wireless**.*

The kernel modules do not support some older wireless standards so that is why it doesn't work on some access points.  You could file a bug report and see if it gets some attention

---

### Post by pieter512 on 2017-03-31
Thanks for the reply.
Where should I file the bug report? (Not that it's gonna make a difference, but I can always try ...)

Pieter

---

### Post by jeremy31 on 2017-03-31
Some info at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
I would file against package linux and you might want to search for the ath10k mailing list and ask there also

---

