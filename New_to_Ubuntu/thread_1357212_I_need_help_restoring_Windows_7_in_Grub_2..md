---
title: "I need help restoring Windows 7 in Grub 2."
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Mashuteichou on 2009-12-17
Okay, started by loading Ubuntu.  Then loaded Windows 7 on another partition.  Tried the Grub loader fix, now Windows 7 is gone, but the Windows XP that isn't installed has taken the place on the Boot Loader screen, but nothing happens when I try to load it.  Just random errors.

So, Ubuntu was deleted by Windows 7.  (Grub 2)
After fixing Grub, Windows 7 was changed to XP and now has errors.  

Multiple tutorials say to edit the grub by typing : sudo gedit /boot/grub/menu.lst

The only issue is, it is a blank page.  Nothing in it to change.  

How do I fix this?

---

### Post by bhaverkamp on 2009-12-17
Yes, those are grub 1 directions. Grub 2 pretty much seems to be a waste of time. I even had Windows 7 wipe out my boot loader during updates. Run Windows 7 in a VM. Friends don't let friends run windows.

---

### Post by kansasnoob on 2009-12-17
Please post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

We'll get it sorted out.

---

### Post by Mashuteichou on 2009-12-17
Indeed.  Windows is a waste of time.  But, I use it for work related things.  Plus half the games I play run on Windows and not Linux yet.  Like FF7 for example.  xD   Old school for the win.

But, I will continue playing around with it.  Maybe I can get an emulator to work correctly with WINE and run FF7 through that.  We shall investigate it a little more, and maybe not even need 7.

---

### Post by kansasnoob on 2009-12-17
There's nothing wrong with keeping Win in a multi-boot or virtual machine.

I still have my Win XP just in case.

Now, let's see that Boot Info Script .text!

---

