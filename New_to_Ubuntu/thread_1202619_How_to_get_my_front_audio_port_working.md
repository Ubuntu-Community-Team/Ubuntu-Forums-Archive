---
title: "How to get my front audio port working ?"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by Dark Star on 2009-07-02
I am using Ubuntu 9.04 and I am facing an issue. I cannot use my headphones/earphones using front audio port.. These port are working in windows without any problem.. I have AMD 790X motherboard with Realtek 8 channel audio ...

Here is lspci output 

```
shashwat@shashwat-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
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
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
shashwat@shashwat-desktop:~$ 

```

Please help me getting my front port working :KS

Regads

---

### Post by Dark Star on 2009-07-03
Someone please help.. I am really frustated, the front port didn't work in any distro :( While it work in WIndows..

---

### Post by FreewheelinFrank on 2009-07-03
Right click the volume control icon in the notification area.

Select 'Open volume Control'.

Select the 'Switches' tab.

Does 'Headphone' appear? Is it ticked?

Click on 'Preference'. Is 'Headphone' ticked?

Also check that the headphones are not muted by default:

[http://www.ericsprojects.com/?p=562](http://www.ericsprojects.com/?p=562)

---

### Post by Dark Star on 2009-07-03
Nope everything is configured as said. I have played a lot with mixer but to no avail. 

Here is the screenshot. [[IMG]http://img269.imageshack.us/img269/3411/screenshotifi.th.png[/IMG]](http://img269.imageshack.us/my.php?image=screenshotifi.png)

What else I need to do ? The headphones do work when I plug it at back audio port !

---

### Post by FreewheelinFrank on 2009-07-04
Googling "hda ati sb" returns a lot of hits. Some are quite old but they might be worth looking into. For example...

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

