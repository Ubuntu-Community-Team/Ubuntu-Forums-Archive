---
title: "Intel Firmware Issues w/ Ubuntu 17.10"
date: 2018-03-22
forum: Networking &amp; Wireless
---

### Post by robertzito on 2018-03-22
I performed a fresh install of Ubuntu 17.10, no upgrade formatted and installed. Now I am seeing the below error with my wifi firmware this is occurring on both kernels but I upgraded to 4.13.0-37-generic
and still getting the below error. I did some searching and this looks like an old bug, is there any fix?
  

```
~ dmesg | grep wifi                                                       
[    2.701939] iwlwifi 0000:6e:00.0: enabling device (0000 -> 0002)
[    2.705030] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8265-33.ucode failed with error -2
[    2.705045] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8265-32.ucode failed with error -2
[    2.705056] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8265-31.ucode failed with error -2
[    2.705065] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8265-30.ucode failed with error -2
[    2.705074] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8265-29.ucode failed with error -2
[    2.705082] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8265-28.ucode failed with error -2
[    2.707271] iwlwifi 0000:6e:00.0: loaded firmware version 27.541033.0 op_mode iwlmvm
[    2.726038] iwlwifi 0000:6e:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    2.779534] iwlwifi 0000:6e:00.0: base HW address: 00:28:f8:51:84:39
[    3.133341] iwlwifi 0000:6e:00.0 wlp110s0: renamed from wlan0
[  550.278157] iwlwifi 0000:6e:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  550.278306] iwlwifi 0000:6e:00.0: Start IWL Error Log Dump:
[  550.278313] iwlwifi 0000:6e:00.0: Status: 0x00000200, count: 6
[  550.278319] iwlwifi 0000:6e:00.0: Loaded firmware version: 27.541033.0
[  550.278326] iwlwifi 0000:6e:00.0: 0x00000038 | BAD_COMMAND                 
[  550.278332] iwlwifi 0000:6e:00.0: 0x00000200 | trm_hw_status0
[  550.278337] iwlwifi 0000:6e:00.0: 0x00000000 | trm_hw_status1
[  550.278343] iwlwifi 0000:6e:00.0: 0x000243A0 | branchlink2
[  550.278348] iwlwifi 0000:6e:00.0: 0x000391BE | interruptlink1
[  550.278353] iwlwifi 0000:6e:00.0: 0x00000000 | interruptlink2
[  550.278359] iwlwifi 0000:6e:00.0: 0x003B001C | data1
[  550.278364] iwlwifi 0000:6e:00.0: 0x0000083C | data2
[  550.278369] iwlwifi 0000:6e:00.0: 0x0000003C | data3
[  550.278375] iwlwifi 0000:6e:00.0: 0x29816ED1 | beacon time
[  550.278382] iwlwifi 0000:6e:00.0: 0x88B3B129 | tsf low
[  550.278390] iwlwifi 0000:6e:00.0: 0x00000079 | tsf hi
[  550.278397] iwlwifi 0000:6e:00.0: 0x00000000 | time gp1
[  550.278404] iwlwifi 0000:6e:00.0: 0x208C8A7D | time gp2
[  550.278411] iwlwifi 0000:6e:00.0: 0x00000001 | uCode revision type
[  550.278418] iwlwifi 0000:6e:00.0: 0x0000001B | uCode version major
[  550.278426] iwlwifi 0000:6e:00.0: 0x00084169 | uCode version minor
[  550.278433] iwlwifi 0000:6e:00.0: 0x00000230 | hw version
[  550.278440] iwlwifi 0000:6e:00.0: 0x00C89000 | board version
[  550.278447] iwlwifi 0000:6e:00.0: 0x003B001C | hcmd
[  550.278455] iwlwifi 0000:6e:00.0: 0x24022080 | isr0
[  550.278463] iwlwifi 0000:6e:00.0: 0x10800000 | isr1
[  550.278470] iwlwifi 0000:6e:00.0: 0x2820180A | isr2
[  550.278477] iwlwifi 0000:6e:00.0: 0x00417CC0 | isr3
[  550.278484] iwlwifi 0000:6e:00.0: 0x00000000 | isr4
[  550.278490] iwlwifi 0000:6e:00.0: 0x0A24001C | last cmd Id
[  550.278496] iwlwifi 0000:6e:00.0: 0x00000000 | wait_event
[  550.278501] iwlwifi 0000:6e:00.0: 0x00004288 | l2p_control
[  550.278506] iwlwifi 0000:6e:00.0: 0x00018034 | l2p_duration
[  550.278512] iwlwifi 0000:6e:00.0: 0x000003BF | l2p_mhvalid
[  550.278517] iwlwifi 0000:6e:00.0: 0x000000E7 | l2p_addr_match
[  550.278522] iwlwifi 0000:6e:00.0: 0x0000000D | lmpm_pmg_sel
[  550.278527] iwlwifi 0000:6e:00.0: 0x15062059 | timestamp
[  550.278533] iwlwifi 0000:6e:00.0: 0x000090A0 | flow_handler
[  550.278598] iwlwifi 0000:6e:00.0: Start IWL Error Log Dump:
[  550.278604] iwlwifi 0000:6e:00.0: Status: 0x00000200, count: 7
[  550.278610] iwlwifi 0000:6e:00.0: 0x00000070 | ADVANCED_SYSASSERT
[  550.278615] iwlwifi 0000:6e:00.0: 0x00000000 | umac branchlink1
[  550.278620] iwlwifi 0000:6e:00.0: 0xC0085C58 | umac branchlink2
[  550.278626] iwlwifi 0000:6e:00.0: 0xC0088EBA | umac interruptlink1
[  550.278631] iwlwifi 0000:6e:00.0: 0xC0083438 | umac interruptlink2
[  550.278636] iwlwifi 0000:6e:00.0: 0x00000800 | umac data1
[  550.278641] iwlwifi 0000:6e:00.0: 0xC0083438 | umac data2
[  550.278646] iwlwifi 0000:6e:00.0: 0xDEADBEEF | umac data3
[  550.278651] iwlwifi 0000:6e:00.0: 0x0000001B | umac major
[  550.278656] iwlwifi 0000:6e:00.0: 0x00084169 | umac minor
[  550.278661] iwlwifi 0000:6e:00.0: 0xC088627C | frame pointer
[  550.278666] iwlwifi 0000:6e:00.0: 0xC088627C | stack pointer
[  550.278672] iwlwifi 0000:6e:00.0: 0x003B001C | last host cmd
[  550.278677] iwlwifi 0000:6e:00.0: 0x00000000 | isr status reg
[  550.278704] iwlwifi 0000:6e:00.0: FW Error notification: type 0x00000000 cmd_id 0x1C
[  550.278710] iwlwifi 0000:6e:00.0: FW Error notification: seq 0x003B service 0x0000001C
[  550.278716] iwlwifi 0000:6e:00.0: FW Error notification: timestamp 0x        208D92F0
```

---

### Post by jeremy31 on 2018-03-22
*Thread moved to **Networking & Wireless**.*  Ubuntu 17.10 is no longer the development version

---

### Post by chili555 on 2018-03-22
Please run and post:```
sudo dpkg -s linux-firmware
ls /lib/firmware | grep 8265
```

---

### Post by robertzito on 2018-03-22
```
Package: linux-firmware
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 210540
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Version: 1.169.3
Replaces: atmel-firmware, linux-firmware-snapdragon (<= 1.2-0ubuntu1), linux-restricted-common
Provides: atmel-firmware
Breaks: linux-firmware-snapdragon (<= 1.2-0ubuntu1)
Conflicts: atmel-firmware
Description: Firmware for Linux kernel drivers
 This package provides firmware used by Linux kernel drivers.


iwlwifi-8265-21.ucode
iwlwifi-8265-22.ucode
iwlwifi-8265-27.ucode
iwlwifi-8265-31.ucode
iwlwifi-8265-34.ucode
```

---

### Post by chili555 on 2018-03-22
>  Direct firmware load for iwlwifi-8265-31.ucode failed with error -2But you have -31:> iwlwifi-8265-21.ucode
iwlwifi-8265-22.ucode
iwlwifi-8265-27.ucode
[COLOR="#FF0000"]iwlwifi-8265-31.ucode[/COLOR]
iwlwifi-8265-34.ucodeIs it readable, writable and not corrupt?```
ls -al /lib/firmware/iwlwifi-8265-31.ucode
md5sum /lib/firmware/iwlwifi-8265-31.ucode
```Fascinating.

---

### Post by robertzito on 2018-03-22
Here is the output

```
 ~ ls -al 
/lib/firmware/iwlwifi-8265-31.ucode
-rw-r--r-- 1 root root 2307104 Dec  6 09:43 /lib/firmware/iwlwifi-8265-31.ucode
```


```
~ md5sum /lib/firmware/iwlwifi-8265-31.ucode
fcb3f15b164f5f90d084de652091691b  /lib/firmware/iwlwifi-8265-31.ucode 
```

dsmsg is clean no but syslogs has 

still getting 
```

[  824.287230] ieee80211 phy0: Hardware restart was requested
[  824.287235] iwlwifi 0000:6e:00.0: FW Error notification: type 0x00000000 cmd_id 0x1C
[  824.287237] iwlwifi 0000:6e:00.0: FW Error notification: seq 0x001D service 0x0000001C
[  824.287238] iwlwifi 0000:6e:00.0: FW Error notification: timestamp 0x        30DAD962
```

---

### Post by robertzito on 2018-03-23
The distro upgrade stopped the errors till I rebooted, here is what I am getting

 ```
2252.853449] iwlwifi 0000:6e:00.0: Microcode SW error detected.  Restarting 0x82000000.
Mar 23 00:18:51 pop-os kernel: [ 2252.853596] iwlwifi 0000:6e:00.0: Start IWL Error Log Dump:
Mar 23 00:18:51 pop-os kernel: [ 2252.853604] iwlwifi 0000:6e:00.0: Status: 0x00000200, count: 6
Mar 23 00:18:51 pop-os kernel: [ 2252.853609] iwlwifi 0000:6e:00.0: Loaded firmware version: 31.560484.0
Mar 23 00:18:51 pop-os kernel: [ 2252.853616] iwlwifi 0000:6e:00.0: 0x00000038 | BAD_COMMAND                 
Mar 23 00:18:51 pop-os kernel: [ 2252.853621] iwlwifi 0000:6e:00.0: 0x00000280 | trm_hw_status0
Mar 23 00:18:51 pop-os kernel: [ 2252.853627] iwlwifi 0000:6e:00.0: 0x00000000 | trm_hw_status1
Mar 23 00:18:51 pop-os kernel: [ 2252.853632] iwlwifi 0000:6e:00.0: 0x0002495C | branchlink2
Mar 23 00:18:51 pop-os kernel: [ 2252.853637] iwlwifi 0000:6e:00.0: 0x0003962E | interruptlink1
Mar 23 00:18:51 pop-os kernel: [ 2252.853642] iwlwifi 0000:6e:00.0: 0x00000000 | interruptlink2
Mar 23 00:18:51 pop-os kernel: [ 2252.853648] iwlwifi 0000:6e:00.0: 0x00EF001C | data1
Mar 23 00:18:51 pop-os kernel: [ 2252.853653] iwlwifi 0000:6e:00.0: 0x000000F0 | data2
Mar 23 00:18:51 pop-os kernel: [ 2252.853658] iwlwifi 0000:6e:00.0: 0x000000F0 | data3
Mar 23 00:18:51 pop-os kernel: [ 2252.853664] iwlwifi 0000:6e:00.0: 0x66001328 | beacon time
Mar 23 00:18:51 pop-os kernel: [ 2252.853669] iwlwifi 0000:6e:00.0: 0xFD03BCD6 | tsf low
Mar 23 00:18:51 pop-os kernel: [ 2252.853674] iwlwifi 0000:6e:00.0: 0x0000007E | tsf hi
Mar 23 00:18:51 pop-os kernel: [ 2252.853704] iwlwifi 0000:6e:00.0: 0x00000000 | time gp1
Mar 23 00:18:51 pop-os kernel: [ 2252.853722] iwlwifi 0000:6e:00.0: 0x860106DB | time gp2
Mar 23 00:18:51 pop-os kernel: [ 2252.853738] iwlwifi 0000:6e:00.0: 0x00000001 | uCode revision type
Mar 23 00:18:51 pop-os kernel: [ 2252.853755] iwlwifi 0000:6e:00.0: 0x0000001F | uCode version major
Mar 23 00:18:51 pop-os kernel: [ 2252.853771] iwlwifi 0000:6e:00.0: 0x00088D64 | uCode version minor
Mar 23 00:18:51 pop-os kernel: [ 2252.853788] iwlwifi 0000:6e:00.0: 0x00000230 | hw version
Mar 23 00:18:51 pop-os kernel: [ 2252.853805] iwlwifi 0000:6e:00.0: 0x00C89000 | board version
Mar 23 00:18:51 pop-os kernel: [ 2252.853818] iwlwifi 0000:6e:00.0: 0x00EF001C | hcmd
Mar 23 00:18:51 pop-os kernel: [ 2252.853823] iwlwifi 0000:6e:00.0: 0x20022082 | isr0
Mar 23 00:18:51 pop-os kernel: [ 2252.853828] iwlwifi 0000:6e:00.0: 0x10800000 | isr1
Mar 23 00:18:51 pop-os kernel: [ 2252.853833] iwlwifi 0000:6e:00.0: 0x2820180A | isr2
Mar 23 00:18:51 pop-os kernel: [ 2252.853838] iwlwifi 0000:6e:00.0: 0x00413CC0 | isr3
Mar 23 00:18:51 pop-os kernel: [ 2252.853843] iwlwifi 0000:6e:00.0: 0x00000000 | isr4
Mar 23 00:18:51 pop-os kernel: [ 2252.853849] iwlwifi 0000:6e:00.0: 0x0A22001C | last cmd Id
Mar 23 00:18:51 pop-os kernel: [ 2252.853854] iwlwifi 0000:6e:00.0: 0x00000000 | wait_event
Mar 23 00:18:51 pop-os kernel: [ 2252.853859] iwlwifi 0000:6e:00.0: 0x00004288 | l2p_control
Mar 23 00:18:51 pop-os kernel: [ 2252.853865] iwlwifi 0000:6e:00.0: 0x00018024 | l2p_duration
Mar 23 00:18:51 pop-os kernel: [ 2252.853870] iwlwifi 0000:6e:00.0: 0x00000000 | l2p_mhvalid
Mar 23 00:18:51 pop-os kernel: [ 2252.853875] iwlwifi 0000:6e:00.0: 0x000000E7 | l2p_addr_match
Mar 23 00:18:51 pop-os kernel: [ 2252.853880] iwlwifi 0000:6e:00.0: 0x0000000D | lmpm_pmg_sel
Mar 23 00:18:51 pop-os kernel: [ 2252.853886] iwlwifi 0000:6e:00.0: 0x13091828 | timestamp
Mar 23 00:18:51 pop-os kernel: [ 2252.853891] iwlwifi 0000:6e:00.0: 0x00006080 | flow_handler
Mar 23 00:18:51 pop-os kernel: [ 2252.853956] iwlwifi 0000:6e:00.0: Start IWL Error Log Dump:
Mar 23 00:18:51 pop-os kernel: [ 2252.853974] iwlwifi 0000:6e:00.0: Status: 0x00000200, count: 7
Mar 23 00:18:51 pop-os kernel: [ 2252.853989] iwlwifi 0000:6e:00.0: 0x00000070 | ADVANCED_SYSASSERT
Mar 23 00:18:51 pop-os kernel: [ 2252.853999] iwlwifi 0000:6e:00.0: 0x00000000 | umac branchlink1
Mar 23 00:18:51 pop-os kernel: [ 2252.854004] iwlwifi 0000:6e:00.0: 0xC0086950 | umac branchlink2
Mar 23 00:18:51 pop-os kernel: [ 2252.854010] iwlwifi 0000:6e:00.0: 0xC00842BC | umac interruptlink1
Mar 23 00:18:51 pop-os kernel: [ 2252.854015] iwlwifi 0000:6e:00.0: 0xC00842BC | umac interruptlink2
Mar 23 00:18:51 pop-os kernel: [ 2252.854020] iwlwifi 0000:6e:00.0: 0x00000800 | umac data1
Mar 23 00:18:51 pop-os kernel: [ 2252.854025] iwlwifi 0000:6e:00.0: 0xC00842BC | umac data2
Mar 23 00:18:51 pop-os kernel: [ 2252.854031] iwlwifi 0000:6e:00.0: 0xDEADBEEF | umac data3
Mar 23 00:18:51 pop-os kernel: [ 2252.854036] iwlwifi 0000:6e:00.0: 0x0000001F | umac major
Mar 23 00:18:51 pop-os kernel: [ 2252.854041] iwlwifi 0000:6e:00.0: 0x00088D64 | umac minor
Mar 23 00:18:51 pop-os kernel: [ 2252.854046] iwlwifi 0000:6e:00.0: 0xC088627C | frame pointer
Mar 23 00:18:51 pop-os kernel: [ 2252.854051] iwlwifi 0000:6e:00.0: 0xC088627C | stack pointer
Mar 23 00:18:51 pop-os kernel: [ 2252.854056] iwlwifi 0000:6e:00.0: 0x00EF001C | last host cmd
Mar 23 00:18:51 pop-os kernel: [ 2252.854061] iwlwifi 0000:6e:00.0: 0x00000000 | isr status reg
Mar 23 00:18:51 pop-os kernel: [ 2252.854070] ieee80211 phy0: Hardware restart was requested
Mar 23 00:18:51 pop-os kernel: [ 2252.854084] iwlwifi 0000:6e:00.0: FW Error notification: type 0x00000000 cmd_id 0x1C
Mar 23 00:18:51 pop-os kernel: [ 2252.854090] iwlwifi 0000:6e:00.0: FW Error notification: seq 0x00EF service 0x0000001C
Mar 23 00:18:51 pop-os kernel: [ 2252.854096] iwlwifi 0000:6e:00.0: FW Error notification: timestamp 0x        8603D2DA
Mar 23 00:18:53 pop-os kernel: [ 2254.807824] iwlwifi 0000:6e:00.0: Microcode SW error detected.  Restarting 0x82000000.
Mar 23 00:18:53 pop-os kernel: [ 2254.807970] iwlwifi 0000:6e:00.0: Start IWL Error Log Dump:
Mar 23 00:18:53 pop-os kernel: [ 2254.807978] iwlwifi 0000:6e:00.0: Status: 0x00000200, count: 6
Mar 23 00:18:53 pop-os kernel: [ 2254.807984] iwlwifi 0000:6e:00.0: Loaded firmware version: 31.560484.0
Mar 23 00:18:53 pop-os kernel: [ 2254.807990] iwlwifi 0000:6e:00.0: 0x00000038 | BAD_COMMAND                 
Mar 23 00:18:53 pop-os kernel: [ 2254.807996] iwlwifi 0000:6e:00.0: 0x00000200 | trm_hw_status0
Mar 23 00:18:53 pop-os kernel: [ 2254.808001] iwlwifi 0000:6e:00.0: 0x00000000 | trm_hw_status1
Mar 23 00:18:53 pop-os kernel: [ 2254.808007] iwlwifi 0000:6e:00.0: 0x0002495C | branchlink2
Mar 23 00:18:53 pop-os kernel: [ 2254.808012] iwlwifi 0000:6e:00.0: 0x0003962E | interruptlink1
Mar 23 00:18:53 pop-os kernel: [ 2254.808017] iwlwifi 0000:6e:00.0: 0x00000000 | interruptlink2
Mar 23 00:18:53 pop-os kernel: [ 2254.808022] iwlwifi 0000:6e:00.0: 0x0064001C | data1
Mar 23 00:18:53 pop-os kernel: [ 2254.808028] iwlwifi 0000:6e:00.0: 0x00000065 | data2
Mar 23 00:18:53 pop-os kernel: [ 2254.808033] iwlwifi 0000:6e:00.0: 0x00000065 | data3
Mar 23 00:18:53 pop-os kernel: [ 2254.808038] iwlwifi 0000:6e:00.0: 0xFFF500F9 | beacon time
Mar 23 00:18:53 pop-os kernel: [ 2254.808043] iwlwifi 0000:6e:00.0: 0xFD218F08 | tsf low
Mar 23 00:18:53 pop-os kernel: [ 2254.808048] iwlwifi 0000:6e:00.0: 0x0000007E | tsf hi
Mar 23 00:18:53 pop-os kernel: [ 2254.808054] iwlwifi 0000:6e:00.0: 0x00000000 | time gp1
Mar 23 00:18:53 pop-os kernel: [ 2254.808059] iwlwifi 0000:6e:00.0: 0x00138A05 | time gp2
Mar 23 00:18:53 pop-os kernel: [ 2254.808064] iwlwifi 0000:6e:00.0: 0x00000001 | uCode revision type
Mar 23 00:18:53 pop-os kernel: [ 2254.808069] iwlwifi 0000:6e:00.0: 0x0000001F | uCode version major
Mar 23 00:18:53 pop-os kernel: [ 2254.808075] iwlwifi 0000:6e:00.0: 0x00088D64 | uCode version minor
Mar 23 00:18:53 pop-os kernel: [ 2254.808080] iwlwifi 0000:6e:00.0: 0x00000230 | hw version
Mar 23 00:18:53 pop-os kernel: [ 2254.808085] iwlwifi 0000:6e:00.0: 0x00C89000 | board version
Mar 23 00:18:53 pop-os kernel: [ 2254.808090] iwlwifi 0000:6e:00.0: 0x0064001C | hcmd
Mar 23 00:18:53 pop-os kernel: [ 2254.808095] iwlwifi 0000:6e:00.0: 0x24022080 | isr0
Mar 23 00:18:53 pop-os kernel: [ 2254.808101] iwlwifi 0000:6e:00.0: 0x01000000 | isr1
Mar 23 00:18:53 pop-os kernel: [ 2254.808106] iwlwifi 0000:6e:00.0: 0x2820180A | isr2
Mar 23 00:18:53 pop-os kernel: [ 2254.808111] iwlwifi 0000:6e:00.0: 0x00417CC0 | isr3
Mar 23 00:18:53 pop-os kernel: [ 2254.808116] iwlwifi 0000:6e:00.0: 0x00000000 | isr4
Mar 23 00:18:53 pop-os kernel: [ 2254.808121] iwlwifi 0000:6e:00.0: 0x0AF0001C | last cmd Id
Mar 23 00:18:53 pop-os kernel: [ 2254.808126] iwlwifi 0000:6e:00.0: 0x00000000 | wait_event
Mar 23 00:18:53 pop-os kernel: [ 2254.808131] iwlwifi 0000:6e:00.0: 0x00004288 | l2p_control
Mar 23 00:18:53 pop-os kernel: [ 2254.808137] iwlwifi 0000:6e:00.0: 0x00018034 | l2p_duration
Mar 23 00:18:53 pop-os kernel: [ 2254.808142] iwlwifi 0000:6e:00.0: 0x000003BF | l2p_mhvalid
Mar 23 00:18:53 pop-os kernel: [ 2254.808147] iwlwifi 0000:6e:00.0: 0x000000E7 | l2p_addr_match
Mar 23 00:18:53 pop-os kernel: [ 2254.808152] iwlwifi 0000:6e:00.0: 0x0000000D | lmpm_pmg_sel
Mar 23 00:18:53 pop-os kernel: [ 2254.808158] iwlwifi 0000:6e:00.0: 0x13091828 | timestamp
Mar 23 00:18:53 pop-os kernel: [ 2254.808163] iwlwifi 0000:6e:00.0: 0x00005860 | flow_handler
Mar 23 00:18:53 pop-os kernel: [ 2254.808227] iwlwifi 0000:6e:00.0: Start IWL Error Log Dump:
Mar 23 00:18:53 pop-os kernel: [ 2254.808233] iwlwifi 0000:6e:00.0: Status: 0x00000200, count: 7
Mar 23 00:18:53 pop-os kernel: [ 2254.808239] iwlwifi 0000:6e:00.0: 0x00000070 | ADVANCED_SYSASSERT
Mar 23 00:18:53 pop-os kernel: [ 2254.808244] iwlwifi 0000:6e:00.0: 0x00000000 | umac branchlink1
Mar 23 00:18:53 pop-os kernel: [ 2254.808249] iwlwifi 0000:6e:00.0: 0xC0086950 | umac branchlink2
Mar 23 00:18:53 pop-os kernel: [ 2254.808254] iwlwifi 0000:6e:00.0: 0xC00842BC | umac interruptlink1
Mar 23 00:18:53 pop-os kernel: [ 2254.808260] iwlwifi 0000:6e:00.0: 0xC008C6BE | umac interruptlink2
Mar 23 00:18:53 pop-os kernel: [ 2254.808265] iwlwifi 0000:6e:00.0: 0x00000800 | umac data1
Mar 23 00:18:53 pop-os kernel: [ 2254.808270] iwlwifi 0000:6e:00.0: 0xC008C6BE | umac data2
Mar 23 00:18:53 pop-os kernel: [ 2254.808275] iwlwifi 0000:6e:00.0: 0xDEADBEEF | umac data3
Mar 23 00:18:53 pop-os kernel: [ 2254.808280] iwlwifi 0000:6e:00.0: 0x0000001F | umac major
Mar 23 00:18:53 pop-os kernel: [ 2254.808285] iwlwifi 0000:6e:00.0: 0x00088D64 | umac minor
Mar 23 00:18:53 pop-os kernel: [ 2254.808290] iwlwifi 0000:6e:00.0: 0xC088628C | frame pointer
Mar 23 00:18:53 pop-os kernel: [ 2254.808295] iwlwifi 0000:6e:00.0: 0xC088628C | stack pointer
Mar 23 00:18:53 pop-os kernel: [ 2254.808300] iwlwifi 0000:6e:00.0: 0x0064001C | last host cmd
Mar 23 00:18:53 pop-os kernel: [ 2254.808306] iwlwifi 0000:6e:00.0: 0x00000000 | isr status reg
Mar 23 00:18:53 pop-os kernel: [ 2254.808313] ieee80211 phy0: Hardware restart was requested
Mar 23 00:18:53 pop-os kernel: [ 2254.808333] iwlwifi 0000:6e:00.0: FW Error notification: type 0x00000000 cmd_id 0x1C
Mar 23 00:18:53 pop-os kernel: [ 2254.808339] iwlwifi 0000:6e:00.0: FW Error notification: seq 0x0064 service 0x0000001C
Mar 23 00:18:53 pop-os kernel: [ 2254.808345] iwlwifi 0000:6e:00.0: FW Error notification: timestamp 0x          138A02
Mar 23 00:19:53 pop-os gnome-shell[2032]: Ignoring excess values in shadow definition
```

---

### Post by robertzito on 2018-03-26
Anything on this?

---

### Post by chili555 on 2018-03-26
Grasping at straws a bit here. Let's try to stop the apparently broken -27 from loading and see what happens.

```
sudo mv /lib/firmware/iwlwifi-8265-27.ucode  /lib/firmware/iwlwifi-8265-27.bak
```

Reboot and show us:```
dmesg | grep iwl
```

--------------------------
Possible reference: [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)
Intel says the correct firmware version is -22.

---

