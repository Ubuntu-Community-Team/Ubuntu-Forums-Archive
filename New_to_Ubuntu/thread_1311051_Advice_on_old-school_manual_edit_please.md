---
title: "Advice on old-school manual edit please"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-02
Advice on old-school manual edit please

Hi, 

I have a great crt monitor (with which i had a res 1600x1200 @ 75/85Hz) which i want to keep. Koala recommends i install nvidia 173 driver but if i do, the install res of 800x600 in Koala drops to 600x480 and the nvidia gui - if it works, is to big to operate on the display. 

I understand a solution is to manually edit:

 /etc/X11/xorg.conf

substituting a few lines.

However it's been a while since i solved this prob -or edited a file, and foolishly i didn't keep a record of how i was guided through this procedure and i need a lot of help. 

Here is what there is in Koala. Can anyone advise me please ?

nnjond@den-desktop:~$ cd /etc/X11
nnjond@den-desktop:/etc/X11$ ls
app-defaults             fonts    xinit      Xresources  Xsession.options
cursors                  rgb.txt  xkb        Xsession    XvMCConfig
default-display-manager  X        xorg.conf  Xsession.d  Xwrapper.config
nnjond@den-desktop:/etc/X11$ 


If you have any ideas, please make sure i can get back to 800x600, because 600x4800 is a strain on my eyes.

Thanks.

nnjond@den-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
nnjond@den-desktop:~$

---

