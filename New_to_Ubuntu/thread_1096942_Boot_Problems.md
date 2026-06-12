---
title: "Boot Problems"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by atngplusultra on 2009-03-15
I feel slightly dumb, but not completely
I have Ubuntu on one partition, and XP on another.
I just now re-installed the XP, but of course, left the Ubuntu partition intact.
Now, at first, I thought that the dunderheaded XP had uninstalled my Ubuntu completely, but this is probably not the case; or at least, I hope it's not, because when I view the amount of hard drive space on Windows, the total is equal to what the newly-formatted XP partition was supposed to be.
Thus, I am assuming that the Ubuntu is still viable, and I want to get back to it, but installing XP has messed up GRUB; I've tried installing and running GRUB, and looking through the commands, but I can't decipher what exactly I should do to get back to my Ubuntu kernel.
any ideas?

---

### Post by blueridgedog on 2009-03-15
It looks like XP just removed grub from the master boot record of the first hard drive.  

This thread covers how to re-install it.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by atngplusultra on 2009-03-15
awesome.
i figured a live cd could help

---

