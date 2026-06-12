---
title: "[SOLVED] wireless issuse on  dual boot dell notebook"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by crazypenguin2008 on 2008-10-10
just installed wubi on my dell notebook at work that has to run windows. wireless works in windows but not in ubuntu. do i need a driver??

---

### Post by crazypenguin2008 on 2008-10-10
seems its not detecting the built in lan card.....

---

### Post by crazypenguin2008 on 2008-10-10
bump

---

### Post by Ayuthia on 2008-10-10
Can you go into the Terminal and post the results of:
```
lspci -nn
```It will help us figure out what your wireless card needs to make it work.

---

### Post by crazypenguin2008 on 2008-10-11
i ran that command but i dont see a way to get it from ubuntu to xp. i guess im just gona have to do a wired connection to get the wireless working. 

i do know its a 1390 broadcom card tho

---

### Post by Ayuthia on 2008-10-11
If you do the lspci -nn, what number shows up in the brackets?  It should be something like [14e4:4311] rev 01.  If it is a 4311 card, it will most likely work out of the box with 8.10.  It should be released on October 30.

Otherwise, you will need to get the firmware, use NDISwrapper, or install the wl driver from the Broadcom site.

---

### Post by crazypenguin2008 on 2008-10-11
crazypenguin@crazypenguin-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
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
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
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
crazypenguin@crazypenguin-laptop:~$ 

im on a wired connection. there the output of terminal

---

### Post by Ayuthia on 2008-10-11
I would first try and see if you can get it to work through System->Administration->Hardware Drivers.  If you are able to see something there for Broadcom b43, enable it.

If it is not there, go to either Synaptic and install b43-fwcutter or else go to the Terminal and do the following:
```
apt-get install b43-fwcutter
```
The process will ask you if you want it to search for the firmware for you.  Select ok and it should install the missing firmware.  It should ask you to reboot if I recall correctly.

---

### Post by crazypenguin2008 on 2008-10-11
crazypenguin@crazypenguin-laptop:~$ apt-get install b43-fwcutter
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
crazypenguin@crazypenguin-laptop:~$ 


didnt do anything

---

### Post by Ayuthia on 2008-10-11
> **crazypenguin2008 said:**
> crazypenguin@crazypenguin-laptop:~$ apt-get install b43-fwcutter
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
crazypenguin@crazypenguin-laptop:~$ 


didnt do anything

Sorry, that was my fault.  I meant to include the sudo:
```
sudo apt-get install b43-fwcutter
```

---

### Post by crazypenguin2008 on 2008-10-11
got it working. thanks :popcorn:

---

