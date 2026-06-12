---
title: "Intel AX200 worked fine on initial install of 20.04, on re-install doesnt work"
date: 2020-06-16
forum: Networking &amp; Wireless
---

### Post by Ranbunta_Bantubunt on 2020-06-16
Hi, I am looking at what is (to me) a fairly perplexing situation.

I installed ubuntu on an extra Nvme SSD on a razer blade 17" early 2019. This uses the Intel AX200 wifi chip. One nvme slot has the original windows SSD, I added another one and installed ubuntu 20.04 with almost-full disk encryption as described here:

[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

secure boot is off

Everything worked out of the box, except a minor hibernation glitch which I fixed by doing this:

[https://danmackinlay.name/notebook/comfy_razer.html](https://danmackinlay.name/notebook/comfy_razer.html)
> 
**Keeps on suspending again after suspending once**

 After the laptop has gone to sleep one time it has narcolepsy and keeps sleeping again?
 I found this fix somewhere: append button.lid_init_state=open to the value of GRUB_CMDLINE_LINUX_DEFAULT="" in /etc/default/grub then
 update-grub

Anyway with this initial install, secure boot was off, I chose normal install rather than minimal, and requested third party drivers. Wifi worked fine!!

Based on this initial positive experience I decided to get a larger Nvme drive and make a serious linux machine out of this laptop. I backed up my data, swapped out the linux nvme for a new one, and re-installed everything the same way. Even using the exact same installer USB. 

Except this time, wifi doesnt work! When I boot into windows it does work. Having done everything the exact same way, I'm confused how I got two different outcomes.

```

$ dmesg | grep iwlwifi
[    9.449778] iwlwifi 0000:3f:00.0: enabling device (0000 -> 0002)
[    9.839374] iwlwifi: probe of 0000:3f:00.0 failed with error -110
$ lspci -nnk | grep 0280 -A3
3f:00.0 Network controller [0280]: Intel Corporation Wi-Fi 6 AX200 [8086:2723] (rev 1a)
    Subsystem: Intel Corporation Wi-Fi 6 AX200 [8086:0084] 
    Kernel modules: iwlwifi

```

I tried installing both the backports driver as well as the iwlwifi-cc-a0-46.ucode driver which I downloaded from Intel

> 
Intel(R) Wi-Fi 6 AX200 160MHz
Copyright (C) 2019 Intel Corporation.  All rights reserved.


Microcode Package README.iwlwifi-cc-ucode


INDEX


1. OVERVIEW
2. INSTALLATION
3. LICENSE




1. OVERVIEW


The file iwlwifi-cc-a0-46.ucode provided in this package must be present on
your system in order for the Intel Wireless WiFi Link AGN driver for Linux
(iwlwifi) to operate on your system.


The "-46" in the filename reflects an interface/architecture version number.
It will change only when changes in new uCode releases make the new uCode
incompatible with earlier drivers.


```

$sudo cp -v -u '/home/user/Desktop/linux/iwlwifi-cc-46.3cfab8da.0/iwlwifi-cc-a0-46.ucode' /lib/firmware
$sudo update-initramfs -uk all
$reboot

```

but after trying both of those drivers, and rebooting, I am still getting the "wi-fi device not detected" error. 

It is the 20.04 ubuntu install from the ISO installer file, but for reference kernel is Linux 5.4.0-37-generic

I am up and running with LAN cable/wired internet now, but obviously really would like to get the wifi working again. 

I also tried installing openrazer-meta which didn't help. I did all software updates offered in the manager, sudo apt update, sudo apt upgrade, etc. 

Any ideas? I am perplexed in particular because the first install went off without a hitch and wifi was working without my having to do anything about it, and now I cant get it to work, I cannot think of what I did differently this time

Thanks!

---

### Post by Ranbunta_Bantubunt on 2020-06-16
OK so a quick followup. I dont know how it happened, but now it is working. I rebooted again into windows to double check wifi was working there, which it was, though I had done this before, then rebooted back into ubuntu and now it's working. 

However something still seems fishy. When I go into Software & Updates > Additional drivers, It lists "Intel Wi-Fi 6 AX200" as "This device is not working". Even though it is working. 

Here is the output from dmesg

```

$ dmesg | grep iwlwifi
[    9.286901] iwlwifi 0000:3f:00.0: enabling device (0000 -> 0002)
[    9.352682] iwlwifi 0000:3f:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[    9.352700] iwlwifi 0000:3f:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[    9.355127] iwlwifi 0000:3f:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    9.355133] iwlwifi 0000:3f:00.0: Found debug destination: EXTERNAL_DRAM
[    9.355135] iwlwifi 0000:3f:00.0: Found debug configuration: 0
[    9.355416] iwlwifi 0000:3f:00.0: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[    9.473723] iwlwifi 0000:3f:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    9.488999] iwlwifi 0000:3f:00.0: Applying debug destination EXTERNAL_DRAM
[    9.489395] iwlwifi 0000:3f:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    9.654416] iwlwifi 0000:3f:00.0: base HW address: (address)
[    9.674677] iwlwifi 0000:3f:00.0 wlp63s0: renamed from wlan0
[   16.792571] iwlwifi 0000:3f:00.0: Applying debug destination EXTERNAL_DRAM
[   16.961548] iwlwifi 0000:3f:00.0: FW already configured (0) - re-configuring
[   16.976856] iwlwifi 0000:3f:00.0: BIOS contains WGDS but no WRDS

```


so something is still not kosher in this setup. somehow i seem to have jerry rigged it and i am getting a connection successfully, but things dont seem to be as they ought to be. any ideas why?
the dmesg output looks like it tried to load one driver and failed, but failed over to another one that worked. Im not sure what the BIOS comment means, regarding WRDS and WGDS

thanks

---

### Post by Yellow Pasque on 2020-06-16
> **Ranbunta_Bantubunt said:**
> When I go into Software & Updates > Additional drivers, It lists "Intel Wi-Fi 6 AX200" as "This device is not working". Even though it is working. 

Don't worry about it: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1859308](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1859308)

---

