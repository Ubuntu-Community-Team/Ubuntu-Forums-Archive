---
title: "Ubuntu Windows installer gone apocatlyptically Haywire"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by USR612 on 2011-03-21
Hi guys, 
After much success using Ubuntu, I decided to use the window installer fo the latest distro on my new laptop.  Unfortunately, after a few months of use, it updated and now won't even get to GRUB when I select ubuntu from the window bootloader.  Several other people seem to have this problem and attribute it to the windows installer.  I'd like to uninstall and reinstall with a proper partitioning job, but am not quite sure of a few details.
1) Is it really as simple as going to the Windows control panel, selectung Ubuntu and clicking uninstall? or is this likely to cause problems
2)  I need to back up my files on Ubuntu, Is there any way of doing this?
Thanks!

---

### Post by andrewthomas on 2011-03-21
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-03-22
> **USR612 said:**
> Hi guys, 
After much success using Ubuntu, I decided to use the window installer fo the latest distro on my new laptop.  Unfortunately, after a few months of use, it updated and now won't even get to GRUB when I select ubuntu from the window bootloader.  Several other people seem to have this problem and attribute it to the windows installer.  I'd like to uninstall and reinstall with a proper partitioning job, but am not quite sure of a few details.
1) Is it really as simple as going to the Windows control panel, selectung Ubuntu and clicking uninstall? or is this likely to cause problems
2)  I need to back up my files on Ubuntu, Is there any way of doing this?
Thanks!
Uninstalling really is that simple. It will delete everything - so only do it when you're sure.

The second link AndrewThomas showed shows how to fix your problem (Problem #2 Solution #1). 

If you just want to recover data, it also links to a tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) that can give you readonly access to the virtual disk (\ubuntu\disks\root.disk) from windows.

If you've spent a lot of time customizing Wubi it's also possible to [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") it to a regular install (but this requires that you create the partitions first - whereas if you use the Ubuntu installer it can do partitioning automatically).

If in doubt, backup the root.disk outside of the \ubuntu directory before uninstalling wubi. Then you can access it later from a live CD or another Ubuntu install.

---

