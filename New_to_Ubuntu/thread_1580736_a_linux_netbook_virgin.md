---
title: "a linux netbook virgin"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by edge0012 on 2010-09-23
hi guys!!
im a newbie, and i have installed a ubuntu netbook in my msi wind 12, just to have something new to try (got bored using windows) and it is really great!! :) though im still in the stage of exploration...
 
but my problem is this..
the installation comes with an application CHEESE, the one you can use to take picture. but it is not working well, and when i open it, it always say 'no device found' wher in fact, my netook has its own camera..... hmmm... 
 
what do you think guys???
 
by the way, may mga filipino ba dito?? hehehehe... tulong guys!!! ndi ko alam ang linux eh!!! :)

---

### Post by sandyd on 2010-09-23
> **edge0012 said:**
> hi guys!!
im a newbie, and i have installed a ubuntu netbook in my msi wind 12, just to have something new to try (got bored using windows) and it is really great!! :) though im still in the stage of exploration...
 
but my problem is this..
the installation comes with an application CHEESE, the one you can use to take picture. but it is not working well, and when i open it, it always say 'no device found' wher in fact, my netook has its own camera..... hmmm... 
 
what do you think guys???
 
by the way, may mga filipino ba dito?? hehehehe... tulong guys!!! ndi ko alam ang linux eh!!! :)
post output of
```

ls /dev/video*
lspci
```

---

### Post by jtarin on 2010-09-23
> **edge0012 said:**
> 
 by the way, may mga filipino ba dito?? hehehehe... tulong guys!!! ndi ko alam ang linux eh!!! :)
Walang problema ang sinasabi nila sa Subic!!:P

---

### Post by edge0012 on 2010-09-23
> **sandyd said:**
> post output of
```

ls /dev/video*
lspci
```
 
hmm...
what will i do with this?  :-k
sorry, i really  dont know anything... :confused:
please bear with me...;););)

---

### Post by Robert.Thompson on 2010-09-23
> **edge0012 said:**
> hmm...
what will i do with this?  :-k
sorry, i really  dont know anything... :confused:
please bear with me...;););)

Do: Accessories --> Terminal, then copy & paste the 1st line of code and hit enter then the second and hit enter.

Then while still in Terminal do: Edit -> Select All -> Copy.

Then paste the copied stuff into your post.

---

### Post by StephenF on 2010-09-23
I have a MSI Wind U100. To turn on the webcam requires Fn+F6.

---

### Post by edge0012 on 2010-09-23
> **Robert.Thompson said:**
> Do: Accessories --> Terminal, then copy & paste the 1st line of code and hit enter then the second and hit enter.
 
Then while still in Terminal do: Edit -> Select All -> Copy.
 
Then paste the copied stuff into your post.
 
 
[FONT=Fixedsys]ahh.. so that's how it is!!! :o[/FONT]
[FONT=Fixedsys]i'll try it later..[/FONT]
[FONT=Fixedsys]i think i'm gonna explore this forum a bit, so i'll learn a few tricks..[/FONT]
[FONT=Fixedsys]thanks a lot!!! :biggrin:[/FONT]

---

### Post by edge0012 on 2010-09-25
> **Robert.Thompson said:**
> Do: Accessories --> Terminal, then copy & paste the 1st line of code and hit enter then the second and hit enter.

Then while still in Terminal do: Edit -> Select All -> Copy.

Then paste the copied stuff into your post.

just did what you said,, and here's what happened..

[PHP]edge@edge-laptop:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
edge@edge-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
edge@edge-laptop:~$[/PHP]

so what do i do next???:confused:

---

