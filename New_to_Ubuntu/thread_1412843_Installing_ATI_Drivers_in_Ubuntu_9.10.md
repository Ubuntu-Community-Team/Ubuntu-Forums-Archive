---
title: "Installing ATI Drivers in Ubuntu 9.10"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by david.rangel93 on 2010-02-21
Ok, so i have an ati radeon xpress 200 graphics card that is integrated into my motherboard. I recently started using Ubuntu 9.10 but i cant find the right driver for my computer. When i look in the hardware drivers it says "no propietary drivers are in use on this system"
My computer specifications are here [http://h10025.www1.hp.com/ewfrf/wc/docum…]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00579240&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=uk&product=1817973&lang=en") 
I am really struggling with this issue can anyone help?

And EnvyNG does not work with my computer. The drivers they show me are not recommended neither compatible.

---

### Post by tom.swartz07 on 2010-02-21
> **david.rangel93 said:**
> Ok, so i have an ati radeon xpress 200 graphics card that is integrated into my motherboard. I recently started using Ubuntu 9.10 but i cant find the right driver for my computer. When i look in the hardware drivers it says "no propietary drivers are in use on this system"
My computer specifications are here [http://h10025.www1.hp.com/ewfrf/wc/docum…]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00579240&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=uk&product=1817973&lang=en") 
I am really struggling with this issue can anyone help?

And EnvyNG does not work with my computer. The drivers they show me are not recommended neither compatible.

Im in the same boat- i have radeon X1270- and that isnt recognized either. 


Personally, I dont use too much 3D intensive things to be bothered, but when I do, I just reboot back to 8.04. 

If you really are into gaming, then XP or win7 is your best bet

---

### Post by sandyd on 2010-02-21
-> [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

and.
> AMD has moved a number of DX9 ATI Radeon&#8482; graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.

**The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):**

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
**ATI Radeon Xpress Series**
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series


AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Any customers using a combination of a ATI Radeon&#8482; HD 2000 Series, ATI Radeon&#8482; HD 3000 Series, or ATI Radeon&#8482; HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.   All future ATI Catalyst&#8482; releases made available past the ATI Catalyst&#8482; 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English)
^^
this.

---

### Post by 3rdalbum on 2010-02-21
> **david.rangel93 said:**
> Ok, so i have an ati radeon xpress 200 graphics card that is integrated into my motherboard. I recently started using Ubuntu 9.10 but i cant find the right driver for my computer.

ATI doesn't support the ATI Radeon Xpress 200 (or X1270) on Linux anymore, which is why you can't install any extra drivers for it.

The Linux community has developed an open-source driver for it which should be enough to run Compiz. This driver is available out-of-the-box on Ubuntu 9.10, so you're already using it.

In other words, you don't need to do anything more.

---

### Post by Mark Phelps on 2010-02-22
> **carlee said:**
> -> [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks for posting this info.  Seems none of the new posters care to do any research anymore.

And ... just to show you how much ATI has abandoned us (since the AMD merger), they have updated their Legacy MS Windows drivers (since 9.3) to 9.8, and now, to 9.11.  They have NOT updated their Linux drivers beyond 9.3.

---

### Post by david.rangel93 on 2010-02-22
OK so i know it comes out of the box and all that, but i always get an "input signal out of range" error every time i boot into ubuntu 9.10. I have two hard drives, one with Ubuntu and the other one with windows xp by the way. Is this another problem or does this also has to do something with the display driver also? Im struggling with this issue big time. :(

---

### Post by halitech on 2010-02-22
if you are getting an input out of range message then the driver is trying to display the output at a resolution higher then the monitor will support. I have the same issue everytime I update the ATI drivers and just have to adjust the xorg.conf file by hand to lower the resolutions it will try.

---

### Post by mcduck on 2010-02-22
> **david.rangel93 said:**
> OK so i know it comes out of the box and all that, but i always get an "input signal out of range" error every time i boot into ubuntu 9.10. I have two hard drives, one with Ubuntu and the other one with windows xp by the way. Is this another problem or does this also has to do something with the display driver also? Im struggling with this issue big time. :(
That would simply mean that while the driver is working fine it has troubles detecting your display. And that resylts in the driver trying to use wrong resolution.

Create /etc/xorg.conf file and define the correct resolution there.

You really have no other options, the open source driver is the only one that works for your graphics card (going back to old enough Ubuntu version to use the proprietary driver would only be a temporary solution until the support for that version ends).

---

### Post by tom.swartz07 on 2010-02-22
> **Mark Phelps said:**
> Thanks for posting this info.  Seems none of the new posters care to do any research anymore.


Im not looking to pick a fight, but I would like to point out that condescending comments like this are really a put-down to those of us that simply 'have less beans' than others. 

As many of us have stated, the drivers built in to the newer versions of Ubuntu work for these video cards right out of the box. Posting information about installing secondary drivers (that are not only no longer supported, but are unnecessary) will only confuse and blur the fact. 

This is an 'Absolute Beginners' forum, so the answers should be as simple and to-the-point as possible. If you want to use Jedi mind tricks and confuse people, do it in the Community Cafe and leave your elitism there.

---

