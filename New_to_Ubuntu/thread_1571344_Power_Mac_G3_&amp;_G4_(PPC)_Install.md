---
title: "Power Mac G3 &amp; G4 (PPC) Install"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by techgrl on 2010-09-09
What is the best distro & instruction set to install Linux on Power Macs? I have Blue/White G3's and Gray/White G4's. I also have a ton of little blue/white cube iMac G3's.

Our company upgraded a department's hard/software and we are left with an entire room of old MACS that I want to re-purpose and give away.

In order to get OS9 off of these relics and make them usable, I am trying Ubuntu 7 (alt CD) and Debian.

I get so far in the install and end up getting stuck on random black screens.

My favorite so far is: initramfs.

I would take any advice you have to offer.

Thank you in advance.

---

### Post by halitech on 2010-09-09
if you want to go Debian there is a nice tutorial here: [http://forums.debian.net/viewtopic.php?f=16&t=43326](http://forums.debian.net/viewtopic.php?f=16&t=43326)

---

### Post by khelben1979 on 2010-09-09
I'm running Debian 6.0 "Squeeze" over here with an Powerbook G3 which only have 128 MB of RAM with working graphics and everything, so I think that Squeeze should be okay for even that kind of hardware.

I'm curious, how much RAM do they have?

---

### Post by techgrl on 2010-09-10
There are random RAM allotments for the stockpile of machines I am working with. I try to make sure they have 512MB, but it's old PC133 or 100, so if I haven't been pack-ratting, some will likely have 128MB.

The Squeeze install went wonderfully. Smooth. BUT...BUT, upon first launch I have a display issue. I can see a very pixel-filled bottom white bar where the taskbar should be, but that is where it freezes.

I have tried Control F1 to get into an editor to modify resolution allowances, but honestly, I don't know exactly how to force it into a terminal session.

After that, I THINK I use the gedit command somehow to USE the editor. Any suggestions?

---

### Post by khelben1979 on 2010-09-11
Just press ctrl + alt + fn + 1 to get to a tty text terminal. By default, the Debian system chooses a suitable graphic driver from the Linux kernel. Hopefully the X server detects your monitor by plug and play, and allows you the screen resolutions which is supported by the monitor.

As a text editor, I would recommend [Emacs]("http://en.wikipedia.org/wiki/Emacs").

---

### Post by mogwhy901 on 2010-11-12
i am running the officially unsupported 10.10 ubuntu on a mac g4 and its all good bar one thing, i dont know how to change the screen res from the default of 800 x 600 on it ,  my monitor is 1024 x 768 so any help here would be top. but bar the res issue its running everything without undue delays.:)

---

### Post by cek on 2010-11-12
For the PowerPC architecture, I've always heard good things about Yellow Dog Linux -- though, never used it myself.

---

### Post by mister_playboy on 2010-11-12
> **cek said:**
> For the PowerPC architecture, I've always heard good things about Yellow Dog Linux -- though, never used it myself.

[Their hardware page](http://ydl.net/support/hardware/) mentions G4 computers but not G3s for the current YDL 6.x

The future of YDL on PPC processors is up in the air now that the last real hardware target (PS3 Linux installs) has faded into history.

---

### Post by halitech on 2010-11-14
> **mogwhy901 said:**
> i am running the officially unsupported 10.10 ubuntu on a mac g4 and its all good bar one thing, i dont know how to change the screen res from the default of 800 x 600 on it ,  my monitor is 1024 x 768 so any help here would be top. but bar the res issue its running everything without undue delays.:)

try this from the link I posted on the Debian install

[http://forums.debian.net/viewtopic.php?f=16&t=43326](http://forums.debian.net/viewtopic.php?f=16&t=43326)

> 
Step 8: Now type:

Code: Select all
    nano /etc/X11/xorg.conf

and add the these lines:

Code: Select all
    Section "Screen"
       Identifier "Default Screen"
       Monitor "Default Monitor"
       DefaultDepth 16
    EndSection
    Section "Monitor"
       Identifier "Default Monitor"
       HorizSync 58-62
       VertRefresh 75-117
    EndSection
    Section "Device"
       Identifier "Video Card"
    EndSection

(Note by pressing command+o, hitting enter, and then pressing command+x you have saved and exited) This is a graphical setup designed to conserve my precious graphics card resources. 3D rendering isn't enabled by default, but I don't care as all I need is 2D rendering. If you want 3D rendering, then you should look into compiling the latest drm and the latest mach64 driver. The reason its not included by default is that it may still have some security issues.


it worked for me in Debian

---

