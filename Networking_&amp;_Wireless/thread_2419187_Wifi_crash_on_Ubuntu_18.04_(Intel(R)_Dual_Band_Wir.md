---
title: "Wifi crash on Ubuntu 18.04 (Intel(R) Dual Band Wireless AC 8265)"
date: 2019-05-17
forum: Networking &amp; Wireless
---

### Post by paleo229 on 2019-05-17
Hi. I use Xubuntu 18.04 for a year on my Thinkpad T470p (a laptop). From the beginning, the wifi crashed randomly once or twice a week, which forced me to reboot. This evening after I updated the OS and rebooted, and now the wifi crashes immediately. I can't use it at all.

```
$ ll /lib/firmware | grep iwlwifi-8265

-rw-r--r--  1 root root 2389968 Nov 17  2017 iwlwifi-8265-21.ucode
-rw-r--r--  1 root root 1811984 Apr 24  2018 iwlwifi-8265-22.ucode
-rw-r--r--  1 root root 2234528 Dec  5  2017 iwlwifi-8265-27.ucode
-rw-r--r--  1 root root 2307104 Dec  6  2017 iwlwifi-8265-31.ucode
-rw-r--r--  1 root root 2440780 Apr 25  2018 iwlwifi-8265-34.ucode
-rw-r--r--  1 root root 2498044 Apr 24 16:20 iwlwifi-8265-36.ucode
```

There is a recent firmware: 'iwlwifi-8265-36.ucode'. But the system use the previous version 'iwlwifi-8265-34.ucode'. How to use the last one?

```
$ modinfo iwlwifi

filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
…
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-34.ucode
firmware:       iwlwifi-8000C-34.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
…
srcversion:     1AD55A6BECD5B5DFB5BBF7E
…
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.15.0-50-generic SMP mod_unload 
signat:         PKCS#7
```

```
$ dmesg | grep iwlwifi

[   11.997372] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
[   12.022749] iwlwifi 0000:03:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
[   12.096659] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[   12.156942] iwlwifi 0000:03:00.0: base HW address: f8:34:41:41:a5:8c
[   12.235849] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[  123.068302] iwlwifi 0000:03:00.0: Error sending SCAN_REQ_UMAC: time out after 2000ms.
[  123.068314] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 58 write_ptr 59
[  123.087177] iwlwifi 0000:03:00.0: iwlwifi transaction failed, dumping registers
[  123.087178] iwlwifi 0000:03:00.0: iwlwifi device config registers:
[  123.087228] iwlwifi 0000:03:00.0: 00000000: 24fd8086 00100000 02800078 00000000 00000004 00000000 00000000 00000000
[  123.087230] iwlwifi 0000:03:00.0: 00000020: 00000000 00000000 00000000 10108086 00000000 000000c8 00000000 00000100
[  123.087231] iwlwifi 0000:03:00.0: iwlwifi device memory mapped registers:
[  123.087272] iwlwifi 0000:03:00.0: 00000000: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
[  123.087274] iwlwifi 0000:03:00.0: 00000020: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
[  123.087278] iwlwifi 0000:03:00.0: iwlwifi device AER capability structure:
[  123.087310] iwlwifi 0000:03:00.0: 00000000: 14010001 00100000 00000000 00462031 00002000 00002000 00000014 40000001
[  123.087311] iwlwifi 0000:03:00.0: 00000020: 0000000f f2200460 00000000
[  123.087313] iwlwifi 0000:03:00.0: iwlwifi parent port (0000:00:1c.0) config registers:
[  123.087338] iwlwifi 0000:00:1c.0: 00000000: a1108086 00100407 060400f1 00810000 00000000 00000000 00030300 200000f0
[  123.087340] iwlwifi 0000:00:1c.0: 00000020: f220f220 0001fff1 00000000 00000000 00000000 00000040 00000000 000001ff
[  123.087342] iwlwifi 0000:03:00.0: iwlwifi root port (0000:00:1c.0) AER cap structure:
[  123.087350] iwlwifi 0000:00:1c.0: 00000000: 14010001 00000000 00010000 00060011 00000000 00002000 00000000 00000000
[  123.087352] iwlwifi 0000:00:1c.0: 00000020: 00000000 00000000 00000000 00000007 00000000 000000e0
```

```
$ sudo journalctl -S "2019-05-17" | grep "iwlwifi"

May 17 18:04:52 hopws kernel: iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
May 17 18:04:52 hopws kernel: iwlwifi 0000:03:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
May 17 18:04:52 hopws kernel: iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
May 17 18:04:52 hopws kernel: iwlwifi 0000:03:00.0: base HW address: f8:34:41:41:a5:8c
May 17 18:04:52 hopws kernel: iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
May 17 18:04:56 hopws sensors[1574]: iwlwifi-virtual-0
May 17 18:04:57 hopws NetworkManager[1454]: <info>  [1558112697.7648] rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.0/0000:03:00.0/ieee80211/phy0/rfkill2) (driver iwlwifi)
May 17 18:05:49 hopws sudo[3336]:      hop : TTY=pts/0 ; PWD=/home/hop ; USER=root ; COMMAND=/sbin/modprobe iwlwifi
May 17 18:06:51 hopws kernel: iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
May 17 18:06:51 hopws kernel: iwlwifi 0000:03:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
May 17 18:06:51 hopws kernel: iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
May 17 18:06:51 hopws kernel: iwlwifi 0000:03:00.0: base HW address: f8:34:41:41:a5:8c
May 17 18:06:51 hopws kernel: iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
May 17 18:06:56 hopws sensors[1495]: iwlwifi-virtual-0
May 17 18:06:57 hopws NetworkManager[1410]: <info>  [1558112817.1443] rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.0/0000:03:00.0/ieee80211/phy0/rfkill2) (driver iwlwifi)
May 17 18:09:14 hopws kernel: iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
May 17 18:09:14 hopws kernel: iwlwifi 0000:03:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
May 17 18:09:14 hopws kernel: iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
May 17 18:09:14 hopws kernel: iwlwifi 0000:03:00.0: base HW address: f8:34:41:41:a5:8c
May 17 18:09:14 hopws kernel: iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
May 17 18:09:19 hopws sensors[1520]: iwlwifi-virtual-0
May 17 18:09:19 hopws NetworkManager[1501]: <info>  [1558112959.6273] rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.0/0000:03:00.0/ieee80211/phy0/rfkill2) (driver iwlwifi)
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: Error sending SCAN_REQ_UMAC: time out after 2000ms.
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: Current CMD queue read_ptr 58 write_ptr 59
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi transaction failed, dumping registers
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi device config registers:
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: 00000000: 24fd8086 00100000 02800078 00000000 00000004 00000000 00000000 00000000
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: 00000020: 00000000 00000000 00000000 10108086 00000000 000000c8 00000000 00000100
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi device memory mapped registers:
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: 00000000: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: 00000020: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi device AER capability structure:
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: 00000000: 14010001 00100000 00000000 00462031 00002000 00002000 00000014 40000001
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: 00000020: 0000000f f2200460 00000000
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi parent port (0000:00:1c.0) config registers:
May 17 18:11:05 hopws kernel: iwlwifi 0000:00:1c.0: 00000000: a1108086 00100407 060400f1 00810000 00000000 00000000 00030300 200000f0
May 17 18:11:05 hopws kernel: iwlwifi 0000:00:1c.0: 00000020: f220f220 0001fff1 00000000 00000000 00000000 00000040 00000000 000001ff
May 17 18:11:05 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi root port (0000:00:1c.0) AER cap structure:
May 17 18:11:05 hopws kernel: iwlwifi 0000:00:1c.0: 00000000: 14010001 00000000 00010000 00060011 00000000 00002000 00000000 00000000
May 17 18:11:05 hopws kernel: iwlwifi 0000:00:1c.0: 00000020: 00000000 00000000 00000000 00000007 00000000 000000e0
```

If someone finds a solution or a workaround it will save me!

---

### Post by paleo229 on 2019-05-18
I found a solution here: [https://ubuntuforums.org/showthread.php?t=2376104](https://ubuntuforums.org/showthread.php?t=2376104) .

Edit file "/etc/modprobe.d/iwlwifi.conf", then append a new line:

```
options iwlwifi 11n_disable=8
```

And reboot.
It works now. Hope it will be stable.

EDIT: After several hours, the wifi crashes again:

```
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: Error sending STATISTICS_CMD: time out after 2000ms.
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: Current CMD queue read_ptr 73 write_ptr 74
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi transaction failed, dumping registers
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi device config registers:
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: 00000000: 24fd8086 00100000 02800078 00000000 00000004 00000000 00000000 00000000
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: 00000020: 00000000 00000000 00000000 10108086 00000000 000000c8 00000000 00000100
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi device memory mapped registers:
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: 00000000: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: 00000020: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi device AER capability structure:
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: 00000000: 14010001 00100000 00000000 00462031 00002000 00002000 00000014 40000001
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: 00000020: 0000000f f2200460 00000000
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi parent port (0000:00:1c.0) config registers:
May 18 08:57:50 hopws kernel: iwlwifi 0000:00:1c.0: 00000000: a1108086 00100407 060400f1 00810000 00000000 00000000 00030300 200000f0
May 18 08:57:50 hopws kernel: iwlwifi 0000:00:1c.0: 00000020: f220f220 0001fff1 00000000 00000000 00000000 00000040 00000000 000001ff
May 18 08:57:50 hopws kernel: iwlwifi 0000:03:00.0: iwlwifi root port (0000:00:1c.0) AER cap structure:
May 18 08:57:50 hopws kernel: iwlwifi 0000:00:1c.0: 00000000: 14010001 00000000 00010000 00060011 00000001 00002000 00000000 00000000
May 18 08:57:50 hopws kernel: iwlwifi 0000:00:1c.0: 00000020: 00000000 00000000 00000000 00000000 00000003 000000e0
May 18 08:57:50 hopws kernel: ------------[ cut here ]------------
May 18 08:57:50 hopws kernel: Timeout waiting for hardware access (CSR_GP_CNTRL 0xffffffff)
May 18 08:57:50 hopws kernel: WARNING: CPU: 0 PID: 1482 at /build/linux-3btXxq/linux-4.15.0/drivers/net/wireless/intel/iwlwifi/pcie/trans.c:1973 iwl_trans_pcie_grab_nic_access+0xea/0xf0 [iwlwifi]
```

Then, on a next crash:

```
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: HW error, resetting before reading
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: Loaded firmware version: 34.0.1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | ADVANCED_SYSASSERT
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | trm_hw_status0
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | trm_hw_status1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | branchlink2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | interruptlink1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | data1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x8841B3D8 | data2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFFA74D | data3
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x9362DE00 | beacon time
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFFFFFF | tsf low
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | time gp1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x000007D0 | time gp2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | uCode revision type
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x8841B4B8 | uCode version major
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFFA74D | uCode version minor
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xA62E8F00 | hw version
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFF8F7C | board version
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFF8F7C | hcmd
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr0
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x1D1525C0 | isr2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFFCB64 | isr3
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000408 | isr4
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | last cmd Id
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000001 | wait_event
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000006 | l2p_addr_match
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | lmpm_pmg_sel
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000007 | timestamp
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: Status: 0x00000100, count: -22707
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xC07BF515 | ADVANCED_SYSASSERT
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFFFFFF | umac branchlink1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xA62E0018 | umac branchlink2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFF8F7C | umac interruptlink1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00A01C30 | umac interruptlink2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | umac data1
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000080 | umac data2
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | umac data3
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x8841B4E0 | umac major
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFFA74D | umac minor
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xC07AE82D | frame pointer
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0xFFFFFFFF | stack pointer
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000246 | last host cmd
May 18 09:30:04 hopws kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr status reg
May 18 09:30:04 hopws kernel: ieee80211 phy0: Hardware restart was requested
May 18 09:30:07 hopws kernel: iwlwifi 0000:03:00.0: Could not load the [0] uCode section
May 18 09:30:07 hopws kernel: iwlwifi 0000:03:00.0: Failed to start INIT ucode: -5
May 18 09:30:07 hopws kernel: iwlwifi 0000:03:00.0: Failed to run INIT ucode: -5
May 18 09:30:07 hopws kernel: iwlwifi 0000:03:00.0: Failed to start RT ucode: -5
May 18 09:30:09 hopws kernel: ------------[ cut here ]------------
May 18 09:30:09 hopws kernel: Hardware became unavailable during restart.
```

---

### Post by jeremy31 on 2019-05-18
See if disabling wifi power management helps
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by paleo229 on 2019-05-18
> **jeremy31 said:**
> See if disabling wifi power management helps

Thank you for the response.

I tried to disable the wifi power management in "/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf", with "wifi.powersave = 2".
No effect.

I also tried to append " pci=noaer" in "/etc/default/grub". In the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"". Then I did "sudo update-grub".
No effect.

The wifi crashes several time a hour.

---

### Post by jeremy31 on 2019-05-18
Try another grub edit to include ```
pcie_aspm=off
```

---

### Post by paleo229 on 2019-05-18
I tried GRUB options "pcie_aspm=off" alone then with "pci=noaer". The wifi crashed in both cases.

How to use the last version of the firmware ("iwlwifi-8265-36.ucode" instead of "iwlwifi-8265-34.ucode")?

---

### Post by jeremy31 on 2019-05-18
The highest version firmware is limited by source code in the kernel module iwlmvm IIRC

---

