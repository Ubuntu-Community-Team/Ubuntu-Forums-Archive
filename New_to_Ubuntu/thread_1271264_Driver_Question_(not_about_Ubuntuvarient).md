---
title: "Driver Question (not about Ubuntu/varient)"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by MiniStephan on 2009-09-20
My girlfriend has a rather old computer, and it's currently running Windows 2k.  We tried plugging in her flash drive so that she could run Firefox off of it (it won't fit on the tiny hard drive they have internally).  However, the driver wouldn't install, it couldn't find it, whatever.  So I'd like to be able to install the driver manually, but the HP website doesn't have a driver download for the flash drive.  Can anyone help me with this?  I can't figure out what to do.

Oh and feel free to relocate this if you think it's in the wrong section.

The flash drive is an HP v125w 2GB Flash Drive.

---

### Post by Yvan300 on 2009-09-20
Wow, windows 2k, if the flash drive was recently manufactured then most likely there won't be a proper driver for it. As far as i know after a few years a version of windows stops receiving updates and stuff and thus a old thing like windows 2000 will have poor support for newer hardware. Why not install puppy linux on it or something, that would solve your problem.

---

### Post by Flying caveman on 2009-09-20
I would do some house cleaning to make more room on the internal hard drive, then see if the manufacturer of the flash drive has a driver for Windows 2000.

---

### Post by Whiffle on 2009-09-20
Sounds like the usb mass storage driver won't load, which is the driver all flash drives use.  

What happens when you plug it in?

---

### Post by MiniStephan on 2009-09-20
It's her family's computer, so there's no chance of me putting linux on it.  Also, it's a 4 GB internal hard drive, so there's no chance of doing house cleaning.  That was the first thing I checked.

Anyway, when I plug it in, it just pops up as "USB Device" or....something like that, but it says the driver isn't working properly.  Will just a generic USB Mass Storage Device driver work, or do I need a specific one?

---

### Post by Whiffle on 2009-09-20
They're generic.  But before you do that, go to the device manager (Right click on my computer, its somewhere in there), and make sure all the USB drivers for the USB hardware on the computer are installed.

---

