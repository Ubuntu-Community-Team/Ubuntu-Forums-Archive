---
title: "Grub Recovery"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by T2manner on 2009-11-13
I had a quad boot setup yesterday.  1. Vista Recovery. 2. Vista. 3 Ubuntu. 4. Windows 7 RC.  I had some unallocated space in there too. Last night, using Windows Vista Disk Manager, I deleted Windows 7 and expanded the Vista Partition.  I just turned on my computer and now I can't even get to the grub menu list.  All i see is Grubrecovery> and some other error message. Please help.

---

### Post by ranch hand on 2009-11-13
Check this thread, it may help.

[http://ubuntuforums.org/showthread.php?t=1325788](http://ubuntuforums.org/showthread.php?t=1325788)

Try to stop and think before you do these things.  Any boot loader has to identify the partitions.  If you set it up and then change the partitions, your boot loader is in trouble.

---

### Post by kansasnoob on 2009-11-13
> **T2manner said:**
> I had a quad boot setup yesterday.  1. Vista Recovery. 2. Vista. 3 Ubuntu. 4. Windows 7 RC.  I had some unallocated space in there too. Last night, using Windows Vista Disk Manager, I deleted Windows 7 and expanded the Vista Partition.  I just turned on my computer and now I can't even get to the grub menu list.  All i see is Grubrecovery> and some other error message. Please help.

Do you know what version of grub you had?

Was this Jaunty or Karmic?

If it's legacy grub you do this:

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

If it's grub2 you do this:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by kansasnoob on 2009-11-13
> **ranch hand said:**
> Check this thread, it may help.

[http://ubuntuforums.org/showthread.php?t=1325788](http://ubuntuforums.org/showthread.php?t=1325788)

Try to stop and think before you do these things.  Any boot loader has to identify the partitions.  If you set it up and then change the partitions, your boot loader is in trouble.

+1! If you're just not sure run that Boot Info Script. That will tell us all we need to know.

---

### Post by T2manner on 2009-11-13
it's Grub 2 I believe.  i have the newest Ubuntu installed.

---

### Post by kansasnoob on 2009-11-13
> **T2manner said:**
> it's Grub 2 I believe.  i have the newest Ubuntu installed.

Then you do this:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by T2manner on 2009-11-13
Yay. Reinstalling Grub worked! Thanks!
For future reference:  when i mess with my partitions, will i have to always reinstall Grub?

---

### Post by ranch hand on 2009-11-14
This is why it is  a good idea to have a plan, on paper, of how you are going to partition your drive before you install the first OS.

Yes, every time you pull the rug out from under your boot loader it will need fixed.

---

### Post by WitchCraft on 2009-11-14
> **T2manner said:**
> Yay. Reinstalling Grub worked! Thanks!
For future reference:  when i mess with my partitions, will i have to always reinstall Grub?

Only if you modify the master boot record.

---

