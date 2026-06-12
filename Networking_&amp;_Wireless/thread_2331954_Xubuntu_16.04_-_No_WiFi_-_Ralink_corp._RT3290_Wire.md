---
title: "Xubuntu 16.04 - No WiFi - Ralink corp. RT3290 Wireless"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by matboe1 on 2016-07-27
Hi all,  I'm pretty new so please forgive if i'm stupid at this :)

My fresh install of Xubuntu 16.04 cannot detect Wi-Fi networks.  Wires networks are fine.

I've found a few other articles on this but none have helped so far.

'lspci' outputs this-

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
09:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
09:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
```

Any help would be very much appreciated.

Ta!

---

### Post by YQ002lc2 on 2016-07-27
I don't know if this would help, but: 

Alt+F2 
or 
Alt+T

Then type:
nm-applet.

You should be able to see the applet on the right side in either the top or bottom. (Wherever your toolbar is) 

From there you should be able to tool around and get connected. 

Sorry if I misunderstood your question.

---

### Post by matboe1 on 2016-07-27
Hi,

Thanks for getting back to me.  
Sorry that my question is not so clear.
I'll try to be more concise.
I believe my Ralink wifi card is not supported, hence no WiFi. I've been fiddling with ndiswrapper and a windows driver but to no avail so far.    
09:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe

Thanks again!

---

### Post by howefield on 2016-07-27
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

