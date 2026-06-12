---
title: "Cannot mount USB Flash Drive"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-15
Hi all and thanks in advance!
I have a fresh install of Ubuntu9 Jaunty 64bit, for first time I tried to read on a USB Flash Drive but I get (sorry for translation...)the following bad traslated message:

> Son process execution "gnome-mount" didnt work (No file nor directory found)

I tried with another USB to see if it could be its fault but failed too. It's Ubuntu's fault.

Any clue?

---

### Post by mikeyphi on 2009-09-15
What format?
Could be it won't mount because it's Fat16.
You can check the file system using partition editor.

---

### Post by webwiller on 2009-09-15
They're fat32

---

### Post by bigboy_pdb on 2009-09-15
You might want to try using the command line to do it.

You can use the following to list hard drive partitions that have been detected: 'sudo fdisk -l'.

One of them should be your flash drive. Then use 'sudo mount /dev/XXX /mnt' to mount it to the '/mnt' folder (where /dev/XXX is the device affiliated with your flash drive).

If this succeeds then it might be a problem with the program that auto mounts the drive.

Also, I just tested this with my flash drive which has a FAT16 partition and it worked so it doesn't seem like FAT16 partitions should be problematic.

---

### Post by bigboy_pdb on 2009-09-15
You might want to look at this [bug]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/102097").

You can also try 'gnome-mount -d /dev/XXX' from the command line to see if any other errors come up.

---

### Post by webwiller on 2009-09-15
I did NOT have the program "gnome mount" installed, ty I found out! When installed it obviously mounted my drive straight away!

Why is that? I never had these troubles with 32bit...is 64bit not "as complete as..."?

Should I expect many differencies (=assollllsss)??!!

:confused:

---

### Post by bigboy_pdb on 2009-09-15
That shouldn't have happened. It doesn't make sense for the installation to leave that package uninstalled.

You might want to file a bug report on [launchpad]("https://bugs.launchpad.net/"). You might also want to check on the live CD if the package is installed and reads USB flash drives (and mention the result on launchpad if you file a bug).

---

