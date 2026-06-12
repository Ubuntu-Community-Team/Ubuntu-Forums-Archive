---
title: "Clueless with wireless connection"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by abc006 on 2008-05-02
I've just installed ubuntu (Hardy Heron) for the first time, and I'm trying to make a wireless connection, but everything I've tried never works. First, I tried connecting manually - I put in all the information needed, I even called my wireless provider to make sure I was putting in the right stuff, but every time nothing worked. When looking into the basic help documents on Hardy Heron, it seems that they are either very outdated, not for the current release, or poorly worded and misleading. In the documentation, it states:
> Network Manager (System &#9656; Administration &#9656; Network) supports Roaming mode. This allows you to connect to any available wireless network in range.

   1. In the Taskbar click the Network Manager icon.
   2. Select your wireless network from the list.
   3. Enter your Network Key.
   4. Click Connect....Except there is no taskbar on the Network window, nor anything labeled Network Manager, nor any list with available wireless connections in the area. As you can see, I'm not familiar with ubuntu at all, so I'm pretty much clueless - but can *someone* give me some actual, "up-to-date" advice on how to simply connect, since through all my searching I've found really none. Thanks a lot for any help!

---

### Post by abc006 on 2008-05-03
Could someone please help me with this? Thanks a lot!

---

### Post by abc006 on 2008-05-04
PLEASE, could SOMEONE, ANYBODY, *please* help me with this? I've posted about this numerous times before, but no one has ever responded. Ubuntu is pretty much useless without internet access, let alone becing able to surf, I can't download programs, updates, etc. - please could someone help me? Thank you so much for your help again.

---

### Post by Ayuthia on 2008-05-04
Can you provide some information about your wireless?  To do this, you will need to go to the terminal and type:
```
lspci -nn
lsusb
```
The first one will list out your PCI information along with the id numbers and lsusb will list out your USB devices.  One of those should list out your wireless card.  Please post those results.  Thank you!

---

### Post by abc006 on 2008-05-07
This is what I got for "lspci -nn":

```
0:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
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
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
```

Thanks again.

---

### Post by Ayuthia on 2008-05-07
Your card needs some firmware in order to get it to work.  There is a menu option called Hardware Driver Manager (I think it is under System--I am a Kubuntu user so I am not familiar with the menu in Gnome anymore).  It will require a wired internet connection.

If you don't have an internet connection, you can try this thread: [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
There is a section on what files you need and how to install it. It also provides another option on installing the firmware without using the Hardware Driver Manager.

If you don't want to go this option, you can use NDISwrapper.  There is a link on how to install that in the link above also.

I have the same card as you so if you have any problems, feel free to ask for help here!

---

### Post by abc006 on 2008-05-08
OK, thanks! I'll try it out and see what happens.

---

### Post by abc006 on 2008-05-09
Hallelujah! What you suggested worked perfectly. Thanks so much.

---

