---
title: "How do I install XP from Ubuntu?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by SwooshOU on 2008-12-30
So, I've tried Ubuntu for a couple weeks.

I am just not familiar enough with how to do things on it to keep it.

So, I put the XP restore CD in and hold the F9 key to select the external USB drive (I have a netbook with no CD drive).  However, the only option is the internal drive.

So, add this to my frustrations of not knowing what to do in Ubuntu.

The CD is able to be read when the Ubuntu desktop is loaded.  It's just not able to run the restore CD by double clicking the restore.exe nor on startup.

Thanks for the help.

---

### Post by oilchangeguy on 2008-12-30
you can't install windows from within ubuntu. if your computer no longer has a working cd drive, have you checked ebay, for a replacement?

---

### Post by SwooshOU on 2008-12-30
> **oilchangeguy said:**
> you can't install windows from within ubuntu. if your computer no longer has a working cd drive, have you checked ebay, for a replacement?

I have an external USB CD Drive.  That is what I am trying to get my computer to recognize upon startup so that I can run the XP software restore.

---

### Post by oilchangeguy on 2008-12-30
> **SwooshOU said:**
> I have an external USB CD Drive.  That is what I am trying to get my computer to recognize upon startup so that I can run the XP software restore.

have you entered the bios, to see what boot options are available?

---

### Post by SwooshOU on 2008-12-30
> **oilchangeguy said:**
> have you entered the bios, to see what boot options are available?

My only options in the BIOS is to enable network boot or boot via the internal hard drive.

---

### Post by shad0w_walker on 2008-12-30
How did you install Ubuntu in the first place?

---

### Post by SwooshOU on 2008-12-30
> **shad0w_walker said:**
> How did you install Ubuntu in the first place?

USB flash drive.

---

### Post by shad0w_walker on 2008-12-30
Surely with the netbook there would be instructions for using the recovery discs.

---

### Post by oilchangeguy on 2008-12-30
> **SwooshOU said:**
> My only options in the BIOS is to enable network boot or boot via the internal hard drive.

if the computer has no cd drive, why do you have a windows cd? did you delete the restore partition, when you installed ubuntu? and this begs the question. why are computers made with no cd drive? and why would you buy one?

---

### Post by shad0w_walker on 2008-12-30
> **oilchangeguy said:**
> if the computer has no cd drive, why do you have a windows cd? did you delete the restore partition, when you installed ubuntu? and this begs the question. why are computers made with no cd drive? and why would you buy one?

He said he has a netbook, you know, the ultrasmall, ultra portable things? There isn't enough space for a CD/DVD drive in them. It's a sacrifice based on the idea that all the needed software would be already installed or downloadable.

---

### Post by SwooshOU on 2008-12-30
> **shad0w_walker said:**
> Surely with the netbook there would be instructions for using the recovery discs.

There are instructions.

It says that I need an external CD drive in order to run the restore CD.

---

### Post by shad0w_walker on 2008-12-30
If it says that, it should also say how to get the system to boot from the external USB drive. What make and model is it?

---

### Post by SwooshOU on 2008-12-30
> **oilchangeguy said:**
> if the computer has no cd drive, why do you have a windows cd? did you delete the restore partition, when you installed ubuntu? and this begs the question. why are computers made with no cd drive? and why would you buy one?

Because the HP mini in question had XP installed on it.  They include a restore CD so that you can hook up an external CD drive if you ever wanted to install software via CD.

Ubuntu erased my computer when it installed.  It installed over XP.

As someone else mentioned, netbooks are tiny and one way to keep it that way is to remove CD drives.

I bought one because I like tiny computers.

---

### Post by SwooshOU on 2008-12-30
> **shad0w_walker said:**
> If it says that, it should also say how to get the system to boot from the external USB drive. What make and model is it?

It's an HP mini 1000.

It says I need to press F9 and then select the USB drive from the options given.  However, when I do that there is only one option: the internal hard drive.  I know the CD drive works, it's just not being recognized.

Ironically, the external cd drive is an HP as well.

---

### Post by shad0w_walker on 2008-12-30
Only really two things to do I guess. Either find a different external drive to try it with or contact HP and see if they have some magic fix.

---

### Post by boof1988 on 2008-12-30
What is the model number of your machine?

Here's a [link](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01613138&lc=en&dlc=en&cc=us&product=3842173&rule=6080&lang=en#N455) at HP for some mini.

Can you tell us exactly what the boot priority options are?  And then maybe we can help more.

---

### Post by Calmor on 2008-12-30
> **SwooshOU said:**
> Because the HP mini in question had XP installed on it.  They include a restore CD so that you can hook up an external CD drive if you ever wanted to install software via CD.

Ubuntu erased my computer when it installed.  It installed over XP.

As someone else mentioned, netbooks are tiny and one way to keep it that way is to remove CD drives.

I bought one because I like tiny computers.

This site says that it's just a matter of hitting F9 and choosing to boot from your USB CD/DVD drive...

[http://www.hp2133guide.com/how-to-install-windows-xp-on-the-hp-2133-mini-note/]("http://www.hp2133guide.com/how-to-install-windows-xp-on-the-hp-2133-mini-note/")

But you've already done that.  If you're using the restore disks, there should be no issue, but if you theoretically had a ripped copy of XP that wasn't bootable, that could cause a problem.

It could be a bad drive and/or mainboard issue too I imagine.  Have you tried other bootable CD-ROMs to determine if the disc itself could be the problem?  Is the CD-ROM connected before power-up and does it seek the disk or at least spin up before offering the boot menu (before/after pressing F9)?

You might also want to try searching for "Install Windows XP from USB" - if you have another computer with CD-ROM to borrow, this might fix your issues.

As for installing from within Ubuntu, it's not possible to run the SETUP.EXE program required to start Windows setup, unfortunately.

Sorry to hear you're having issues with Ubuntu.

---

### Post by SwooshOU on 2008-12-31
> **boof1988 said:**
> What is the model number of your machine?

Here's a [link](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01613138&lc=en&dlc=en&cc=us&product=3842173&rule=6080&lang=en#N455) at HP for some mini.

Can you tell us exactly what the boot priority options are?  And then maybe we can help more.

My hp mini model is 1030nr.

In BIOS setup when I hit f10, the only option is to enable net boot or boot from the internal drive.  No USB options or anything else.

I even disabled the internal hard drive, restarted with the USB drive attached and it still wouldn't recognize it.

Ubuntu wouldn't have messed with the BIOS such that it would disable the ability to startup via CD would it?

I called hp and they seem to think something is wrong with the computer because they insist the external drive I have should work with it.

SO, unless anyone else has any other ideas, I suppose I'll just let hp either replace it or send me my mini with XP installed.

Thanks for your help though!

---

### Post by Calmor on 2009-01-02
Since Ubuntu is just an OS installed on the hard drive, there's no way it could have affected the BIOS.  Unless you installed a BIOS update (usually administered via a boot-up software or via Windows software) I'm not sure why the BIOS won't pick up the external.

Have you tried other USB drives, just out of curiosity?

---

