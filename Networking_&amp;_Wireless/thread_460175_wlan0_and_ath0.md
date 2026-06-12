---
title: "wlan0 and ath0 ?"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by cool2121 on 2007-05-31
Can someone please explain whats the different between the 2? 

I installed Fiesty 7.04 on my laptop which comes with IWP2200 wifi. It works out of the box. But i dont see it under ifconfig. Also in my /etc/network/interfaces it shows as ath0. 

So where is wlan0? 

Thanks

---

### Post by tturrisi on 2007-05-31
post result of:
lspci

---

### Post by cool2121 on 2007-06-01
> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
**05:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)**
05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller



lspci give me that. The wireless works out of the box, but i dont see where to config the network in terminal. 
ifconfig doesnt show the device. 

What does ubuntu install by default to handle this card? 

i tried iwconfig but no dice. It shows eth0 as wireless ethernet

Everywhere i see ppl talking about wifi card, they always prefer to ath0 or wlan0 . But mine just shows eth0. I try to understand what they're preferring to. I really want to learn more about linux. 

Thanks

---

### Post by tturrisi on 2007-06-01
Linus assigns names for ethernet devices on a comp:
eth0, eth1, eth2, etc., and these are usually names of wired adapters, firewire adapters, etc.
Some wireless adapters also get an ethX name.
athX is used for adapters w/ an ATHeros chipset inside it.
wlanX is used for other brands/chipsets.

You should not have any athX references in /etc/network/interfaces.

Config the wifi using Network Manager which I believe is the default utility in Feisty.

---

