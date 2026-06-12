---
title: "wireless help please.............."
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by dnice on 2007-12-02
Hello Ubuntu family,
           I am very new to ubuntu 7.10. All is great!!!!!! so far except for this wireless connection issue i have. I have a Toshiba Satellite A215-S4697 The card is a Atheros Commuication Inc Ar500ge 802.11 b/g wireless PCI express. Some background information is; I do have a Windows wireless driver choice in my system admin drop down. I have also downloaded the drivers and  the message reads;

netathr

Hardware present; yes


In the terminal it reads;

phillipduhart@phillipduhart-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

phillipduhart@phillipduhart-laptop:~$ 

 Please if someone could help explain it step by step, as i am but an infant.

---

### Post by kevdog on 2007-12-02
In the terminal can you type:

lspci -nn

And post the output.  I only want the line about that talks about the atheros card.

---

### Post by dnice on 2007-12-02
Ok, here is the whole thing;


phillipduhart@phillipduhart-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
14:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
1a:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
1a:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
1a:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
1a:04.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
phillipduhart@phillipduhart-laptop:~$

---

### Post by kevdog on 2007-12-02
Your card is supported by the madwifi drivers -- Great.  That means within synaptic you need to install the linux-restricted package for your kernel version.  No ndiswrapper fiasco.

---

### Post by MrFSL on 2007-12-02
> **kevdog said:**
> Your card is supported by the madwifi drivers -- Great.  That means within synaptic you need to install the linux-restricted package for your kernel version.  No ndiswrapper fiasco.

This is not entirely correct. I am tracking an issue: [http://madwifi.org/ticket/859](http://madwifi.org/ticket/859) with this chipset and madwifi. Recompiling with the latest madwifi drivers might help but would mean a tricky process of installing them over the linux-restricted package if you don't wish to remove it.

Ndiswrapper success seems to be alright, but it really depends highly on:
1) Making sure that the restricted module does not start

2) That you have the best version of the ndis driver and ndiswrapper.

I have read contrary information on this issue. In at least on place on the madwifi site (lost the link sorry) it was reported that this was an issue with HAL and not with the driver, so I would not be fixed with the latest madwifi packages.

**EDIT** 
@dnice - my suggestion is to ensure first that the restricted module is not loaded. Then tinker try more then one version of the ndis driver. Ultimately you should be able to see a wireless device added using: *iwconfig*

Furthermore, additional information regarding the success of the Windows Driver load by ndiswrapper can be found by typing: *dmesg*

---

### Post by kevdog on 2007-12-02
Just a quick question -- say you install the linux restricted drivers package with madwifi and found it would work.  Without having to uninstall all the drivers included in this release you could simply delete the drivers if they didnt work, or simply compile madwifi from source and then install these drivers ontop (overwrite) the older drivers!!  I'm not sure what the big deal is.

If the restricted madwifi drivers and the compiled madwifi drivers fail, then resort to ndiswrapper.  It might take a little experimentation, however its definitely possible.

svn versions are the best if you decide to start compiling.

---

### Post by MrFSL on 2007-12-02
> **kevdog said:**
> Just a quick question -- say you install the linux restricted drivers package with madwifi and found it would work.  Without having to uninstall all the drivers included in this release you could simply delete the drivers if they didnt work, or simply compile madwifi from source and then install these drivers ontop (overwrite) the older drivers!!  I'm not sure what the big deal is.

If the restricted madwifi drivers and the compiled madwifi drivers fail, then resort to ndiswrapper.  It might take a little experimentation, however its definitely possible.

svn versions are the best if you decide to start compiling.

This issue has been reported in other posts as well as community docs. The restricted module is installed already in gutsy and checked for the card. Recompiling from source does not overwrite all the instances of the old driver and creates issues. 

This is one of those "apple or oranges" situations. If you want to break a package (restricted modules) by deleting files and overwriting them, or if you do not need any of the other restricted modules (such as nvidia support) then either recompile, replace, or remove.

If you want to give ndiswrapper a try (which in the trouble ticket on madwifi seems to be the most reliable current solution) then simply disable the madwifi driver and give ndiswrapper a shot.

Up to you - but I know which one I'd choose first.

---

### Post by juniorbink on 2008-03-04
what you have is not the AR5006eg it is the AR5007eg wireless card and you will need to use ndiswrapper.  I have the same laptop and i got it working using ndiswrapper.  It not that madwifi isn't compatable, but rather a problem with HAL or atleast that is the problem using fedora.  I hope the info helps I can post a step by step setup if you like. Just let me know.

---

