---
title: "Installation Noob - Dual Boot"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Asreial on 2009-05-11
Hello everyone. :o  Asreial here. 

I have a question about installing Ubuntu. 

I have a brand new computer that currently has no operating system.
I would like to make it a dual boot system.
Should I install Windows XP first or should I install Ubuntu?
Does it really matter what I install first?

Thanks for your advice and opinions. :)

---

### Post by HeirPixel on 2009-05-11
Easiest is to install Windoze first and have the Ubuntu LiveCD use "free space" to install Linux. This way you won't have any issues with your Windows installation writing over GRUB and having to reinstall it.

---

### Post by Asreial on 2009-05-11
I will do this.  Thanks.

---

### Post by Dill on 2009-05-11
You'll want to install XP first. Basically, if you install Ubuntu and then XP afterwards, XP will overwrite what's called the Master Boot Record, which is a small section of the hard drive that contains information about the partitions (on which there may be different operating systems, etc.), and other such data. But if you install XP and then install Ubuntu, you'll want to install GRUB (Grand Unified Boot Loader), which you can configure to allow you to choose to boot from either XP or Ubuntu. But there's a preliminary step you'll want to do before installing either...

Partition your hard drive -- you'll have to have a separate partition for your XP and Ubuntu installations; you can either create two partitions and install XP on one, then Ubuntu on the other (you should have the choice of the partition on which you want to install both XP and Ubuntu as part of the installation process), or install XP and then "resize" the partition, then create a partition for Ubuntu. 

At any rate, there are plenty of good guides explaining this process online, like this one: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Good luck!

Cheers,
Dill

---

### Post by HeirPixel on 2009-05-11
Here's also a way to use your Windows MBR to boot both systems: [http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")

I really, really don't think it's a very useful/effective/productive/etc. solution, but I suppose it can't hurt to reference it anyhow.

---

