---
title: "I have to boot windows in order for Wifi to work on Ubuntu"
date: 2017-12-12
forum: Networking &amp; Wireless
---

### Post by bshatt1987 on 2017-12-12
Hi, I've been having this problem for a long time, across all Linux distributions that I have tested, I believe.  
So the problem is, sometimes my Wifi doesn't work when I boot into Ubuntu/Other Linux.
What I have found, is that the wifi seems to work if I have restarted the computer from Windows.

So, say I'm on Windows where the wifi always works.  I decide to reboot the computer into Ubuntu.  The wifi will work on Ubuntu.
But then say I decide to reboot from Ubuntu back into Ubuntu, the wifi will not work.  
To clarify, though, the wireless card is powered on, but no networks show up to connect to.

The wifi card is a Realtek RTL8188EE, I'm not sure what other information you may require, if any, but please let me know.  
[FONT=monospace]Thanks for reading![/FONT]

---

### Post by timothylegg on 2017-12-14
Can you elaborate on the machine?  Is this chipset on an edgecard on a Desktop, module on a laptop?  I've had good luck at using lsusb to track down root causes on laptops.  I haven't used a desktop PC in years, but I think it's counterpart is lspci.

This page looks interesting and complete.  Try these steps, regardless of the type of machine you are using:

[https://wiki.debian.org/HowToIdentifyADevice/USB](https://wiki.debian.org/HowToIdentifyADevice/USB)

Let us know what you find out.

Timothy Legg

---

### Post by timothylegg on 2017-12-14
Thinking about it some more, this sounds like an ACPI problem.  I recall having this issue with an Asus EeePC several years back.  Being a boot-up issue, the output of dmesg is interesting, especially when comparing dmesg outputs from booting with wifi available or missing.  I think that was what I did to solve the problem.  Unfortunately, I don't remember what I did exactly as that was over 10 years ago.

---

### Post by bshatt1987 on 2017-12-14
> **timothylegg said:**
> Can you elaborate on the machine?  Is this chipset on an edgecard on a Desktop, module on a laptop?  I've had good luck at using lsusb to track down root causes on laptops.  I haven't used a desktop PC in years, but I think it's counterpart is lspci.

This page looks interesting and complete.  Try these steps, regardless of the type of machine you are using:

[https://wiki.debian.org/HowToIdentifyADevice/USB](https://wiki.debian.org/HowToIdentifyADevice/USB)

Let us know what you find out.

Timothy Legg

> **timothylegg said:**
> Thinking about it some more, this sounds like an ACPI problem.  I recall having this issue with an Asus EeePC several years back.  Being a boot-up issue, the output of dmesg is interesting, especially when comparing dmesg outputs from booting with wifi available or missing.  I think that was what I did to solve the problem.  Unfortunately, I don't remember what I did exactly as that was over 10 years ago.

Sorry for being slow to respond but thanks for your reply! The machine is an HP 2000 Laptop (model 2d70dx, if that helps).
Would you like for me to show the dmesg outputs?  

This is the output of lsusb and lspci, respectively:

```
[FONT=monospace][COLOR=#000000]ben@ben-kubuntu:~$ lsusb[/COLOR]
Bus 003 Device 005: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b34f Chicony Electronics Co., Ltd  
Bus 001 Device 002: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1d57:ad17 Xenta  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ben@ben-kubuntu:~$ lsusb -v | grep -E '\<(Bus|iproduc|bDeviceClass|bDeviceProtocol)
' 2>/dev/null
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 003 Device 005: ID 1a40:0101 Terminus Technology Inc. Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            9 Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         1 Single TT[/COLOR]
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            9 Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0 Full speed (or root) hub[/COLOR]
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            9 Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0 Full speed (or root) hub[/COLOR]
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            9 Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0 Full speed (or root) hub[/COLOR]
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            9 Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0 Full speed (or root) hub[/COLOR]
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 001 Device 004: ID 04f2:b34f Chicony Electronics Co., Ltd  [/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]          239 Miscellaneous Device[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         1 Interface Association[/COLOR]
      ([COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] Powered)[/COLOR]
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 001 Device 002: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            0 (Defined at Interface level)[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0  [/COLOR]
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            0 (Defined at Interface level)[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0  [/COLOR]
  ([COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] Powered)[/COLOR]
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            9 Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0 Full speed (or root) hub[/COLOR]
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 004 Device 002: ID 1d57:ad17 Xenta  [/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            0 (Defined at Interface level)[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0  [/COLOR]
      ([COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] Powered)[/COLOR]
Couldn't open device, some information will be missing
[COLOR=#FF5454]**Bus**[/COLOR][COLOR=#000000] 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
  [COLOR=#FF5454]**bDeviceClass**[/COLOR][COLOR=#000000]            9 Hub[/COLOR]
  [COLOR=#FF5454]**bDeviceProtocol**[/COLOR][COLOR=#000000]         0 Full speed (or root) hub[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]
```
ben@ben-kubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root C
omplex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [R
adeon HD 8400 / R3 Series]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functi
on 0
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functio
ns 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functio
ns 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functio
ns 5:1
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AH
CI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller 
(rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller 
(rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller 
(rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller 
(rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev
 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Control
ler (rev 01)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller 
(rev 39)
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller 
(rev 39)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functi
on 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functi
on 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functi
on 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functi
on 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functi
on 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functi
on 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Expre
ss Fast/Gigabit Ethernet controller (rev 05)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Netw
ork Adapter (rev 01)
06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Expres
s Card Reader (rev 01)

```[/FONT]

---

