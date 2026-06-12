---
title: "Linksys WPM11 wireless set-up--HELP!!"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by jazzbo88 on 2008-08-06
:confused: I have been trying for a week to get this wireless to work. I have used numerous different posts, followed step-by-step instructions with no luck and am now ready to bite the heads off nails!!

Here are the files installed in Windows (where the wireless does work):

C:\Program Files\Linksys\WMP11 Config Utility
InstallDrv.exe<>PCong.bin
InstallDrvV27.exe<>PLink.bin
remove.exe<>PProfile.bin
RemoveV27.exe<>PSite.bin
RunU.exe<>WMP11CFG.bin
WPM11CFG.exe<>WMP11NDS.cat
BMWL3.dll<>WMP11V27.cat
DAct.bin<>WMP11NDS.inf
DInact.bin<>WMP11V27.inf
DNoDrv.bin<>WMP11NDS.sys
FBase.bin<>WMP11V27.sys


The device ID taken directly from WMP11V27.inf above is:

     [I]PCI\VEN_14e4&DEV_4301&SUBSYS_43011737
[/I]
The device ID taken directly from WMP11NDS.inf above is:

     [I]PCI\VEN_1260&DEV_3873&SUBSYS_38711737
[/I]
When I open terminal and enter *sudo lshw -C network*
I get this:

[I]*-network:1 DISABLED
      description: Wireless interface
      product: BCM4303 802.11b Wireless LAN Controller
      vendor: Broadcom Corporation
      physical id: 10
      bus info: pci@0000:00:10.0
      logical name: eth1
      version: 01
      serial: 00:06:25:0a:5c:a5
      width: 32 bits
      clock: 33MHZ
      capabilities: pm bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b [/I]

While I'm not a beginner I'm no expert either, falling a little shy of being an intermediate user of Ubuntu "Terminal." Would someone please take a look at this and help me enable this wireless network in Ubuntu/Linux?

Thanks a million!!
Jazzbo
:guitar:

---

### Post by ajgreeny on 2008-08-06
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=767372&highlight=BCM4303](http://ubuntuforums.org/showthread.php?t=767372&highlight=BCM4303)
If not give it a try and you may be lucky.  Your lshw shows you have a BCM4303 chip so you may just get it to work as all these have.  Good luck.

---

