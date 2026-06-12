---
title: "floppy formatting error"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by dspisak on 2009-01-04
Hello.  I've tried to use "Floppy Formatter" to format a 1.44 MB disk.  The floppy drive can be mounted and the files on the disk can be read.  The permissions for /dev/fd0u1440 are set to +rwx.  Floppy Formatter keeps returning "Error formatting track #0".  This happens with any 1.44 disk I insert.  The disks are not write protected.  Any ideas?  TIA.

Dan

---

### Post by dspisak on 2009-01-07
Does anyone have any ideas how to solve this problem?

Dan

---

### Post by plucky on 2009-01-07
Open a terminal window and try ```
mkfs.msdos /dev/fd0
``` and see what errors that produces.Or use **mkfs.vfat /dev/fd0** 

Then mount the drive with ```
mount /dev/fd0
``` and the floppy icon should appear on your desktop.

If there is a problem please post output of ```
ls -l /dev/fd0
```

Good Luck

---

### Post by decoherence on 2009-01-07
I consider myself fortunate in that I have not had to deal with floppies in a while.

```

man mbadblocks
```

seems a reasonable first step.

>        mbadblocks - tests a floppy disk, and marks the bad blocks in the FAT (file allocation table)

could be you've got a bunch of bunk floppies. i've been through that a few times.

barring that, I'd check launchpad or the linux kernel mailing list for bugs on writing to a floppy. perhaps you trawl through the output of

```
sudo lshw
```

to find more useful information to use in your search. (can someone with a floppy drive give dspisak a more specific usage of lshw?) Might as well post the output here, too; in case somebody knows... i really have no idea, though. see first sentence ;)

i really, really, *really* hate floppies. if i need therapy now, you're getting the bill! :lolflag:

floppy disk == run away!!!!

---

### Post by linux_tech on 2009-01-07
You may also give
```
fdformat /dev/fd0H1440
```
a try or ```
mformat
```

---

### Post by dspisak on 2009-01-08
EDIT:
Well I attempted to make a rescue floppy in GRUBEditor.  It started to format the floppy but returned the error message "Error - KDE Control module, The floppy formatting process failed".  Any ideas?  TIA.

EDIT:
Ah ha, problem solved.  The floppy must be unmounted before applying *fdformat /dev/fd0u1440*.  Too bad Format does not appear when the icon is right-clicked.

OK, folks.  Here is what I get.

spisaks@djs-pc:~$ fdformat /dev/fd0u1440
/dev/fd0u1440: Device or resource busy

and

spisaks@djs-pc:~$ mkfs.msdos /dev/fd0
mkfs.msdos 2.11 (12 Mar 2005)
mkfs.msdos: /dev/fd0 contains a mounted file system.

or

spisaks@djs-pc:~$ mkfs.vfat /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: /dev/fd0 contains a mounted file system.

also

spisaks@djs-pc:~$ ls -l /dev/fd0
brwxrwxrwx 1 root floppy 2, 0 2009-01-08 17:47 /dev/fd0

and

spisaks@djs-pc:~$ mbadblocks -V fd0
Mbadblocks version 3.9.11, dated May 31st, 2007
configured with the following options: enable-xdf disable-vold disable-new-vold disable-debug enable-raw-term 

I can mount the floppy and Places/Computer can read the files.  The "1.5MB Media" icon appears on the desktop. I thought that When the icon was right-clicked the menu that appears would contain the Format option, but the option does not appear.

I also agree about using floppies.  However, the program KGRUBEditor allows one to make a Rescue Floppy - which looks to be a good thing.  Being new to Linux I do not know of any other means of rescue.  TIA.

---

### Post by Lingonet on 2009-07-07
This solved a part of my problem, it's just, I get this error now:

```
Read error: Problem reading cylinder 0, expected 18432, read -1
```

Can someone help me?

Thank you!

-Lingot

---

### Post by wpshooter on 2009-07-07
Have you tried cleaning the heads on your floppy drive ?

---

