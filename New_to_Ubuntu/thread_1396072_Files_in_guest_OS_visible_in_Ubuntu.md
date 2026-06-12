---
title: "Files in guest OS visible in Ubuntu?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by OllieGab on 2010-02-01
I use Ubuntu 9.10 but have installed a guest OS in my VirtualBox.
Are files saved in the quest OS visible from Ubuntu? Ie, if I save file X on the desktop when using the guest OS can I search for it in Ubuntu, for instance by using 'Search for files...'
After all the whole guest OS resides in file in Ubuntu...or?

Cheers

---

### Post by nhasian on 2010-02-01
no you cannot search for files as you described because all the files in the guest OS reside inside a virtual hard disk image.  You can however share the files through samba, ftp, etc.

---

### Post by jflaker on 2010-02-01
You can set shared folders then map/mount that share and save your data there from your guest OS....otherwise, the .vdi (virtual disk) is just a file to Ubuntu.  

A quick google search turns up a few utilities that CLAIM to mount .vdi disks, but it seems that a dynamically expanding disk can not be mounted unless you know the offsets of the blocks, which will change each time you use the guest system....a fixed vdi seems to be able to be mounted but I have not and will not test on my current vdi disks for fear of destroying the integrity of the disks.

Otherwise, bump or allow for more answers

---

### Post by bodhi.zazen on 2010-02-01
> **nhasian said:**
> no you cannot search for files as you described because all the files in the guest OS reside inside a virtual hard disk image.  You can however share the files through samba, ftp, etc.

I advise you use samba as well.

If you prefer VirtualBox offers what they term "Shared Folders"

[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

---

### Post by MoebusNet on 2010-02-01
If you are using the VirtualBox PUEL version, you can install Guest Additions and share files and folders between the host OS and the guest OS. The VirtualBox "Help" file will tell you how.

---

