---
title: "karmic koala does not play nice with broadcom  4322"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-10-29
is there a bug with karmic because im not seeing any restricted hardware drivers so i have no wifi. anyone know what is going on

---

### Post by Technoviking on 2009-10-29
The Broadcom STA should show in Hardware Drivers. What is the output if you do lspci in a terminal.

T-V

---

### Post by PatrickMoore on 2009-10-29
i got it on the release canidate's live disc. however i was having crashes when i started playing around with it.

 my lspci 
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602 
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) 
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) 
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) 
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a) 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40) 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller 
09:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01) 
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 

```

i have not seen a single restricted driver since installing the final this evening

---

### Post by dyous87 on 2009-10-30
Run this command from terminal:

```
sudo apt-get install bcmwl-kernel-source
```

Then restart and your drive should work.

Regards,
David

---

### Post by asusu90 on 2009-10-30
Hi!
That's all right.
BCM4322 does not work for me after upgrade to 9.10 from 9.04.

lspci does not show it(!).
But with 9.04 Live it works.

---

### Post by PatrickMoore on 2009-10-31
> **dyous87 said:**
> Run this command from terminal:

```
sudo apt-get install bcmwl-kernel-source
```

Then restart and your drive should work.

Regards,
David

is there any solution without an internet connection. i dont have wired access at this point

---

### Post by Bobson on 2009-10-31
You can just install **bcmwl-kernel-source** with the CD, just follow the instructions in this post:

[http://swiss.ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://swiss.ubuntuforums.org/showpost.php?p=8090292&postcount=1)

It's how I got my broadcom wireless to work.

Hope this helps.

---

### Post by ThinkEntropy on 2009-11-21
> **dyous87 said:**
> Run this command from terminal:

```
sudo apt-get install bcmwl-kernel-source
```Then restart and your drive should work.

Regards,
David


I just wanted to say thank you!!!!!!  

After much fussing about this got my wireless working on my laptop \\:D/

---

