---
title: "Installing CD/DVD media to non DVD Machine"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-27
Hi Forum,

I'm playing around with a new laptop from work. The current system is WinXP, the hardware is Intel Atom 280. I'm thinking about putting Ubuntu on the system but I need to retain Windows for some in-house software.

The system HDD is probably too small for a dual boot and I don't feel like carrying an external drive so I'm toying with Virtual Box. Not sure whether the system is powerful enough for that with the virtualisation overhead.

The problem is that the system doesn't have a CD drive. I can create a recovery ISO from the system under Windows. I also have an old set of XP installation CDs knocking around (fully paid up licence).

How do I get the XP software into Virtualbox on a machine without CD ROM.

From a forum search I found the command

  dd if=/dev/dvd of=XP.iso

The problem is that, if this doesn't work I'm stuck with a non-working system. Therefore I can't just try it....


Any help appreciated


Richard

---

### Post by MelDJ on 2009-10-27
download this drive emulator: [http://www.daemon-tools.cc/eng/downloads](http://www.daemon-tools.cc/eng/downloads)
then mount the ubuntu .iso and you can install it on the system. i recommend wubi in this case

---

### Post by WolfRage on 2009-10-27
Just wanted to mention my favorite option. First if you have a flash at least as large as the iso with about an extra 100mb you can format it with xp then use unetbootin to install the iso on the flash drive, then you can use the wubi from the flash drive or boot straight off the flash drive to give Ubuntu a test run with out installing anything... and if satisfied you can then use that to install Ubuntu from the boot flash.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by John Bean on 2009-10-27
> **WolfRage said:**
> use unetbootin to install the iso on the flash drive
[]("http://unetbootin.sourceforge.net/")
+1

This is my preferred method with CDless machines like netbooks. Reliable and effective.

---

### Post by RichardCL on 2009-11-16
Thanks for the tips. I tried the USB key install (Ubuntu version from the system menu). It only allows for 4MB of persistence, which is a pity since I'm using a 75GB HDD. Therefore I installed to the USB. It works fine although a little slow.

Since Ubuntu is my favored OS, I'd rather use windows from the external drive and have Ubuntu as the primary OS. That doesn't seem possible though.

---

