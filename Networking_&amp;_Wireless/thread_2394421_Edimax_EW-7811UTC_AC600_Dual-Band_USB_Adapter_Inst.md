---
title: "Edimax EW-7811UTC AC600 Dual-Band USB Adapter Installation &amp; Setup"
date: 2018-06-16
forum: Networking &amp; Wireless
---

### Post by Glen_Wilson on 2018-06-16
Depending on the age and specifications of your computer, you may be looking for a wireless adapter that is faster than what the factory gave you.  I have a Lenovo G-series laptop that is not that old, but it came equipped with an internal wifi adapter that operates on the 802.11N protocol and gives me a wireless connection speed of 72 Mb/s. For $14.40 (as of 6-16-18) with Prime delivery you can buy the following adapter and boost your speed to 434 Mb/s with very little hassle.

Edimax EW-7811UTC AC600 Dual-Band USB Adapter              Available at Amazon with Prime for $14.40

**IMPORTANT NOTE:** I have specified the Edimax EW-7811UTC  AC600 Dual-Band USB Adapter in this post because I have several of them  running and because they run reliably by simply installing the  rtl8812au-dkms software. I have tried higher speed adapters claiming  600, 800, 1200, and 1300 Mb/s from Edimax and other manufacturers and  have had nothing but problems. Sometimes they run unreliably. Frequently  "nano" sized adapters overheat and die. So, this 600AC adapter  delivering a reliable 434 Mb/s in a compact package is my compromise, and I am completely  satisfied with it. This has been my experience, and your mileage may  vary!

This adapter will not work "out of the box" because the Linux kernel doesn't support the chipset. Why? I have no idea. But it is easy to get it up and running.

The best method is to open the Synaptic package manager and type "rtl88" in the search field. The search will show you **rtl8812au-dkms** and allow you to install it in the normal manner. If you use the Synaptic or other software installer that came with your distribution, you will be assured that the version of rtl8812au-dkms is compatible.

When you install rtl8812au-dkms, it will incorporate the rtl8812au chipset driver into your kernel and also run depmod and everything else to get you up and running. Depending on the speed of your system, it may take a minute or two to complete. It seems like forever, but that's normal.

When it is completed, insert or re-insert your USB adapted, and it should start working immediately and also work the every time you reboot your system.

**NOTE:** You don't want both the internal wifi adapter and the external USB adapter working at the same time. They interact in unpredictable ways and can cause problems loading web pages. Find your way to "Edit Connections..." and change the settings of the adapters under the **General** tab. Activate the box marked **"Automatically connect..." **for the external USB adapter, and deactivate the "automatic" box for the internal adapter.

That's it, and you've gone from 72 Mb/s up to 434 Mb/s for under $15.

Just for reference, if you run the **lsusb** command in a terminal window, you will see something similar to this:

Bus 002 Device 004: ID 13d3:5741 IMC Networks 
**Bus 002 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. **
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
**Bus 003 Device 004: ID 7392:a812 Edimax Technology Co., Ltd **
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
The Bus 002 Device is the internal wifi adapter. The Bus 003 Device is the external USB adapter.

**IMPORTANT NOTE:** I have specified the Edimax EW-7811UTC AC600 Dual-Band USB Adapter in this post because I have several of them running and because they run reliably by simply installing the rtl8812au-dkms software. I have tried higher speed adapters claiming 600, 800, 1200, and 1300 Mb/s from Edimax and other manufacturers and have had nothing but problems. Sometimes they run unreliably. Frequently "nano" sized adapters overheat and die. So, this 600AC adapter delivering a reliable 434 Mb/s is my compromise, and I am completely satisfied with it. This has been my experience, and your mileage may vary!

---

