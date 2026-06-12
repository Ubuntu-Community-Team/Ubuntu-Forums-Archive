---
title: "Computer crashed!!!"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-09-28
Hello
My computer has an ATI graphic card which worked all fine with Ubuntu until I found out that the driver installed only supported 2D graphics and doesn't support 3D graphics.So I tried to install the ATI Catalyst from the add/remove button and after restarting my computer and booting to Ubuntu at first it looks like its loading but then the screen is simply mashed up and you cant see anything.
Please help

---

### Post by mosaabJ on 2009-09-28
My problem is still on please help

---

### Post by beak02 on 2009-09-28
I had exactly the same problem with my computer the first time I installed ubuntu.  Sadly - the only solution I could find was to re-install ubuntu via the CD.

---

### Post by cariboo on 2009-09-28
It would be helpful if you let us know what version you are using.

---

### Post by LowSky on 2009-09-28
and what vmodle number video card. ATI doesn't supprt anyhing earlier than the HD2xxx series under linux.

---

### Post by beak02 on 2009-09-28
If you know the program that caused the problem - could you hypothetically open up recovery mode, drop a root terminal and sudo apt-get remove it?

---

### Post by grturner on 2009-09-28
also what card are you using? The new ATI drivers aren't compatable with cards that are even a couple years old.? 

To try to fix it, after the computer boots up, press the key combination of CTRL+ALT+F1 to bring you out of X, login and then try the command
```
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by mosaabJ on 2009-09-28
My graphic card is ATI Radeon X1650

---

### Post by mosaabJ on 2009-09-28
> **beak02 said:**
> If you know the program that caused the problem - could you hypothetically open up recovery mode, drop a root terminal and sudo apt-get remove it?
I tried doing that the program name is ATI Catalyst but I really don't know what to write after sudo apt-get remove for the program name

---

### Post by argos3016 on 2009-09-28
linux resolution=1024x768 noprobe

---

### Post by OffAxis on 2009-09-28
> tried doing that the program name is ATI Catalyst but I really don't know what to write after sudo apt-get remove for the program name
```
aptitude search fglrx
```

returns

**fglrx-amdcccle** "-Catalyst Control Center for the ATI graphics..."


my guess would be it's that one.
If it's marked with an **i** on the left then it's "installed"

```
sudo apt-get remove fglrx-amdcccle
```

---

### Post by mosaabJ on 2009-09-29
> **OffAxis said:**
> ```
aptitude search fglrx
```

returns

**fglrx-amdcccle** "-Catalyst Control Center for the ATI graphics..."


my guess would be it's that one.
If it's marked with an **i** on the left then it's "installed"

```
sudo apt-get remove fglrx-amdcccle
```

Thank you and thanks to every one now I am writing from Ubuntu I just need one other favour and that is installing the driver for 3D graphics

---

### Post by OffAxis on 2009-09-29
did you originally use the Restricted Drivers Manager to install the driver?
That's by far the easiest way.

I think it's under 
**System-->Administration-->Restricted Drivers Manager**

---

### Post by mosaabJ on 2009-09-29
> **OffAxis said:**
> did you originally use the Restricted Drivers Manager to install the driver?
That's by far the easiest way.

I think it's under 
**System-->Administration-->Restricted Drivers Manager**

Thanks a lot OffAxis

---

### Post by OffAxis on 2009-09-29
you're welcome :)

---

### Post by mosaabJ on 2009-09-30
Sorry to bother you again I just want to ask. I don't have the restricted driver manager in my administration menu so how I can I install it, is it from the Synaptic Package Manager but how do you do that

---

### Post by starcannon on 2009-09-30
> **mosaabJ said:**
> Sorry to bother you again I just want to ask. I don't have the restricted driver manager in my administration menu so how I can I install it, is it from the Synaptic Package Manager but how do you do that
It's actually called Hardware Drivers:
System>Administration>Hardware Drivers

GL and HF

---

### Post by mosaabJ on 2009-10-03
I couldn't see any options in the hardware drivers section and the following screen shot is from my computer
[[IMG]http://img202.imageshack.us/img202/5117/screenshotc.th.png[/IMG]](http://img202.imageshack.us/i/screenshotc.png/)

---

### Post by mosaabJ on 2009-10-03
Can someone please help me:(

---

### Post by halitech on 2009-10-03
You don't mention what version of Ubuntu you are using but if its 9.04, then forget about getting 3d support with an ATI x1650 video card.

---

### Post by mosaabJ on 2009-10-03
> **halitech said:**
> You don't mention what version of Ubuntu you are using but if its 9.04, then forget about getting 3d support with an ATI x1650 video card.
Why is that? can you please give more details
Thanks

---

### Post by halitech on 2009-10-03
Basically because ATI has dropped support for older cards as seen here

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

Ubuntu 9.04 uses a newer Xorg then the driver supports so you will only have 2d support that is in the open source driver that 9.04 comes with.

---

### Post by mosaabJ on 2009-10-03
> **halitech said:**
> Basically because ATI has dropped support for older cards as seen here

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

Ubuntu 9.04 uses a newer Xorg then the driver supports so you will only have 2d support that is in the open source driver that 9.04 comes with.

Thanks for the help

---

### Post by clhsharky on 2009-10-03
Ubuntu 9.04 open source stack Radon driver fully supports ATI X1650 cards.
Including 3D

Status
R100/R200 (Radeon 7000 – Radeon 9250) and R300/R400/R500 (Radeon 9500 – Radeon X1950) class chips:
2D: accelerated (EXA), stable
XVideo: accelerated and tear free, stable
3D: accelerated, stable
[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)

Accelerated 3D support (r300, r400 and r500 series)

All these cards and derivatives have good 3D acceleration support

9500 / R300 based cards
9600 / rv350 or rv360 based cards
9700 / R300 based cards
9800 / R350 or R360 based cards
X300 / rv370 based cards
X600 / rv380 based cards
X700 / rv410 based cards
X800 / R420 or R423 or R430 or R480 based cards
X850 / R480 or R481 based cards
X1050 / rv370 based cards
X1300 / R515 based cards
X1600 / R530 based cards
X1800 / R520 based cards
X1900 / R580 based cards
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

 True ATI Catalyst drivers don't support legacy cards any more, but ATI Radon does. 2D is actually  better with the radon driver. I have a ATI X-1650 card,and it works quite well with oos including 3D.

---

