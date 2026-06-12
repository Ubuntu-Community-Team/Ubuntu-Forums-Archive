---
title: "Cant view contents of old Mac floppies"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-06-20
Please Help Me If You Can:

I am running a copy of Ubuntu 8.04 on an older PC
(the only machine I have with a working floppy drive)
I can read PC formatted flopies but not my Mac discs
I need to get some information off them to add to an iMac with 
OS 9 added.  If there are any suggestions out there I would 
appreciate the help.

Thanx Norm

Oh, BTW if helped I would like to log a thanks.  Some help with
that would also be appreciated.

---

### Post by LewRockwell on 2009-06-20
just some casual reading to start with: [http://www.tprthai.net/fslinux.htm](http://www.tprthai.net/fslinux.htm)

wonder what file system those floppies are using?

---

### Post by Norman Thom on 2009-06-20
Thanks Lew for the tip.

Unfortunately the frustrating part is I don't know howto install the program.

are there any other ideas or help with installation?

---

### Post by LewRockwell on 2009-06-20
Most of these links are to older information that may or may not be helpful at all. If it's a do-or-die that you recover the data from your disks I would advise you strongly to investigate your local Apple community(there may very well be someone close by that can do what you need safely and efficiently).

[http://www.linuxjournal.com/article/210](http://www.linuxjournal.com/article/210)

[http://www.macgeek.org/downloads/readme_pc_mac.txt](http://www.macgeek.org/downloads/readme_pc_mac.txt)


If you have access to Windows I think this might work with XP
[http://www.extractnow.com/](http://www.extractnow.com/)

---

### Post by Rubicon_82 on 2009-06-20
Hi,

The 'mount' command can cope with both HFS and HFS+ filesystems (the latter only in read-only mode unless journaling is disabled).  Mount can also guess the filesystem type, but this may lead to data loss if it guesses incorrectly.  To read your data, I suggest the following:

**A:** Make a disk image of your floppy with the dd command.
```

dd if=/dev/fd0 of=floppy.img

```
In the above command, dd will copy from the input file  /dev/fd0 (which is probably the floppy drive) to the output file floppy.img in the current directory.  If you don't have read access to fd0, you may need to run the above command as root (sudo).  Be warned that dd will do **exactly** what you tell it to without asking for confirmation first.  This may include overwriting your data if you mix up the 'if=' and 'of=' fields.  **Double check the command before you run it.** See man dd for more details.

**B:**  Mount the image as a loop device.
```

sudo mount floppy.img /mnt -o loop

```
The loop device allows you to mount a disk image as if it were a file system.  In this case, it will be mounted in the /mnt directory.  If you don't specify the filesystem (with the -t flag), mount will try to guess.  If it doesn't work, you can post any error messages here.

---

### Post by LewRockwell on 2009-06-21
I just found this also:

[http://ubuntuforums.org/showthread.php?t=239370](http://ubuntuforums.org/showthread.php?t=239370)

we'll have this figured out one way or another!

---

