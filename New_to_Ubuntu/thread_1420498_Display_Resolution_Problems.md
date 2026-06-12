---
title: "Display Resolution Problems"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by Loveablesurfer on 2010-03-03
Hi there :)

I've recently installed Ubuntu 9.10 onto a E-Systems 4213 Laptop. The display settings only give me 2 options 640 x 480 and 800 x 600. I installed Start-up Manager and set it to boot up with 1024 x 768, rebooted but it has no effect. I have also searched for propriety drivers in ADMINISTRATION - HARDWARE DRIVERS but it comes up with nothing. Is there anything else I can do to get the resolution up?

---

### Post by realzippy on 2010-03-03
Welcome!

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)


...if unsure what to do,open terminal,type:

**xrandr**

and post its output.

---

### Post by Loveablesurfer on 2010-03-03
Thanks Real Zippy

I tried it but no luck. The screen didn't change resolution momentarily and entering the code into the Default file didn't have an effect. Even after rebooting. Any other ideas?

---

### Post by halitech on 2010-03-03
what video card do you have? run
```
lspci
```
and post the output here if you aren't sure

---

### Post by realzippy on 2010-03-03
*Any other ideas?*

Sounds strange,but...sometimes it works:
Create a new user ("desktop-user",not root/admin account),log in/switchuser into that new created account,and see if resolution is also limited.If so,
you can delete this account.


BTW,
what command did you run exactly?
No error message?
(*..The screen didn't change resolution momentarily...*)

---

### Post by Loveablesurfer on 2010-03-03
> **halitech said:**
> what video card do you have? run
```
lspci
```and post the output here if you aren't sure

Here goes.....

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Thanks for you help! :D

---

### Post by Loveablesurfer on 2010-03-03
> **realzippy said:**
> *Any other ideas?*

Sounds strange,but...sometimes it works:
Create a new user ("desktop-user",not root/admin account),log in/switchuser into that new created account,and see if resolution is also limited.If so,
you can delete this account.


BTW,
what command did you run exactly?
No error message?
(*..The screen didn't change resolution momentarily...*)

I ran everything as described on the page you recommended. After running the addmode VGA1 and output VGA1 lines a load of code came up on the screen (no errors) but nothing changed resolution. Will try making a new user and get back to you.

Cheers!

---

### Post by Loveablesurfer on 2010-03-03
Ok. I tried creating a new user (desk top only) but still no improvement in resolution.

---

### Post by halitech on 2010-03-03
> **Loveablesurfer said:**
> Here goes.....

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Thanks for you help! :D

this is your video card
[color="red"]01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)[/color]

SIS is not well known for supporting Linux but maybe the info here will help

[http://ubuntuforums.org/showpost.php?p=6103534&postcount=11](http://ubuntuforums.org/showpost.php?p=6103534&postcount=11)

> 1. logout
2. press ctrl+alt+F1 (starts a virtual terminal)
3. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup041108 (best to backup settings)
4. sudo nano /etc/X11/xorg.conf (to edit the file)
5. go down to the Section "Monitor"and write in:
HorizSync 30-107
VertRefresh 50-185
then hit CTRL O to save, CTRL X to exit
6. press ctrl+alt+F7 (to go back to normal view)
7. press ctrl+alt+backspace (to restart the X server, just to make sure) and try logging in..


if that doesn't work, try the instructions here: [http://ubuntuforums.org/showpost.php?p=6129991&postcount=16](http://ubuntuforums.org/showpost.php?p=6129991&postcount=16)

---

### Post by Loveablesurfer on 2010-03-04
I tried doing ctl alt f1 when I was logged off but it didn't open a virtual terminal. The screen went black with a few jittery white lines and that was all that happened. After leaving it for about 5 min I had to force a shut down.

I'll try the other solution later today.

Thanks again

---

### Post by hobo14 on 2010-03-04
I wrote this howto after my possibly similar problem, it may help:

[http://ubuntuforums.org/showthread.php?t=1346125]("http://ubuntuforums.org/showthread.php?t=1346125")

---

