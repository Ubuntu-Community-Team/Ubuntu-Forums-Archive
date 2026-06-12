---
title: "[SOLVED] Windows xp won't boot anymore after installing Ubuntu"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by bielcoral on 2008-12-23
Hi all,

today I have installed ubuntu 8.10 in a pen drive. After doing this I cannot boot anymore the windows xp installed in the hard drive of my computer, unless my usb stick is plugged in.

I think my computer is trying to boot all the time from my usb pen drive, although I have set as first priority in my bios that it should boot from a hard drive.

I have no idea how I can solve this, so please help me!

---

### Post by oilchangeguy on 2008-12-23
> **bielcoral said:**
> Hi all,

today I have installed ubuntu 8.10 in a pen drive. After doing this I cannot boot anymore the windows xp installed in the hard drive of my computer, unless I my usb stick is plugged in.

I think my computer is trying to boot all the time from my usb pen drive, although I have set as first priority in my bios that it should boot from a hard drive.

I have no idea how I can solve this, so please help me!

ubuntu's bootloader (grub) has overwritten windows bootloader. and since ubuntu is on the pen drive, when you remove it, windows won't boot. you'll probably need to install grub on the internal hard drive.

---

### Post by bielcoral on 2008-12-23
hi thanks for the reply the reply, but how do I do this since in my internal drive there is only windows?

---

### Post by wilson47 on 2008-12-23
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

The second post gives pretty good directions. There are also lots of tutorials on how to do this if you look around. Sorry I can't be of more help.

---

### Post by Duck2006 on 2008-12-23
Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by LtPitt on 2008-12-23
Maybe you don't know and don't want to understand much about it and just want to recover your data easily :)

Then you can use [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Super grub =)

---

### Post by teh_yodeler on 2008-12-23
[http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

GAG has helped me in the past with similar circumstances.  Download it (from the link above), burn the ISO, boot with it in the drive and use it to reclaim your computer!!

---

### Post by halitech on 2008-12-23
you just need to restore your windows boot loader. you can do that from your windows CD. Just boot from the windows install cd and go into recovery mode (by pressing R) and at the prompt type
```
fixmbr
```

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

---

### Post by bielcoral on 2008-12-24
Hi thanks all of you for your help in the end I solved it using this:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

so if anyone has a similar issue I think this is the best solution

---

