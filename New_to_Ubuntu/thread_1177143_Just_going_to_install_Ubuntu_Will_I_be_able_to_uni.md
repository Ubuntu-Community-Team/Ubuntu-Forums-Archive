---
title: "Just going to install Ubuntu: Will I be able to unistall it safely ?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by hammadmunawar on 2009-06-03
Hello,

(Absolute beginner in Ubuntu)

I am running Windows XP and planning to install Ubuntu in dual boot. I have heard that uninstalling can be a problem.

Please advise

---

### Post by Sef on 2009-06-03
No.  You just reformat the Ubuntu partition, and reinstall the XP Bootloader.

---

### Post by cak3 on 2009-06-03
If you wan't to remove ubuntu, It should't be to difficult. If you have it set up with grub (the normal, booted from CD install) then uninstalling would mostly involce deleting the partition that is was on and resizing the windows one to fill the space (this can be done in gparted, which is on the ubuntu install cd's). You would then want to rewrite the windows bootloader to the mbr (master boot record) of the hard drive. You can do that with any windows xp cd (you just need to be able to get into the recovery console and then use the "fixmbr" command).

You can also install ubuntu in windows via wubi (where you put the disk in while booted into windows and follow that process) which will install it on the windows partition in the windows bootloader. I have never used that myself, but, assuming there is not a specific uninstall process, you shuld be able to remove it just by deleting the ubuntu directorie(s) and maybe remving its entry from the windows boot.ini (a hidden file loacted on the top level of the C drive usually).

A bit of forum digging also yeilded this [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

it offers a much simpler solution that what I have just described, though I have never used it and so can't really say anything to how well it works.

---

### Post by hammadmunawar on 2009-06-03
@cak3!

thanks! this info will  be useful when i need it (i do sincerely hope i would never need to uninstall Ubuntu)

---

### Post by cak3 on 2009-06-03
> **hammadmunawar said:**
> thanks for the reply!

how can i reinstall the XP bootloader ?

see my post =P

---

### Post by mc4100 on 2009-06-03
[Another solution]("http://wubi-installer.org/")

---

### Post by hammadmunawar on 2009-06-03
thanks to every body !

your help will make my Ubuntu experience more pleasant !

---

### Post by hammadmunawar on 2009-06-03
I have decided to use Ubuntu with Wubi at first ... it is good for trying out Ubuntu ... and has no uninstallation problems ...

---

### Post by lisati on 2009-06-03
> **hammadmunawar said:**
> I have decided to use Ubuntu with Wubi at first ... it is good for trying out Ubuntu ... and has no uninstallation problems ...

Welcome to the family. Feel free to continue asking questions and sharing your thoughts.

---

### Post by mc4100 on 2009-06-03
> **hammadmunawar said:**
> I have decided to use Ubuntu with Wubi at first ... it is good for trying out Ubuntu ... and has no uninstallation problems ...
It's ideal for trying Ubuntu, but be sure to read the [FAQ]("http://wubi-installer.org/faq.php") (A few catches):
> 
Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

---

### Post by hammadmunawar on 2009-06-03
yes ... i read about this in the Ubuntu handbook ... 

I am buying a new hard disk ... and will soon be switching to full time Ubuntu ...

---

### Post by nandemonai on 2009-06-03
Just realise that Wubi is not as quick as a real install and has some odd quirks here and there. Don't base your judgment on a wubi install alone. I only suggest it as an extended test, not unlike the live CD. ;)

---

### Post by hammadmunawar on 2009-06-03
@nandemonai !

i will keep this in mind ...

---

