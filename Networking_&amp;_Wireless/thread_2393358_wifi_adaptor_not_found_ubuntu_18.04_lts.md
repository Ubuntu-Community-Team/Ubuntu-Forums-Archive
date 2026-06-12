---
title: "wifi adaptor not found ubuntu 18.04 lts"
date: 2018-06-02
forum: Networking &amp; Wireless
---

### Post by singhalshrish on 2018-06-02
hello!
i have just set up ubuntu 18.04 lts as a dual boot along with windows 10.I used a usb stick to accomplish the task but i am unable to connect to the wifi. The system shows no wifi adaptor found. However it worked fine in windows.

lspci gives the following result

shrish@shrish-HP-ProBook-440-G3:~$ lspci
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Broadcom Limited BCM43228 802.11a/b/g/n
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)


it would be great if you could explain it to me how to get it working in layman terms as i am new to ubuntu.

---

### Post by chili555 on 2018-06-02
> Network controller: Broadcom Limited BCM43228 802.11a/b/g/nPlease check here for a complete guide to installing drivers for Broadcom wireless devices. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by olds97lss on 2019-03-06
> **chili555 said:**
> Please check here for a complete guide to installing drivers for Broadcom wireless devices. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

I followed that thread on my usb install, but it's still not showing the adapter in settings. Says no wifi adapter found.

I did start my own thread regarding that. Just thought I'd mention it in an existing one in case anyone else trips across this.
[https://ubuntuforums.org/showthread.php?t=2414174](https://ubuntuforums.org/showthread.php?t=2414174)

---

