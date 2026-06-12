---
title: "how to get online from offline"
date: 2016-12-19
forum: Networking &amp; Wireless
---

### Post by hyburn on 2016-12-19
greetings folks,

it has been almost 8 years and it is good to "try" and get back into the ubuntu world.

Update:

Windows system crapped out (what a surprise).

found an old HDD with ubuntu 8.04 on it. no drivers of any kind.

if someone can help walk me through the steps to get a wireless driver for a Linksys AE2500 wireless USB installed without having internet on that system, it would be greatly appreciated.(I am messaging you from my laptop, so I will be able to find and download drivers as the suggestions are made.)


Long story short, just call me forgetful, Im basically a 1 bean noob again

:D

-regards

---

### Post by QIII on 2016-12-19
Hello!

That release is so hopelessly out of date, insecure and unsupported that it wouldn't be worth anyone's time to try to work with it.

You should probably install a supported release before you go any further.

---

### Post by hyburn on 2016-12-19
BWAH HA HA HA HA... HA HA HA,

    Ok, sorry for that outburst... I figured as much. can you make a suggestion?

    -regards

---

### Post by hyburn on 2016-12-19
hi guys,


I need some help...

old system died (windows, how typical).

I found an old HD with 8.04 on it. wrote 16.04 over it, also would need a walkthrough with using ndiswrapper. cant remember how to properly install anything...

what have I tried?
I have downloaded the ndiswrapper -1.61.tar.gz but not able to remember how to properly install it...
I have downloaded the driver AE2500xp_\WHQL,0.zip but need the ndiswrapper to get the driver to work...
******************************

it has been years since I have used linux, and I would love to get back into it. any help would be awesome

LSPCI results:
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
```

lsusb results:
```
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 124: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 122: ID 13b1:003a Linksys AE2500 802.11abgn Wireless Adapter [Broadcom BCM43236]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ubuntu love;

-hyburn

---

### Post by QIII on 2016-12-19
Threads merged.

---

### Post by hyburn on 2016-12-19
it appears they have

---

### Post by wildmanne39 on 2016-12-20
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by wildmanne39 on 2016-12-20
I just saw the usb adapter that you have and it is the hardest to get working and a lot of times it never works, I am sorry but I can not help with that device it would be better to buy a new one that is compatible with ubuntu, usually for around 10 to 20 dollars.

---

### Post by hyburn on 2016-12-20
> **wildmanne39 said:**
> I just saw the usb adapter that you have and it is the hardest to get working and a lot of times it never works, I am sorry but I can not help with that device it would be better to buy a new one that is compatible with ubuntu, usually for around 10 to 20 dollars.

found an old TPlink USB network card... Plugged it in and was able to connect instantly.

Thanks for the suggestion that the previous card was not supported.

---

