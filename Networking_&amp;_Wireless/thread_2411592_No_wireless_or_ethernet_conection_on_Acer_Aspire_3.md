---
title: "No wireless or ethernet conection on Acer Aspire 3690 Broadcom 4318"
date: 2019-02-01
forum: Networking &amp; Wireless
---

### Post by paolaarg on 2019-02-01
Hi, I'm new in the forum, so i hope don't break any of the rules. My english is a little rusty, i speak spanish but if you have a little bit of patience this will work. a few days ago i install lububtu 17.10, Artful aardvark released. I don't have ethernet conection, so i try to read the forums and do everything they says, nothing works for me. Somebody can help me, please? Here i put all the information
Notebook Acer Aspire 3690 
The first thing i did was type in the terminal, lspci -vnn -d 14e4:  
Which gave me: 
06:01.0 Ethernet controller [0200]: Broadcom Limited BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
Subsystem: Acer Incorporated [ALI] BCM4401-B0 100Base-TX [1025:0090] 
Flags: bus master, fast devsel, latency 64 IRQ 21 
Memory at d0000000 (32-bit, non-prefetchable) [size=8K] 
Capabilities: <acess denied>
Kernel driver in use: b44 
Kernel modules: b44 

06:02.0 Network controller [0280]: Broadcom Limited BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312] 
Flags: bus master, fast devsel, latency 64, IRQ 22 
Memory at d0000000 (32-bit, non-prefetchable) [size=8K] 
Capabilities: <acess denied>
Kernel drive in use: b43-pci-bridge 
Kernel modules: ssb 

After i did this, rfkill list, and gave me
0:acer-wireless: Wireless LAN 
Soft blocked: no 
Hard blocked: no 

I try with sudo apt-get purge bcmwl-kernel-source 
the outcome was E: the package could not be located bcmwl-kernel-source. 
So i think well, i don't have the kernel, and I started looking for it. Install the fwcutter, one in a million, just to be sure i type: 
Sudo b43-fwcutter -w /lib/firmware --identify 
Gave me this:
b43-fwcutter version 019 
A tool to extract firmware for Broadcom 43xx device from a propietary Broadcom 43xx device driver file. 

Usage: b43-fwcutter [OPTION] [propietary-driver-file] 
--unsopported Allow working on extractable but unsopported drivers 
-l|--list List Supported driver versions 
-b| --brcmsmac create firmware for brcmsmac 
-i| --identify Only identify driver file (don't extract) 
-w|--target-dir DIR extract and write firmware to DIR 
-v|--version Print b43-fwcutter version 
-h|--help Print this help 
Example: b43-fwcutter -w /lib/firmware wl_apsta.o 
To extract the firmware blobs from wl_apsta.o and store the resulting firmware in /lib/firmware. 
And after --list, because i download wl_apsta-3.130.20.0.o.tar.gz y el broadcom-wl-5.100.138.tar.bz2.enc and nothing. Even download ndiswrapper-source_1.60, ndiswrapper dbgsym, ndiswrapper-utils, ndiswrapper-dkms, ndiswrapper-common, a few patch, like, patch-2.6.0.xz.enc, backports, glibc, nothing. I try everything i can read, download all the packages, and nothing. Try again with Sudo b43-fwcutter -w /lib/firmware --list 
And gave this:
<driver>      <filename>     <microcode>     <MD5 checksum>
b43legacy   wl_apsta.o      295.14   
                                              e08665c5c5b66beb9c3b2dd54aa80cb3 
b43               wl_apsta.o      351.126                     
                                              9207bc565c2fc9fa1591f6c7911d3fc0 
b43             wl_apsta.mimo.o  351.126   
                                               722e2e0d8cc04b8f118bb5afe6829ff9 
b43             wl_apsta.mimo.o  410.2160     
                                                cb8d70972b885b1f8883b943c0261a3c 
b43             wl_apsta.o.         478.104     
                                                bb8537e3204a1ea5903fe3e66b5e2763 
b43            wl_prebuilt.o      508.1084   
                                                490d4e149ecc45eb1a91f06aa75be071 
b43            wl_apsta.o          508.1107     
                                                f06c8aa30ea549ce21872d10ee9a7d48 
b43             wl_apsta.o        508.10872     
                                                  e413c0017b99195f3231201c53f31d1 
b43              wl_apsta.o        508.154     
                                                023fafbe4918e384dd531a046dbc03e8 
b43             wl_apsta.o          644.1001       
                                                68f38d139b1f69f3ea12393fb645c6f9 
b43            wl_apsta.o           666.2       
                                                 e1b05e268bcdbfef3560c28fc161f30e 
b43             wl_apsta.o          784.2       
                                                  29c8a47094fbae342902d84881a465ff 

So, i was thinking that i don't have the right driver again, so i was looking in all the forums, even OpenSuse looking for the right driver and kernel but nothing again. Really don't know what to do, so, i follow the steps in this page, but nothing. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) 
Every time i try with sudo modprobe b43 -r or sudo modprobe, nothing. So here i am, looking for the right steps for my situation. Please help me, i'm going crazy with this. And i know for a fact that the wifi can work, before i did it with ethernet, but is no longer an option, so please, i need to do this offline, with only my cellphone. Thanks so much. If you need some information, please let me know and i post all you need.

---

### Post by wildmanne39 on 2019-02-01
Please use your thread here:

[https://ubuntuforums.org/showthread.php?t=2411591](https://ubuntuforums.org/showthread.php?t=2411591)

I answered you right after you posted:

[https://ubuntuforums.org/showthread.php?t=2411591](https://ubuntuforums.org/showthread.php?t=2411591)

Duplicate thread closed!

---

