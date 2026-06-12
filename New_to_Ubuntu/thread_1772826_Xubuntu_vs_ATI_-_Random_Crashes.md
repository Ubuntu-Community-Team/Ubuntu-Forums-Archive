---
title: "Xubuntu vs ATI - Random Crashes"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by GaryTheCat on 2011-06-01
Hello

I've just installed xubuntu on an old desktop for my son - after installing it I realised that the hardware is pretty much ATI everything

lspci gives:

```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

```

What logfiles would anyone willing to help need to look at and where would I find them?

Many thanks

G

---

### Post by Toz on 2011-06-01
It kind of depends on what sort of crashes they are (application, system, hardware, etc). You can look at the .xsession-errors and .xsessions-errors.old files in your home directory and the various log files in /var/log. Here is a link that might help: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

If they are application-type crashes, you can also help diagnose the problem by running the application executable on a terminal window and seeing what output emerges after the crash.

---

### Post by GaryTheCat on 2011-06-01
I installed Xubuntu 10.04 from a live CD and then upgraded to 10.10 then to 11.04.

Is there any value in reinstalling 10.04 and not upgrading it?

If so, how do I do it?

---

### Post by Toz on 2011-06-01
It depends. I run 11.04 with an ATI card (HD2600) with the proprietary drivers and am not having any problems. Perhaps you can give us a better idea of what sorts of problems/crashes you are having. Perhaps we can help.

---

### Post by GaryTheCat on 2011-06-01
I think I've made a bit of a mess of it with trying to resolve this and some wireless issues - I'm going get rid of xubuntu 11.04 and replace with 10.04

---

### Post by mastablasta on 2011-06-01
if you decide to use 10.04 LTS you probably should upgrade the opensource graphics drivers using x-org edgers PPA.
 
Poor performance is probably caused by bad graphics card drivers for your chip:
ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

 
more info on this topic can be found here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Also if you wish to run 11.04 it would be better to just download 11.04 CD and do a fresh install rather than upgrading.

---

### Post by GaryTheCat on 2011-06-05
I decided to do a fresh install of xubuntu 11.04.

Still getting the odd 'black screen of death' with a lot of scrolling text.

Which log files would I need to post for someone to be able to help to diagnose the problem and where might I find them? 

Many thanks

G

---

### Post by Mark Phelps on 2011-06-06
Did you try mastablata's solution using the PPA?

If not, do THAT before expecting us to read through lengthy logs.

If the PPA approach doesn't solve the problem -- then you're stuck because the default open-source drivers don't work properly with your video card, and the PPA approach is the only alternative.

---

