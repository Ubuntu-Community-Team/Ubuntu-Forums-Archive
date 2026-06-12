---
title: "Having Graphics Problems with 9.10"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by thevor on 2009-11-11
Hey,

I upgraded to 9.10 from 9.04 last night, and while most things are working just fine, I am definitely having problems with my graphics card. For whatever reason, when I goto into "Appearance", I can not activate the "normal", "Extra", or "Custom" settings, and when I try to enable them, I get an error message that says "Desktop Effects can not be enabled". In addition to this, or perhaps as a consequence of it, my whole environment is loading very slowly. Things such as scrolling through webpages, or opening a document, take a great deal longer than they did with 9.04. 

I am working with a Dell Inspiron 1525, which uses the Intel Integrated Graphics Media Accelerator X3100. I have had problems before with my intel chip with previous linux installations, but have always been able to find a work around, and this time I feel totally lost.

Has anyone stumbled upon this? Or found a solution? I was up all night last night searching for a solution and couldn't find one.

Hope someone can help.

Cheers

Thevor

---

### Post by thevor on 2009-11-12
Hey,

Anyone have any ideas about this? Sorry to bump my own thread, but I'd really like to get this working.

Thanks

The Vor

---

### Post by Ampi on 2009-11-12
Do you have Compiz or Compiz-fusion installed?
I thought that was necessary to get the visual effects normal and extra turned on.
Had some problems myself and haven't fixed everything yet, so I'm not sure if I can help you.

---

### Post by thevor on 2009-11-12
Ya compiz-fusion is installed, I just can't use any of it.  It's quite frustrating.

---

### Post by Ampi on 2009-11-12
You also installed the graphics drivers through System-Administration-Harware Drivers?
I also believe there are some problems with ATI drivers. So if you have ATI you might want to go to their webpage (so not through Ubuntu) and download the latest driver.

---

### Post by thevor on 2009-11-12
System-Administration-HarwareDrivers doesn't offer any graphics drivers for me. All it displays is a broadcom driver for my wireless, which is already installed and working fine.

I'll check the ATI though, thanks for your help

---

### Post by Tholley on 2009-11-12
If I an correct, anytime you install or uprade to a new version, you have to re-add the medibuntu repository. Kinda start all over...
 
See...
 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
 
Not sure if this is critical for visual effects, but maybe
 
Hope this helps...

---

### Post by braveheart2 on 2009-11-12
I am having the exact same problem, please help us :(

---

### Post by ubumania on 2009-11-13
Maybe the upgrade has resulted in the [compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check") having to be done again? Could the upgrade reset that kind of thing? I was just about to upgrade my Inspiron 1525 to 9.10 but am having doubts now???

edit: I have to run the compiz-check to get the restricted ATI driver working with desktop effects whenever I do a clean install but I didn't have to on the upgrade from 8.10 to 9.04.

---

### Post by thevor on 2009-11-14
Just ran compiz check, this was the output:

```

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use
 
```

This is getting very frustrating. It's like being on an old 486 or something. Has anyone heard of any solutions for this, or should I just revert back to 9.04?

---

### Post by TheNessus on 2009-11-14
You can download the latest driver from the ATI website and install it. from cmd, and turn off gdm before you do it.

---

### Post by Scarlath on 2009-11-14
When I googled, this was found: [http://ubuntuforums.org/showthread.php?t=1018240](http://ubuntuforums.org/showthread.php?t=1018240)

---

