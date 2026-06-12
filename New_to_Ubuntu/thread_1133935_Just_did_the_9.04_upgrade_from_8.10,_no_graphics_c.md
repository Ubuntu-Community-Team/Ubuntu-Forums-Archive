---
title: "Just did the 9.04 upgrade from 8.10, no graphics card listed"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ROUBOS on 2009-04-23
Hi people, I just let my machine do the upgrade from 8.10 to 9.04. 
The installation finished, and the new logon screen looks nice ;)
I get no loading screen, only have a blank screen when its loading. I don't see the orange bar, but that was happening before as well.

Anyway, I new that I had to re-install my graphics card drivers ATI 1950 pro, but under System>Administration>Hardware Drivers nothing is listed. 

What should I do with installing my graphics card?

EDIT > What's the new windows look in 9.04? The upgrade kept my Custom settings, Is it Human? How can I switch all to default 9.04 settings?

EDIT >>>> I get the following error when trying to install the latest ATI drivers from the AMD/ATI site:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

---

### Post by NuBiXx on 2009-04-23
I get the same error message when I try to install the driver from ati's site and no divers show up when I run "Hardware Drivers" can anyone help?

ubuntu 9.04 clean install
graphics card ati radeon x1300

---

### Post by Kareeser on 2009-04-23
Check to see if you've downloaded the right version. The file you've indicated above is for 64-bit architectures.

---

### Post by ROUBOS on 2009-04-23
It's the only available file to download. It worked when i installed it under 8.10.
Its the same file for 32bit and 64bit

---

### Post by NuBiXx on 2009-04-23
> **Kareeser said:**
> Check to see if you've downloaded the right version. The file you've indicated above is for 64-bit architectures.
the file supports both but we get that error
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.7&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.7&lang=English)

---

### Post by ROUBOS on 2009-04-23
ok go here: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I followed the manual install instructions using the ati driver we downloaded. Now the graphics card is listed under hardware drivers.

The problem is that when using the fglrx driver in /etc/X11/xorg.conf it gives me a black screen on reboot. When using the ati or radeon driver it loads into ubuntu, but no Combiz and the Graphics Card is not enabled.

here is my xorg.conf file:
---------------------------

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "radeon"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

-----------------------------------------

try it out and it might be a xorg problem. see what you can manage and let me know

GOOD LUCK

---

### Post by ROUBOS on 2009-04-24
OK just did a fresh install of Ubuntu 9.04 and my ATI X1950pro card is not listed under System>Administration>hardware Drivers :(

Cannot install any drivers realy if it's not listed, even though lspci give me these:

01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)


Any thoughts?

---

### Post by ROUBOS on 2009-04-24
OK. After reading and wasting all night trying to fix it, I gave up.
Looks like I need a new PC and never getting an ATI card again.
So, back to a clean install of Ubuntu 8.10.
At least my card works...

---

### Post by NuBiXx on 2009-04-24
> **ROUBOS said:**
> OK. After reading and wasting all night trying to fix it, I gave up.
Looks like I need a new PC and never getting an ATI card again.
So, back to a clean install of Ubuntu 8.10.
At least my card works...

yeah I went back to 8.10 also after trying all night yesterday to get the drivers to work my card (ATI x1300) is not listed under System>Administration>hardware Drivers also. I guess we'll have to wait awhile for proper driver support..

---

### Post by triniclemist90 on 2009-04-24
I am having the same problem.  The weird thing is that I had full driver support in 9.04 beta until the day before the stable release.  I noticed that I had to update so I did and I lost compiz and emerald and it stopped letting me use any visual effects.  They had it right and then killed it the day before the final release.  They need to go back and use the drivers from the beta.

---

### Post by AFarris01 on 2009-04-24
This is odd... my fiancé had a similar issue when she upgraded her pc from 8.10 to 9.04, compiz quit working and the graphics card wont show up under "hardware drivers," but it worked just fine in 8.10. wierd part is though, she's got an nVidia 9600GT... 

...*sigh*...

---

### Post by ROUBOS on 2009-04-24
I just installed 8.10 and everything works sweet. Not going to 9.04 until i get a new PC and no more ATI for me....

---

### Post by NuBiXx on 2009-04-27
anyone one with simaler video cards as us get the drivers to work?

---

### Post by Didius Falco on 2009-04-28
Hello All,

This from ATI:

> AMD has moved a number of DX9 ATI Radeon™ graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.
 The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):
 ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series
 
AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.
 Any customers using a combination of a ATI Radeon™ HD 2000 Series, ATI Radeon™ HD 3000 Series, or ATI Radeon™ HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.   All future ATI Catalyst™ releases made available past the ATI Catalyst™ 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.



So the ATI FGLRX 9.4 Driver won't work in Ubuntu. The other half of that catch-22 is that the 9.3 drivers do not support the latest version of X.org, which is in 9.04, so none of the proprietary drivers will work for those with those older cards.

There are Open Source X.org drivers in Synaptic that will work, but with no 3D support at this time - the Open Source developers are still working on them, trying to get 3D to work.

No 3D means no Compiz and no visual effects under Metacity. The driver will work in 2d, but it's far from snappy.

It's up to you, but if it were me, I'd wait until I got a newer graphics card to go to 9.04.

At any rate, at least you know why you've had the problem now.

Sorry to be the bearer of ill tidings...

---

### Post by Blara on 2009-04-28
> **Didius Falco said:**
> Hello All,

[...]
There are Open Source X.org drivers in Synaptic that will work, but with no 3D support at this time - the Open Source developers are still working on them, trying to get 3D to work.

No 3D means no Compiz and no visual effects under Metacity. The driver will work in 2d, but it's far from snappy.

It's up to you, but if it were me, I'd wait until I got a newer graphics card to go to 9.04.

At any rate, at least you know why you've had the problem now.

Sorry to be the bearer of ill tidings...

I find the open source driver to be better at managing 2D graphics... Just too bad that 3D doesn't work yet BUT ATI did release the documentation so it should speed up the process, in the meantime I'll revert back to 8.04 or 8.10

---

### Post by svamppi on 2009-04-28
Even though every upgrade since ubuntu 6.something has resulted in nothing but trouble for me I couldn't resist trying to upgrade to 9.04. But after reading that Ati statement I feel effed in the aye. I'm also starting to think I should never buy an Ati card again.

---

### Post by NuBiXx on 2009-04-28
ATi Radeon HD4770 was released today I was thinking of ordering one do you think I'll have any problems with that card?
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Description=hd%204770&bop=And&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Description=hd%204770&bop=And&Order=PRICE)

---

### Post by Didius Falco on 2009-04-29
> **NuBiXx said:**
> ATi Radeon HD4770 was released today I was thinking of ordering one do you think I'll have any problems with that card?
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Description=hd%204770&bop=And&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Description=hd%204770&bop=And&Order=PRICE)

Only with your friends being jealous. :popcorn:

---

### Post by Jeanke on 2009-05-02
Same problem here...

---

### Post by clhsharky on 2009-05-02
Open Source X.org drivers in 9.04 do have 3D suport in ATI X series chips.
 
X.Org Wiki - radeon

[Status

    * R100/R200 (Radeon 7000 – Radeon 9250) and R300/R400/R500 (Radeon 9500 – Radeon X1950) class chips:
          o 2D: accelerated (EXA), stable
          o

            XVideo: accelerated and tear free, stable
          o 3D: accelerated, stable]

Compiz does work in 9.04 with X1650 card.

---

