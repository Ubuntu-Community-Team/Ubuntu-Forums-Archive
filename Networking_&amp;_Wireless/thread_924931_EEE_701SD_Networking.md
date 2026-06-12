---
title: "EEE 701SD Networking"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by Peque on 2008-09-20
Hey Guys. 

I've installed Ubuntu for a friend on such litlle machine - there's only some small problems. 
I don't want to use the EEE - caurse of the look on it - just normal Ubuntu. 
But after installing 8.04-1 i686 No network is working. I've search compiled and reinstalled several times without getting anything to work: 

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 8199 (rev 22)
03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
```

Which is the output from lspci - I've search and found atl2.ko should work - downloaded it - and compiled - But no go for working. 

So what can I do - to maker both wired and wireless works.

---

### Post by alvinistic on 2008-10-18
The ethernet networking use atl1e kernel module, instead of atl2.

The wireless uses r8180 kernel module (same as MSI wind).
Look here for more info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141)

---

