---
title: "How to determine wireless module name, etc"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2014-01-13
I have read this thread:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

Specifically section 4 "search for modules", it tells me to do an lsmod and then grep for the module name. 
1. How do I determine what to grep for? 
2. I am assuming that this is the module currently *in use* (for a particular card) is that correct?
3. In this context, the word "module" is the same as "driver", correct?
4. Assuming that doing a lsmod | grep "wlan_module_name" produces the driver currently in use, how do I determine a list of all possible drivers for this card? For example, I am assuming that there is a FOSS driver, and perhaps a proprietary driver. How do I find out the names of these? (Assuming I am using apt of course)
5. How do I determine the version number of the kernel module/driver? 
6. How I determine all of the above for a card I have not yet purchased, if I know the card model?

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
Does not mention anything about firmware. I am assuming that firmware is a separate issue from drivers. If so, how do I get a list of possible firmware for a particular card? (assuming at least two versions, FOSS and proprietary) (Again, assuming apt)

Thanks!

---

### Post by chili555 on 2014-01-13
There are a couple  of easier ways to do what you want to do. Assuming to have a PCI card, run:```
lspci -nn | grep 0280
```Here is a sample from my machine:> 03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)Now we see the pci.id, in this case 8086:4239. We can Google it and see this result: [http://ubuntuforums.org/showthread.php?t=2195603](http://ubuntuforums.org/showthread.php?t=2195603) As you can see, it refers to a driver iwlwifi. Now we check the modules that are loaded to see if it is among them:```
lsmod | grep iwl
```> $ lsmod | grep iwl
iwldvm                243729  0 
mac80211              635046  1 iwldvm
iwlwifi               179509  1 iwldvm
cfg80211              505004  4 wl,iwlwifi,mac80211,iwldvmWe can check *modinfo* to see if firmware is required:```
$ modinfo iwlwifi
filename:       /lib/modules/3.12.4-031204-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     A3081EB36A8BAE67C8037E0
<snip>
```What you will know only from experience is whether firmware is included by default or needs to be installed separately. The message logs will tell you however:```
$dmesg | grep iwl
[   26.511160] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   26.511303] iwlwifi 0000:03:00.0: irq 43 for MSI/MSI-X
[   26.819914] iwlwifi 0000:03:00.0: [COLOR="#FF0000"]loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm[/COLOR]
[   27.108282] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   27.108284] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   27.108285] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   27.108288] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   27.108394] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S

```The corresponding identifier for USB devices is:```
lsusb
```If you have more questions, please fire away!

---

