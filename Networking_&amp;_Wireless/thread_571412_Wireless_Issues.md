---
title: "Wireless Issues"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by Harry_A on 2007-10-09
Hi all this is my first post and this is my first day of using Ubuntu and  must say that after reading some of the threads in these forums this is a very helpful and friendly place.

Basically I've been wanting to switch to a linux OS but i have always been put off by the huge number of distributions out there, along with my fear of letting go of windows. I decided to dualboot with windows Vista on my main system, and after some fiddling I've started to run into problems.

I'm sure if i could get connected to the internet i would be able to fix most of them, but that is proving to be a very challenging task indeed.

My desktop pc (the one with ubuntu) is in my room, and i have a netgear wireless modem that is located at the center of the house (60m or so away from me). I really don't want to move my desktop pc over to the router to connect via ethernet if it can be avoided, but I'm willing to do it if i can get wireless working afterwards. I read some of the threads and was unable to get anything working, and now i even lost the "wireless connections" option from the menu on the taskbar thing.

Basically the wireless network is using WPA2 personal, broadcasting is enabled. I have a ASUS	

WL-138G V2 and on the wiki it says "Driver installed in Feisty, lacks firmware. bcm43xx-fwcutter in repos will fetch the firmware". The wireless card is PCI and is broadcomm chipset.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus)

I"m using my laptop to download things, putting them on a usb stick and installing them on the ubuntu desktop.

So I'm asking for your help with this, if anybody has any help they can give me, or any suggestions, I'd be very glad.Thanks in advance.

edit: Ive reinstalled now so im sitting on a fresh install and i havent touched a single thing. Thanks again.

---

### Post by kevdog on 2007-10-09
Can you post:

lshw -C network
lspci -nn

Thanks

---

### Post by Harry_A on 2007-10-09
harun@harun-desktop:~$ lshw -c network 
Hardware Lister (lshw) - B.02.08.01 
usage: lshw [-format] [-options ...] 
       lshw -version 

        -version        print program version (B.02.08.01) 

format can be 
        -html           output hardware tree as HTML 
        -xml            output hardware tree as XML 
        -short          output hardware paths 
        -businfo        output bus information 

options can be 
        -class CLASS    only show a certain class of hardware 
        -C CLASS        same as '-class CLASS' 
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 

harun@harun-desktop:~$ lspci -nn 
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f4] (rev a2) 
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2) 
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2) 
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2) 
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2) 
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2) 
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2) 
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2) 
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1) 
00:08.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1) 
00:09.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2) 
00:09.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2) 
00:09.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2) 
00:0a.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1) 
00:0a.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2) 
00:0c.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1) 
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2) 
00:0d.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2) 
00:0d.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2) 
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2) 
00:10.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2) 
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2) 
00:12.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a2) 
00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2) 
00:17.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2) 
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100] 
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101] 
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103] 
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7900 GT [10de:0291] (rev a1) 
02:08.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 01) 
02:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
02:0a.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007] 

there it is. Thanks for the quick response!

Harry.

---

### Post by kevdog on 2007-10-09
This is your network card:

02:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 

Here is a post addressing what you need for ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by Harry_A on 2007-10-09
BCM4318 in an Asus WL-138G-rev2. But used [WWW] drivers from Asus Website. Installed WinXP drivers. Seems stable and I don't see any transmission power issues that I've seen with the free bcm34xx driver. Network Manager + WPA working [I've incorporated this feedback into the howto -- JamieJackson]

This is from 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

this guy has the same wireless card that i do.

What does he mean by installed winxp drivers?

Thanks, though while following the guide i got stuck on step 1. After typing apt-get install ndisvwrapper-utils-1.9 i get a E:Couldnt find package error.

Harry.

---

