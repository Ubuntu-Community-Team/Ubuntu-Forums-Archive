---
title: "Acer Aspire One 751 Problems"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Yizi on 2010-03-11
I just bought a Aspire one 751 and installed a fresh copy of ubuntu, but there are some problems with the graphic card, there was some threads regarding that and i followed them carefully and there was no result!

Anyone know how i can sort it out, anyone with the Aspire One 751?

---

### Post by audiomick on 2010-03-11
Perhaps you could post a description of the problems and the output of
```
lspci
```to show what the graphics card is.

---

### Post by Yizi on 2010-03-11
```
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by bodhi.zazen on 2010-03-11
Can you be more specific ?

What problem are you having ? 

What have you done to try to fix the problem ?

What Acer (how big is the screen) ?

What version of Ubuntu ?

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by Yizi on 2010-03-11
This link should give you all the details you need:

[http://www.acer.co.uk/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=60839&sp=page16e&ctx2.c2att1=17&link=ln438e&CountryISOCtxParam=UK&ctx1g.c2att92=842&ctx1.att21k=1&CRC=1471684927](http://www.acer.co.uk/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=60839&sp=page16e&ctx2.c2att1=17&link=ln438e&CountryISOCtxParam=UK&ctx1g.c2att92=842&ctx1.att21k=1&CRC=1471684927)

The problem i have is the graphic issue, it's laggy, looks like there is no driver setup for it, i followed few post that pretty much had my problem, but i have 9.10 installed so its a diffrent story.

---

### Post by bonethug on 2010-03-11
Could you do ```
lspci -nn|grep VGA
``` and paste the output?

---

### Post by Yizi on 2010-03-11
```
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)

```

---

### Post by bonethug on 2010-03-11
Ok, seems that your card is Intel Graphics Media Accelerator 500.
I've found a guide which describes how to fix your issue on [http://www.linlap.com/wiki/acer+aspire+one+751#Graphics](http://www.linlap.com/wiki/acer+aspire+one+751#Graphics). 
Try it and follow it's instructions. Hopefully it will work.

---

### Post by bonethug on 2010-03-11
..and [http://touchstudio.wordpress.com/2009/05/31/acer-aspire-one-1366x768-graphics-driver-needed/](http://touchstudio.wordpress.com/2009/05/31/acer-aspire-one-1366x768-graphics-driver-needed/)

---

### Post by bodhi.zazen on 2010-03-11
> **Yizi said:**
> This link should give you all the details you need:

[http://www.acer.co.uk/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=60839&sp=page16e&ctx2.c2att1=17&link=ln438e&CountryISOCtxParam=UK&ctx1g.c2att92=842&ctx1.att21k=1&CRC=1471684927](http://www.acer.co.uk/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=60839&sp=page16e&ctx2.c2att1=17&link=ln438e&CountryISOCtxParam=UK&ctx1g.c2att92=842&ctx1.att21k=1&CRC=1471684927)

The problem i have is the graphic issue, it's laggy, looks like there is no driver setup for it, i followed few post that pretty much had my problem, but i have 9.10 installed so its a diffrent story.

I have that exact model and the best you can do is to run the script on this page:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Direct link (to the script) :

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo?action=AttachFile&do=get&target=poulsbo.sh](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo?action=AttachFile&do=get&target=poulsbo.sh)

This page will give you additional details as well:

[https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)

This second page will go through how to install and configure the driver manually, but all those changes are made by the script in the first link, so you do not need to manually do anything but run the script as root.

The driver needs to be updated with each kernel.

With that said, the driver is buggy to say the least.

---

### Post by cgriffith on 2010-03-12
I also have that same model.  Follow the advice of bodhi.zazen.  The only other thing I would add is...

1) keep an eye on this thread for updates: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

2) If you find after installing the psb drivers that you can't suspend/resume try a trick I recently found described in that forum that causes the 98smart-kernel-video pm-util script to not get executed.

Also, please let me know how #2 goes cause I am trying to get feedback if this is a valid tip.

I have not had any issue with these psb drivers and am satisfied with the performance.

---

