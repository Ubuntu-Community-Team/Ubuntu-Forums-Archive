---
title: "Compiz wont run"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by sixthwheel on 2010-03-16
When I start Compiz in the terminal, this is the output I'm getting.

peter@peter-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!

---

### Post by sixthwheel on 2010-03-16
Video card is an ATI Radeon 9200

---

### Post by halitech on 2010-03-16
what version of Ubuntu are you running? Chances are if you have 9.04 or above, you are using the opensource drivers which, as far as I know, don't support 3d (yet) so compiz won't run.

---

### Post by sixthwheel on 2010-03-16
> **halitech said:**
> what version of Ubuntu are you running? Chances are if you have 9.04 or above, you are using the opensource drivers which, as far as I know, don't support 3d (yet) so compiz won't run.

Do you know if this issue is going to be fixed in Lucid, or do I need a new card?

---

### Post by halitech on 2010-03-16
Unfortunately I'm not a dev so I have no idea what will be included or not included. It may work better in Lucid when it's released but I don't know. Safest bet might be to get a newer card so you know it will work.

---

### Post by Tikkyca on 2010-03-16
I think you need to reinstall your drivers and see if it works.

---

### Post by halitech on 2010-03-16
> **Tikkyca said:**
> I think you need to reinstall your drivers and see if it works.

the only drivers the OP can install are the opensource drivers. Trying to install the ATI drivers will result in a borked system and ubuntu doesn't provide proprietary drivers for that card.

---

### Post by Tikkyca on 2010-03-16
> **halitech said:**
> the only drivers the OP can install are the opensource drivers. Trying to install the ATI drivers will result in a borked system and ubuntu doesn't provide proprietary drivers for that card.

That means he needs to buy a new graphic card,or wait for stable drivers to come out,i have ATI graphic card everything works good with my model.

---

### Post by halitech on 2010-03-16
there won't be any *stable* drivers for it. ATI dropped support for everything under the HD2400 series and 3d probably isn't a priority for the people developing the open source driver. I have an HD4350 and it works perfectly as well. If the OP is happy without 3d support and not running compiz then they don't need to do anything.

---

### Post by clhsharky on 2010-03-16
HI

ATI does actively support legacy cards with the open source radeon driver.

[HTML]SUPPORTED HARDWARE
       The  radeon driver supports PCI, AGP, and PCIE video cards based on the
       following ATI chips:

       R100        Radeon 7200
       RV100       Radeon 7000(VE), M6, RN50/ES1000
       RS100       Radeon IGP320(M)
       RV200       Radeon 7500, M7, FireGL 7800
       RS200       Radeon IGP330(M)/IGP340(M)
       RS250       Radeon Mobility 7000 IGP
       R200        Radeon 8500, 9100, FireGL 8800/8700
       RV250       Radeon 9000PRO/9000, M9
       RV280       Radeon 9200PRO/9200/9200SE/9250, M9+
       RS300       Radeon 9100 IGP
       RS350       Radeon 9200 IGP
       RS400/RS480 Radeon XPRESS 200(M)/1100 IGP
       R300        Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1
       R350        Radeon 9800PRO/9800SE/9800, FireGL X2
       R360        Radeon 9800XT
       RV350       Radeon 9600PRO/9600SE/9600/9550, M10/M11, FireGL T2
       RV360       Radeon 9600XT
       RV370       Radeon X300, M22
       RV380       Radeon X600, M24
       RV410       Radeon X700, M26 PCIE
       R420        Radeon X800 AGP
       R423/R430   Radeon X800, M28 PCIE
       R480/R481   Radeon X850 PCIE/AGP
       RV505/RV515/RV516/RV550
                   Radeon X1300/X1400/X1500/X2300
       R520        Radeon X1800
       RV530/RV560 Radeon X1600/X1650/X1700
       RV570/R580  Radeon X1900/X1950
       RS600/RS690/RS740
                   Radeon X1200/X1250/X2100
       R600        Radeon HD 2900
       RV610/RV630 Radeon HD 2400/2600
       RV620/RV635 Radeon HD 3450/3470
       RV670       Radeon HD 3850/3870
       RS780       Radeon HD 3100/3200/3300
       RV710       Radeon HD 4350/4550
       RV730       Radeon HD 4650/4670
       RV770       Radeon HD 4850/4870
[/HTML]

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

Your distro and drivers may not be new enough for Radeon features 
listed.

Sharky

---

### Post by lidex on 2010-03-16
Can you provide the output of this terminal command:
```
lspci -nn | grep VGA
```

In your Applications menu: "Accessories>Terminal"

> Full 3D support (r100 and r200 series)

All these cards and derivatives have full 3D acceleration support

7000 / rv100 based cards
7200 / R100 based cards
7500 / rv200 based cards
8X00 / R200 based cards
9000 / rv250 based cards
9100 / R200 based cards
9200 / rv280 based cards

From this page: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by sixthwheel on 2010-03-17
> Can you provide the output of this terminal command:

```
peter@peter-desktop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200] [1002:5961] (rev 01)
peter@peter-desktop:~$ 

```

---

### Post by lidex on 2010-03-17
> **sixthwheel said:**
> ```
peter@peter-desktop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200] [1002:5961] (rev 01)
peter@peter-desktop:~$ 

```
So it should work. Follow instructions in the link in my previous post.

---

