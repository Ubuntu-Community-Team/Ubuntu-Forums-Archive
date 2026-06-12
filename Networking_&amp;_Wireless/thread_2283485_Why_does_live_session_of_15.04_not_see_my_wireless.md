---
title: "Why does live session of 15.04 not see my wireless when the installed 12.04 does?"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by t0p on 2015-06-22
I've got 12.04 installed on my laptop.  I use my Sony Xperia Android phone as a wireless router, which works perfectly with 12.04.

I've recently downloaded 15.04, looking to upgrade.  I've run it in live session, to see if it's all compatible.  My computer's wireless adapter doesn't see the phone.  But the adapter *does* see my neighbours' routers. Also, I can tether the phone to the computer, and access the internet that way.  And I have another computer, which has Windows 8.1 on it, and the Windows computer has no problem at all using the phone as a wireless access point.

lspci output:
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation BCM57765/57785 MS Card Reader (rev 10)
02:00.3 System peripheral: Broadcom Corporation BCM57765/57785 xD-Picture Card Reader (rev 10)
03:00.0 Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ubuntu@ubuntu:~$ 

```

---

### Post by oscar-tiderman on 2015-06-23
Could you check with iwconfig if you have Power Management on or Power Management off when in live vs. when in 12.04? If it is on in 15.04, then do sudo iwconfig wlan0 power off, and wait for a rescan and see if your mobile hot spot shows up.

---

### Post by slickymaster on 2015-06-23
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by jeremy31 on 2015-06-23
It might be a regulatory setting, check ```
iwlist chan
``` in 12.04 and 15.04 and see if your wifi is on a channel that isn't available in 15.04

---

