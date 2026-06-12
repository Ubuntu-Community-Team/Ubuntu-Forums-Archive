---
title: "Broadcom 43 wireless not workign with Hardy"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by GroupB on 2008-04-25
Hello,
I upgraded today from 7.10 to 8.04 on my Dell Latitude laptop.  After the upgrade and restart, my wireless was not working (however, it instructed me to Enable the Restricted Driver for my Broadcom 43 Wireless Card like I did way back when I first installed 7.10).  So, I did that, and it downloaded the driver once again.  After downloading and installing the driver, when I tried to enable it (by checking the box), it said I need to restart my computer, so I did.  However, after restarting, the wireless still does not work.  Everytime I try to check the box in the Restricted Device Manager thing, it tells me I need to restart, which never works.  Any ideas?  Thank you so much,

---

### Post by goslings on 2008-04-25
similar issue for me 
initial 7.10 issues with making wireless work with broadcom 43 and now the same problematic issues with 8.04. - wired ethernet - no problems 
I would be interested in any idea?

---

### Post by GroupB on 2008-04-25
Hello,
I found this thread which told me to uninstall 2 packages realated tot he Broadcom card with Synaptic and then use the command line to re-install the driver.  The instructions are here:

[http://ubuntuforums.org/showthread.php?t=709259&highlight=hardy+broadcom](http://ubuntuforums.org/showthread.php?t=709259&highlight=hardy+broadcom)

It worked!

---

### Post by GroupB on 2008-04-25
Sorry, here is the correct link:

[http://ubuntuforums.org/showthread.php?t=709259](http://ubuntuforums.org/showthread.php?t=709259)

---

### Post by goslings on 2008-04-25
> **GroupB said:**
> Hello,
I found this thread which told me to uninstall 2 packages realated tot he Broadcom card with Synaptic and then use the command line to re-install the driver.  The instructions are here:

[http://ubuntuforums.org/showthread.php?t=709259&highlight=hardy+broadcom](http://ubuntuforums.org/showthread.php?t=709259&highlight=hardy+broadcom)

It worked!

Dasly does not work for me 
and now reg drivers does not list broadcom 43 
Same issue I had under 7.1 
Why o why does this never work out of the box 
wired is fine !
thanks

---

### Post by Pablo12CR on 2008-04-25
Hi!!!

Im using a new Pavilion dv2718us, NO wireless :mad:, I getting this:
[IMG]http://img222.imageshack.us/img222/2319/screenshotwirelessnetwokm2.png[/IMG]

But then 
[IMG]http://img134.imageshack.us/img134/1766/screenshotnetworksettinlu0.png[/IMG]

If i do lspci: Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller  <<<<

Anyway I gonna try "GroupB's" Link :(

---

### Post by GroupB on 2008-04-26
I hope it works for you "Pablo12CR".  Under the Thread link I posted previously, it is the second posting in that thread which describes the method that worked for me.

---

### Post by brew1brew on 2008-04-26
> **Pablo12CR said:**
> Hi!!!

Im using a new Pavilion dv2718us, NO wireless :mad:, I getting this:
[IMG]http://img222.imageshack.us/img222/2319/screenshotwirelessnetwokm2.png[/IMG]

But then 
[IMG]http://img134.imageshack.us/img134/1766/screenshotnetworksettinlu0.png[/IMG]

If i do lspci: Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller  <<<<

Anyway I gonna try "GroupB's" Link :(


I have Braodcom wireless on my HP f579. I had to use ndiswrapper, I had to compile ndiswrapper in fiesty. it was broken when I upgraded to 8.04, but this [document]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") has all the instructions on installing the driver or fixing it in hardy if you already had it installed in fiesty.

Les

---

