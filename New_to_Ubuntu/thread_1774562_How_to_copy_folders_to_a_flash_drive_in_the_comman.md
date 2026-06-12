---
title: "How to copy folders to a flash drive in the command line"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by perlgoodies on 2011-06-03
Sorry for bugging everyone AGAIN, still getting used to this Ubuntu thing and still can't load into my box because there's too much stuff on the HD.
 
I can't sign in but I can do that thing where you do CTRL+ALT+F2 and login that way to see the files.
 
Question: From the menu I'm at (the black DOS-like terminal prompt) is there a way to plug in a flash drive and do a ninja command like COPY FOLDER TO USB DRIVE?  I know I'm a dreamer but I hope there is such a way that I can copy stuff to a flash drive in this menu so I don't have to blindly delete stuff I don't what it is yet.

---

### Post by mikewhatever on 2011-06-03
Of cause you can, but you need to know some bash commands. Wouldn't be easier to use a Live CD/USB?

---

### Post by diablo75 on 2011-06-03
After you've attached the drive, type this command into a terminal:

```
sudo fdisk -l
```

This lists mountable partitions.  Your output will look like this:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9697acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13944   112005148+   7  HPFS/NTFS
/dev/sda2           13945      121601   864754822    5  Extended
/dev/sda3           22455      120951   791177152+  83  Linux
/dev/sda5           13945       22454    68356543+  83  Linux
/dev/sda6          120952      121601     5221093+  82  Linux swap / Solaris

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4aafc753

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

```

In the above example, I have two drives.  The first is my internal hard drive, which houses Windows and Linux partitions, and the second drive (/dev/sdb1) is an 400 GB external hard drive with an NTFS partition on it.  You can pretend this is your flash drive.  Just look at the output you get and you should be able to tell which is your flash based on the size declared in the drives first line.  Above it says "Disk /dev/sdb: 400.1 GB" about my external.

Now you'll want to mount this drive, after you've determined which /dev/sdXx ID your partition is under.  First create a directory to mount your flash into:

```
sudo mkdir /media/flash
```

Then mount your flash into that folder:

```
sudo mount /dev/sdb1 /media/flash
```

In the above example, change the "sdb1" to whatever partition corresponds with your flash.  Note that the "sdb" and the "1" mean "Device sdb, partition 1".  You'll have to type it has it's printed in the fdisk output above.

Once the drive is mounted, you can browse it by going to /media/flash.  You can do this by typing

```
cd /media/flash
```

Repeat this same procedure to mount any other partitions on the system you might not have access to yet, such as an internal windows partition if you have one.

Now to copy folders from one drive to your flash drive, you might type something like:

```
sudo cp -r /home/yourusername/* /media/flash
```

Another way of typing this exact same command is:

```
sudo cp -r /~ /media/flash
```

"/~" is a shortcut for YOUR home folder.

Otherwise the syntax is:

cp (options) /source/folder/* /destination/

You can read more about the copy command here:

[http://ss64.com/bash/cp.html](http://ss64.com/bash/cp.html)

Good luck!

---

### Post by Wim Sturkenboom on 2011-06-03
Some comments on post #3

First of all, the external drive will probably be mounted already, so no need to mount. You can check by examining the directories in /media using the *ls* command.
And you need to unmount when you're done (e.g. sudo umount /media/flash).

---

