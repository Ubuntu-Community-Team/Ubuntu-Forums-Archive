---
title: "Intel AX200 not working... Firmware not found"
date: 2019-11-27
forum: Networking &amp; Wireless
---

### Post by dxpolo on 2019-11-27
Hello,
My intel wifi network has stopped working:

iwlwifi: probe of 0000:3e:00.0 failed with error -110

 I think that it's a problem with firmware, I've checked the firmwares and I see that a lot of then are not avaliable:

firmware:       iwlwifi-cc-a0-52.ucode

Does anybody know where to download it?
I've been searching, but didn't found it.

thanks in advance

---

### Post by chili555 on 2019-11-27
I'm skeptical that it's the firmware. Let's dig deeper:

```
lspci -nnk | grep 0280 -A3
dmesg | grep iwl
```Please ost the results.

---

### Post by dxpolo on 2019-11-28
Hello:
dani@omen:~$ lspci -nnk | grep 0280 -A3
3e:00.0 Network controller [0280]: Intel Corporation Device [8086:2723] (rev 1a)
    Subsystem: Intel Corporation Device [8086:0084]
    Kernel modules: iwlwifi

dani@omen:~$ dmesg | grep iwl
[    3.442209] Loading modules backported from iwlwifi
[    3.442209] iwlwifi-stack-public:master:8042:654c426c
[    3.462840] iwlwifi 0000:3e:00.0: enabling device (0000 -> 0002)
[    3.959950] iwlwifi: probe of 0000:3e:00.0 failed with error -110


dani@omen:~$ modinfo iwlwifi
filename:       /lib/modules/5.0.0-36-generic/updates/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
version:        iwlwifi-stack-public:master:8042:654c426c
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-36.ucode
firmware:       iwlwifi-8000C-36.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-46.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-46.ucode
firmware:       iwlwifi-ty-a0-gf-a0-52.ucode
firmware:       iwlwifi-so-a0-gf-a0-52.ucode
firmware:       iwlwifi-so-a0-hr-b0-52.ucode
firmware:       iwlwifi-so-a0-jf-b0-52.ucode
firmware:       iwlwifi-cc-a0-52.ucode


And I don't find *52* firmware.

Thanks in advance

---

### Post by dxpolo on 2019-11-28
Don't know why.... but it has started to work again....
dani@omen:~$ dmesg |grep iwl
[    3.350727] Loading modules backported from iwlwifi
[    3.350728] iwlwifi-stack-public:master:8042:654c426c
[    3.364946] iwlwifi 0000:3e:00.0: enabling device (0000 -> 0002)
[    3.376720] iwlwifi 0000:3e:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    3.376846] iwlwifi 0000:3e:00.0: Direct firmware load for iwlwifi-cc-a0-52.ucode failed with error -2
[    3.376959] iwlwifi 0000:3e:00.0: Direct firmware load for iwlwifi-cc-a0-51.ucode failed with error -2
[    3.377065] iwlwifi 0000:3e:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[    3.377070] iwlwifi 0000:3e:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[    3.378458] iwlwifi 0000:3e:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    3.378461] iwlwifi 0000:3e:00.0: Found debug destination: EXTERNAL_DRAM
[    3.378462] iwlwifi 0000:3e:00.0: Found debug configuration: 0
[    3.378643] iwlwifi 0000:3e:00.0: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[    3.404820] iwlwifi 0000:3e:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    3.419231] iwlwifi 0000:3e:00.0: Applying debug destination EXTERNAL_DRAM
[    3.419378] iwlwifi 0000:3e:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    3.585650] iwlwifi 0000:3e:00.0: base HW address: d0:ab:d5:19:bf:40
[    3.817090] iwlwifi 0000:3e:00.0 wlp62s0: renamed from wlan0
[    4.083386] iwlwifi 0000:3e:00.0: Applying debug destination EXTERNAL_DRAM
[    4.249541] iwlwifi 0000:3e:00.0: FW already configured (0) - re-configuring
[    4.257766] iwlwifi 0000:3e:00.0: BIOS contains WGDS but no WRDS


Thanks

---

