---
title: "Two seperate hard drives for different OS"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by paul6 on 2011-03-26
I want to set up my dual boot system like this:

1 hard drive for Windows 7
1 hard drive for Ubuntu
1 hard drive for data storage (Windows Formatted)

However, I want to have only 1 OS hard drive plugged in to the motherboard at a time, so I will manually plug in the hard drive of the OS I want to run.

This will save me from having to use GRUB, and also will conserve the life of the OS hard drive that is not hooked up.

Will this type of strategy work?

---

### Post by Hedgehog1 on 2011-03-26
If you use a drive tray and swap the 'OS' drive(s) when powered down:

[IMG]http://images.highspeedbackbone.net/SKUimages/gallery/large/I202-1030-call01-or.jpg[/IMG]

Or a 'drive dock' with eSATA:

[IMG]http://images.highspeedbackbone.net/skuimages/large/S262-7198-main01-op.jpg[/IMG]

Then you can have an unlimited number of OS's and a common internal 'data storage' drive.

As a note, the Ubuntu Hard Drive will put grub on itself to boot Ubuntu, but you will not see it unless you need it, and then hold down the "Shift" key during reboot to get it to show.


***The Hedge***

:KS

p.s. As cheap as hard drives are today, this concept has some real merit if you want ***complete isolation*** of your OS's.

---

### Post by andrewthomas on 2011-03-26
> **paul6 said:**
> 
However, I want to have only 1 OS hard drive plugged in to the motherboard at a time, so I will manually plug in the hard drive of the OS I want to run.

This will save me from having to use GRUB, and also will conserve the life of the OS hard drive that is not hooked up.

Will this type of strategy work?
This will eventually break the motherboard due to the excessive plug-unplug operations (way quicker than any HD would fail due to usage.)

If you really want to go with this option, just disable the drives that you choose not to use in BIOS.

---

