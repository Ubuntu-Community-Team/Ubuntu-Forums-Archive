---
title: "make another partition - whats the best way?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Falc7 on 2008-12-10
On my laptop atm i have only ubuntu. I want to make another partition and dual boot XP, how would i go about making another partition? I tried through the system -> administration-> partition editor, but the option to resize the ubuntu partition is greyed out. Presumably because it is amounted

---

### Post by bobnutfield on 2008-12-10
It's greyed out because you cannot resize a partition that is mounted, which it obviously is since you are running from it. You can do it with the Live CD using the partition editor.  Keep in mind that when you install XP to a second partition it is going to wipe out grub with its own boot loader and you will have to re-install grub.

---

### Post by Falc7 on 2008-12-10
ok thanks, i'll give it a go with the Live CD now.
Thanks for the tip about re-writing grub, lucky i've got my copy of super grub handy :)

---

### Post by Coreigh on 2008-12-10
The easiest way is to backup anything you want to save, and wipe the disk and start over.

Boot the liveCD, use partition editor to make 4 partitions, (3 if you don't want to share files between Ubuntu and Windows)

Install Windows FIRST, Ubuntu and Grub will handle dual booting and saving the Windows boot information.

Lets say you have a 40GB hard drive. I would partition it this way;
1) First partition 8GB for Windows
2) Second, 10GB for Ubuntu
3) Third 20GB for user files. You can point My Documents to it from WIndows and ~./Home to it from Ubuntu (or better yet link to it from a folder in you ~./Home folder)
4) Remaining space for a /swap partition. Ubuntu doesn't need much but it will work better if you have it.

---

### Post by kansasnoob on 2008-12-10
> **Falc7 said:**
> On my laptop atm i have only ubuntu. I want to make another partition and dual boot XP, how would i go about making another partition? I tried through the system -> administration-> partition editor, but the option to resize the ubuntu partition is greyed out. Presumably because it is amounted

So you have Ubuntu and now want to install XP?

Look here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

