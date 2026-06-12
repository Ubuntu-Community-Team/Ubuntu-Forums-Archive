---
title: "Broken NVIDIA Driver"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Unanimated on 2009-02-06
When I connect my PC to my TV through S-Video and to the monitor at the same time, my driver completely freaks out. The TV screen goes completely white, then zooms in on a certain section of the wallpaper. Then, on the monitor, the panels come up completely clear with no icons. I have to unplug the TV then restart the X server for it to work again. I'm using 180.22 downloaded from the NVIDIA site, as the proprietary drivers in Ubuntu won't download. When they do, I get a message saying that it failed to load the NVIDIA kernel module and then it runs in low-graphics mode. I'm using kernel 2.6.27-11-generic.

NOTE: This worked perfectly before the upgrade, and I do not wish to downgrade - after all, when it upgrades the kernel again, I'll have this same problem, so I want to fix it now.

EDIT: GLXGEARS, 5 cycles result:
```
9 frames in 5.1 seconds =  1.762 FPS
8 frames in 5.5 seconds =  1.455 FPS
9 frames in 5.3 seconds =  1.683 FPS
9 frames in 5.4 seconds =  1.663 FPS
8 frames in 5.3 seconds =  1.521 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 92 requests (89 known processed) with 0 events remaining.

```

LSPCI output:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)

```

Obviously, my video card should be able to handle glxgears. I ran it shortly after installing the card, and I was getting framerates in the thousands.

---

### Post by Unanimated on 2009-02-06
Even running something fullscreen is too much for it - I opened ZSNES and closing it was a 10 minute long fiasco that ended with me typing sudo killall ZSNES into runlevel 1. It's not even plugged into the TV right now.

---

### Post by Unanimated on 2009-02-06
I reconfigured the X server (sudo dpkg-reconfigure xserver-xorg) then restarted the server. I reinstalled the 180.22 driver, no errors came up, but there is no change at all. What's going on?

---

### Post by mpl34 on 2009-02-06
An easy way to see which driver is in place is to download
compiz-check given [here]("http://forlong.blogage.de/entries/pages/Compiz-Check"), and follow the instructions it will tell u what driver is running.

I don't no if this is of much help but i found it extremely useful

---

### Post by Unanimated on 2009-02-07
```
 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV43 [GeForce 6200] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

But the question still remains. I ran glxgears after running compiz-check, with the same result. :|

---

### Post by mpl34 on 2009-02-07
Hmm well looks like the NVidia driver is installed correctly, however i do no that when the driver is installed it is specific to the kernel module and may need to be recompiled with the new module. I had a problem with running the NVidia driver after the upgrade and found information telling me to re-install after updating the kernel and it seemed to fix my problems. If you've got the driver its only a 5min process so i sujjesting giving it a try.

---

### Post by Unanimated on 2009-02-07
I've reinstalled the driver at least 5 times today, and it's still like this.

---

### Post by mpl34 on 2009-02-07
The glxgears results do seem strange but sorry i'm not going to be of much more help i'm still pretty new

---

