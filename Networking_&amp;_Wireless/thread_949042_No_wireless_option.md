---
title: "No wireless option"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by Garrison_O on 2008-10-15
Hi everyone! I'm new to ubuntu and Linux, but my current operating system (windows vista) is really slow, and I just don't like it. 
I installed Ubuntu with Wubi a few days ago, and everything works fine, except the wireless internet. In the network manager thing, there isn't even the option of making a wireless connection. 
I went to a troubleshooting section of this site and found help on what to do, but when it told me to go to System -> preferences -> Hardware Information, I couldn't find the Hardware Information. The help didn't have anything to do if I don't have it, so maybe this hasn't happened before...? 
If anyone could help, that would be wonderful! I'm also wondering if it has anything to do with me installing it with Wubi...?

---

### Post by Ayuthia on 2008-10-15
Installing wubi should have no factor on your wireless.  However, we will need some help in figuring out what wireless card you have.  Can you go into the Terminal and post the results of:
```
lspci -nn
```This will list out your pci cards and hopefully we will be able to identify your card from there and point you in the right direction.

---

### Post by Garrison_O on 2008-10-18
Thanks for helping!
Here's what lspci -nn did:

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10) 
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f] 
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36] 
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37] 
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80) 
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80) 
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80) 
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80) 
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83) 
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80) 
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01) 
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80) 
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80) 
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100] 
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101] 
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103] 
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975] 
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01) 
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10) 
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01) 
06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01) 
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01) 
06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01) 

I hope this helps, and one of you can make sense of this. I'll be excited to get my internet working!

---

