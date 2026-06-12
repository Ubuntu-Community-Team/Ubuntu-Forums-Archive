---
title: "Centrino wireless able to connect but does nothing"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by sunshineacid on 2014-01-08
Hey there, I am a complete Ubuntu noob. Just wanted to preface that.

I am having a rather strange issue in all variants of ubuntu, debian, and mint that I have tried. Currently running kubuntu 12.04 + kde 4.12. The issue is that about 95% of the time from a boot or a suspend to wake, my wireless connects to my home network, however it is unable to actually connect to anything. I can't hit my own router, and attempting to use any browser results in my browser hanging on "resolving host."

The twist on this, is that as soon as I connect it to an ethernet cable, I have full access to the web, even if I unplug my ethernet cable afterwards. 

TLDR: My wireless connects but doesn't go anywhere until I plug and unplug ethernet cable into laptop.

lspci output:
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 08)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 04)

Any help would be greatly appreciated.

---

### Post by chili555 on 2014-01-08
Please open a terminal and do:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us hear your report.

---

### Post by sunshineacid on 2014-01-09
Thank you, that appears to have done it.

What did that do? Disable wireless N for my device?

---

### Post by chili555 on 2014-01-09
> **sunshineacid said:**
> Thank you, that appears to have done it.

What did that do? Disable wireless N for my device?Correct. Some router and wireless card combinations don't do N very well. Some, including mine, do well. The classic fix is to disable N at the card leaving N intact at the router for other users. We have been hoping for a fix for many years but I suspect Intel blames the router manufacturer and vice versa.

---

