---
title: "Ubuntu 14.04 reports no wireless card with Intel Wireless 7260"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by Trekkin on 2014-08-30
Hello. I installed Ubuntu 14.04.1 LTS on an Asus Q302 today, and while it can find my usb-to-Ethernet adapter it cannot use my wireless card, which lspci claims is an Intel Wireless 7260 rev cb. The wireless-info is [here]("http://pastebin.com/9SebiByL"). Additionally:

```
lshw -C network

  *-network UNCLAIMED
       description: Network controller
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c01fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:50:b6:10:75:ca
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Dec-2011 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=192.168.1.3 link=yes multicast=yes port=MII speed=100Mbit/s
```

If anyone could help me fix this, I'd very much appreciate it; I'm very new to Linux.

---

### Post by ThatBum on 2014-08-31
I bet it needs a proprietary driver. Connect to the Internet using the Ethernet adapter and look in the Additional Drivers tab of the Software and Updates section from settings, and see if there's anything there. If not try updating first.

---

### Post by Trekkin on 2014-08-31
Nothing is there, even after I updated.

---

### Post by ThatBum on 2014-08-31
Perhaps these will be of assistance?
[Intel® Wi-Fi Products &#8212; Linux* support for Intel® Wi-Fi Adapters]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm")
[iwlwifi - Linux Wireless]("http://wireless.kernel.org/en/users/Drivers/iwlwifi")
[No wireless for Intel Corporation 7260 version 63 - Ask Ubuntu]("http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63")

---

### Post by jeremy31 on 2014-08-31
For whatever reason, Ubuntu did not load iwlmvm and it is needed to load the ucode file, see if ```
sudo modprobe iwlmvm
``` does anything and rerun the wireless script so we can see any dmesg errors

---

### Post by Trekkin on 2014-08-31
It returned nothing, and my wireless is still nonfunctional, so i will assume no. The new wireless-info is [here]("http://pastebin.com/F16sRtiJ").

I tried running the backport from the third link in ThatBum's post; it quit after 

/Desktop/backports-3.11-rc3-1/net/wireless/sysfs.c:151:2: error: unknown field &#8216;dev_attrs&#8217; specified in initializer
  .dev_attrs = ieee80211_dev_attrs,

---

### Post by jeremy31 on 2014-08-31
Might be able to get this to work using a backdoor approach as the revision you have isn't listed for iwlwifi yet as far as I know```
cat /sys/bus/pci/devices/0000:02:00.0/modalias
```

---

### Post by Trekkin on 2014-08-31
It returned



```
pci:v00008086d000008B1sv00008086sd00004C70bc02sc80i00
```

---

### Post by chili555 on 2014-08-31
A Google for your device:> Intel Corporation Wireless 7260 [8086:08b1] (rev cb)
        Subsystem: Intel Corporation Device [[COLOR="#FF0000"]8086:4c70[/COLOR]]...shows but one interesting post: [http://ubuntuforums.org/showthread.php?t=2238735](http://ubuntuforums.org/showthread.php?t=2238735)

To cut to the conclusion, the poster says:> the card is likely an OEM version with a custom subsystem revision number that is not on the alias list for the driver. If this conclusion is correct then I would have to either wait until upstream finds and adds the number or edit the source and manually compile the driver every time that there is a kernel update. 

Unfortunately I needed to use the laptop for work, so I ended up swapping the card with the Atheros card from my wife's laptop. She is running Windows, so the Intel card is OK in her system and the Atheros card just works in Ubuntu.If you'd care to experimentally; no, *highly* experimentally edit the .c code and compile your own driver, I will be happy to get out my plasma cutter, hammer and other tools of destruction.

If, on the other hand, you'd care to buy a fully supported USB wireless, consult the many threads on this forum on that subject.

EDIT: If Jeremy wants to attempt it, please proceed.


-------------------------
Note to Chili: pcie/drv.c around line 334 in backports 3.16-1.

---

### Post by Trekkin on 2014-08-31
I'm game to try compiling my own driver. Strictly speaking, this machine doesn't *need* wireless for what I need to do with it, so I'm not pressed for time.

What do I need to do?

---

### Post by jeremy31 on 2014-08-31
> **chili555 said:**
> A Google for your device:...shows but one interesting post: [http://ubuntuforums.org/showthread.php?t=2238735](http://ubuntuforums.org/showthread.php?t=2238735)

To cut to the conclusion, the poster says:If you'd care to experimentally; no, *highly* experimentally edit the .c code and compile your own driver, I will be happy to get out my plasma cutter, hammer and other tools of destruction.

If, on the other hand, you'd care to buy a fully supported USB wireless, consult the many threads on this forum on that subject.

EDIT: If Jeremy wants to attempt it, please proceed.


-------------------------
Note to Chili: pcie/drv.c around line 334 in backports 3.16-1.

Have fun, I have other projects

---

### Post by chili555 on 2014-08-31
First of all, this is purely experimental. It may work well; it may work partially or it may not work at all. We never know until we try.

First, download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.16/backports-3.16-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.16/backports-3.16-1.tar.xz) Right-click it and select 'Extract Here.' Navigate to the directory Desktop/backports-3.16-1/drivers/net/wireless/pcie and open the file drv.c with gedit, nano, leafpad or any text editor. Scroll down to line 334. We are going to add a new line below it to add your device. Change this section:```
        {IWL_PCI_DEVICE(0x08B1, 0xC02A, iwl7260_2n_cfg)},
	{IWL_PCI_DEVICE(0x08B2, 0xC220, iwl7260_2n_cfg)},
	{IWL_PCI_DEVICE(0x08B1, 0xC420, iwl7260_2n_cfg)},
```...to add your device. I don't know if your device is an N, a 2N or a 2AC, so all we can do it take a guess, unless you know some other details about it. My wild guess is 2AC. So we add a new line:```
        {IWL_PCI_DEVICE(0x08B1, 0xC02A, iwl7260_2n_cfg)},
	{IWL_PCI_DEVICE(0x08B2, 0xC220, iwl7260_2n_cfg)},
	{IWL_PCI_DEVICE(0x08B1, 0xC420, iwl7260_2n_cfg)},
        {IWL_PCI_DEVICE(0x08B1, 0x4C70, iwl7260_2ac_cfg)},
```Spacing, caps, brackets, etc. are crucial and must be exact. Type carefully, proofread twice, save and close the text editor.

Now we compile the driver.```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.16-1
make defconfig-iwlwifi
make
sudo make install
```The driver requires firmware:```
$ modinfo drivers/net/wireless/iwlwifi/iwlwifi.ko 
filename:       /home/chili/Downloads/backports-3.16-1/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:d
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       [COLOR="#FF0000"]iwlwifi-7260-9.ucode[/COLOR]
firmware:       iwlwifi-8000-8.ucode

```If your linux-firmware package is fully updated, you probably have it; check:```
ls /lib/firmware | grep 7260
```If the backports package built without error and you have the firmware, you ought to be able to load the driver and have wireless (!!!).```
sudo modprobe iwlwifi
iwconfig
```Are there any errors or signs of distress in the log?```
dmesg | grep iwl
```Let us know your results; we will probably have one additional step.

---

### Post by Trekkin on 2014-08-31
That appears to have worked perfectly! I now have wifi. I will watch for any disconnects or other abnormal behavior over the next few hours, though.

Thank you so much!

---

### Post by chili555 on 2014-08-31
Awesome! I suspect you will have helped some searchers.

You have compiled the driver for your current kernel only. When a newer kernel, known in Ubuntu World as linux-image, is installed by Update Manager, re-compile:```
cd ~/Desktop/backports-3.16-1
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-iwlwifi
make
sudo make install
```Please retain the files and these instructions for that time.

CAUTION to searchers: Unless your device is the exact same, Intel Corporation Wireless 7260 [8086:08b1] (rev cb)
Subsystem: Intel Corporation Device [[COLOR="#FF0000"]8086:4c70[/COLOR]], then this process is not the solution to your problem. These are not the droids you are looking for. Move along!

---

### Post by User-007 on 2014-10-31
Thanks a lot, Chili555! This guide solved my problem with Asus TP300LA. Now having wireless working, without problems so far. Would it be possible to get this fix into mainstream?

User 007

---

### Post by chili555 on 2014-10-31
I just checked my 14.10 installation and it hasn't made it so far. It would be helpful to file a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

The key thing to report is that, although many other subsystem ids are included in iwlwifi, yours, 8086:4c70, is not. If you wish, feel free to refer to this thread in your report.

---

### Post by jeremy31 on 2014-10-31
Might be worth sending an email to [email]ilw@linux.intel.com[/email]

---

### Post by User-007 on 2014-10-31
I sent a message to [email]ilw@linux.intel.com[/email]. Hope they will fix the issue in the future.

Thank you!

---

### Post by User-007 on 2014-11-03
I received a quick response from Intel. The problem has been already fixed in upstream kernels. I tested with 3.18-rc1 and everything with Wifi was OK. So everyone facing this problem, go to [https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds) ang grab yours from upstream archive.

---

