---
title: "Wireless card issue- think I have an idea"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by swimm3r137@gmail.com on 2008-04-15
Okay...  UGH, im frustrated, but i think this really really REALLY needs to be addressed.  It seems like the vast majority of users just cannot connect to the internet without problems.  Tell me if I'm wrong, but I think the issue is this (i'm a newbie, so bear with me)- Let's say you overwrite windows and install ubuntu.  Once you do so, ubuntui starts, but the windows wireless drivers that previously make your wireless card function are gone (because so is windows).  Because of this, they don't work.  DUH!  BUT, how the hell do you download drivers onto this computer, when the internet doesn't work.....???  Do you guys think I can download these drivers to a flash usb drive and then just transfer them to ubuntu on the laptop that doesn't have internet??  

If I can, the problem then becomes- WILL UBUNTU RUN THESE **WINDOWS** drivers correctly??  I hope so, or this is gonna get much much worse.  

If lets say I cant download the drivers, because I have no ethernet cord, and I transfer them to the ubuntu OS, how do I:

1) make them work
2) where do I transfer them to
3) is there any specific commands I need to do once I open the flash drive on ubuntu?

I REALLY REALLY would appreciate any and all help from anyone.  This is a big issue on the forums and I think alot of ppl would benefit from it.

---

### Post by jimrz on 2008-04-15
> **swimm3r137@gmail.com said:**
> Okay...  UGH, im frustrated, but i think this really really REALLY needs to be addressed.  It seems like the vast majority of users just cannot connect to the internet without problems.  Tell me if I'm wrong, but I think the issue is this (i'm a newbie, so bear with me)- Let's say you overwrite windows and install ubuntu.  Once you do so, ubuntui starts, but the windows wireless drivers that previously make your wireless card function are gone (because so is windows).  Because of this, they don't work.  DUH!  BUT, how the hell do you download drivers onto this computer, when the internet doesn't work.....???  Do you guys think I can download these drivers to a flash usb drive and then just transfer them to ubuntu on the laptop that doesn't have internet??  

If I can, the problem then becomes- WILL UBUNTU RUN THESE **WINDOWS** drivers correctly??  I hope so, or this is gonna get much much worse.  

If lets say I cant download the drivers, because I have no ethernet cord, and I transfer them to the ubuntu OS, how do I:

1) make them work
2) where do I transfer them to
3) is there any specific commands I need to do once I open the flash drive on ubuntu?

I REALLY REALLY would appreciate any and all help from anyone.  This is a big issue on the forums and I think alot of ppl would benefit from it.

First thing -  the win drivers you had in windows would not allow your card to work in linux, as they are completely separate OS's.
 (did your wifi work using the "live" cd? if so, then win drivers are not what you are missing.)

Next - please post the make / model / chipset of the card you are trying to use, so that others with the same can tell you how they were able to get theirs functioning. If you do not know the card info, open a terminal and type 
 ```
lspci
```
press enter and the output will give you the info.

Then, if needed, you can d/l the win drivers to a thumb drive or whatever and move them to your ubuntu machine for use with ndiswrapper should that be the solution for your card.

---

### Post by swimm3r137@gmail.com on 2008-04-15
My computer kept freezing when I attempted to install withthe "live cd."  Therefore, what I did was just download the alternate 64 cd and installed it with that, so I have no idea if the wifi would have worked with the live cd.  Heres what it said when I did "lspci":

alex@Ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
alex@Ubuntu:~$

---

### Post by jimrz on 2008-04-16
try looking in [[COLOR="Sienna"]**_this thread_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318") found by searching these forums for"BCM4318" which also returned many other hits.

---

