---
title: "Computer Freezing"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-08-02
Ever since upgrading to Lucid Lynx my computer will freeze up occasionally.  The computer starts slowing down, then the mouse icon stops moving and nothing works.  I have a cpu monitor running and it does not show the processor is over taxed.  Also a couple of lights on the keyboard will start flashing (I think the caps lock and num lock lights).  The only way for me to get out of this is to hit the power button on my computer and shut the computer down.

I have let this sit for several hours and it does not unfreeze by itself.  The hard drive light is not on - I don't know what's going on.  Could this be a hardware conflict?

---

### Post by LowSky on 2010-08-02
Sounds like bad RAM, or a loose connector to a hard drive or even the RAM not seated properly.

---

### Post by dondiego2 on 2010-08-02
Thanks, I will check that out.

---

### Post by terobin on 2010-09-02
I've been experiencing a similar problem, and the System Monitor is telling me I have 3 gigabytes of RAM when really I have 6, could this support the bad RAM theory?

It's dual boot with Windows 7 and I have never had a problem with freezing before while using Windows.

I seem to remember reading in a different thread that the problem lay with the driver for nvidea graphics cards, which I have.

---

### Post by Cypress421 on 2010-09-02
> **terobin said:**
> I've been experiencing a similar problem, and the System Monitor is telling me I have 3 gigabytes of RAM when really I have 6, could this support the bad RAM theory?

It's dual boot with Windows 7 and I have never had a problem with freezing before while using Windows.

I seem to remember reading in a different thread that the problem lay with the driver for nvidea graphics cards, which I have.

Are you running 64-bit Ubuntu? I tried the live cd (32-bit) and only 3GB was recognized (which is about right in terms of addressable memory) 64-bit clean install all 6 was recognized (well, 5.8GB).

---

### Post by terobin on 2010-09-03
No, I don't think I am running 64 bit. Will I have to download that and start from scratch?

Will I be able to save my preferences (theme/panel settings/etc) that I have now, install the 64 bit version, and then load in my saved preferences?

---

### Post by alphacrucis2 on 2010-09-03
> **terobin said:**
> No, I don't think I am running 64 bit. Will I have to download that and start from scratch?

Will I be able to save my preferences (theme/panel settings/etc) that I have now, install the 64 bit version, and then load in my saved preferences?

An option may be to use the pae version of the 32bit kernel which is able to utilise the extra RAM. Probably an easier solution than trying to figure out how to restore all your settings from a 32 bit to a 64 bit system.

[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

---

### Post by terobin on 2010-09-03
Installing the pae stuff from the instructions on that page worked for finding the rest of my RAM. Hopefully it'll stop the freezing too.

---

### Post by terobin on 2010-09-15
Installing that pae stuff seems to have solved the crashing problem.

---

### Post by dondiego2 on 2010-09-23
Mine is still locking up like I first posted - now 2 or 3 times a day.  I have a feeling it could be the  NVIDIA graphics driver.  I am running 10.04 (195.36.24) on a Compaq Presario that used to dual boot XP but now I just run Linux.

Anyway to troubleshoot this?

---

