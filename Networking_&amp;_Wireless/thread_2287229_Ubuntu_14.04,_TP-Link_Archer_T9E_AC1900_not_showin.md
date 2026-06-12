---
title: "Ubuntu 14.04, TP-Link Archer T9E AC1900 not showing in lspci"
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by Tom_Wilkinson on 2015-07-17
Hello all!

I've been having troubles trying to install a wireless adapter onto a new build.  

And I don't know where to start since it doesn't even show up in lspci,

This is my lspci output:

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3 Processor DRAM Controller (rev 06)
00:14.0 USB controller: Intel Corporation Device 8cb1
00:16.0 Communication controller: Intel Corporation Device 8cba
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V
00:1a.0 USB controller: Intel Corporation Device 8cad
00:1b.0 Audio device: Intel Corporation Device 8ca0
00:1c.0 PCI bridge: Intel Corporation Device 8c90 (rev d0)
00:1c.3 PCI bridge: Intel Corporation Device 8c96 (rev d0)
00:1c.4 PCI bridge: Intel Corporation Device 8c98 (rev d0)
00:1d.0 USB controller: Intel Corporation Device 8ca6
00:1f.0 ISA bridge: Intel Corporation Device 8cc6
00:1f.2 SATA controller: Intel Corporation Device 8c82
00:1f.3 SMBus: Intel Corporation Device 8ca2
02:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
04:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)
04:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)

```

No wireless adapter!  I am sure it's plugged into the PCI express slot, there's a green light even on the adapter.

Looked through the BIOS and didn't see a wireless network disable so don't think that's it.

Tried to download drivers that would make sense for Broadcom but no such luck

Any help? 

[ATTACH]263254[/ATTACH]

---

### Post by praseodym on 2015-07-18
Did you reset the BIOS to default? Check "lspci -nnk" afterwards

---

### Post by justin36 on 2015-10-07
I am having the same problem. Did you find a solution?

---

### Post by derlemon on 2016-05-09
I know that this is months after,  Have you guys Tried Additional Drivers?

Search Your Computer ->  Additional Drivers

There might be a listing for Broadcom Corporation 802.11ac wireless Network Adapter.  This will work for the TP-Link Archer Network Adapter, and likely many others.  If you select the radio button to use broadcom and hit apply you should get some SSID's appearing underneath your available networks list.

---

