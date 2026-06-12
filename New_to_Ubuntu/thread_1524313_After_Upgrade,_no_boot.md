---
title: "After Upgrade, no boot"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by zaivala on 2010-07-05
On Wednesday or Thursday, I did an upgrade, which included a new Linux kernel.  As expected, I had to reboot after this.

Upon rebooting, the screen is mostly black, with about 1/6 of the screen in the upper left corner looking like a tiny version of Terminal -- although it is non-functional -- and nothing else happens.

Anyone have any ideas?

Update:  This time, the Terminal was active, kinda, and I typed Exit.  It then brought up my picture to choose user, asked for my password (this is supposed to be on Automatic), and then gave me the usual desktop background, no launchbar -- and still having the mini-Terminal in the upper left.  Also, still no way to run programs except from Terminal, and I'm not good at that.

---

### Post by Oldieone56 on 2010-07-05
I've had a similar problem after installing 10.04 from the CD. Ubuntu 9.04 installed and booted without issue. 10.04 gets stuck in a boot attempt loop. All I can do is power down. I'm in the process of trying various 'fixes' found in the forums. Being new to Linux/Ubuntu it is a challenge.

---

### Post by hdtvman on 2010-07-05
I just had this happen to me.  I have a Windows Vista machine and I wanted to install 10.04 on a new disk, not on the same Vista boot disk.  I'll use the bios boot options to select the boot OS.

Any way, after installing 10.04, I got the blank screen described above.  I did a re-install on the new disk and this time I went to the advanced section of the disk install options and set the boot to appear new disk and everything worked this time.

So maybe that needs to be done in your case also.  On the other hand it could be totally unrelated.

hdtvman

---

### Post by philinux on 2010-07-05
> **zaivala said:**
> On Wednesday or Thursday, I did an upgrade, which included a new Linux kernel.  As expected, I had to reboot after this.

Upon rebooting, the screen is mostly black, with about 1/6 of the screen in the upper left corner looking like a tiny version of Terminal -- although it is non-functional -- and nothing else happens.

Anyone have any ideas?

Update:  This time, the Terminal was active, kinda, and I typed Exit.  It then brought up my picture to choose user, asked for my password (this is supposed to be on Automatic), and then gave me the usual desktop background, no launchbar -- and still having the mini-Terminal in the upper left.  Also, still no way to run programs except from Terminal, and I'm not good at that.

Try booting with the previous kernel.

---

### Post by zaivala on 2010-07-05
Well, this is not a dual boot machine.  Also, I have been running 10.04 since a day or two after release with (almost) no problem ("almost" means it keeps asking for my keyring login, which is supposed to be automatic).  So this is new with the latest upgrade.

Not sure I have half a clue about how to boot from an earlier kernel, but that would likely work if I did know.

I'm one of those n00bs who has been running Ubuntu for a long time (since Hardy Heron) (and some other Linuxes going back more years, but Ubuntu has been my best experience), sometimes without a hitch and sometimes with one, but still doesn't really know "how to use Linux" other than the way Windoze users use Windoze.

---

### Post by zaivala on 2010-07-05
Also, if I'm going to fix the problem by reinstalling, it would be gravy to know how to do that without wiping the disk.  Yeah, I can restore it from various sources, but that does make installation more tedious.

---

### Post by zaivala on 2010-07-05
Not wanting to mess things up worse, in case they can be fixed, I'm booting off my live CD of 9.10.  If all else fails, I can reinstall that and then do the updates and upgrades and hope for the best.  I also have a Windoze machine, which I use for most things... that should end once I get the money together to get Crossover so I can run MS Office on my Ubuntu machine.

---

### Post by zaivala on 2010-07-16
Thanks for all the lack of help.  I went ahead and reinstalled.  This is the first time I've not been given any help, other than support from others with the problem.  Bad Ubunters, no beans for you.

---

