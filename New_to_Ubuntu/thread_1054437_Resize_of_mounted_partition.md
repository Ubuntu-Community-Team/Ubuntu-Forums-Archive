---
title: "Resize of mounted partition"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by oyroy on 2009-01-29
Ive been browsing around for a while now, searching for a thread that could help me, but havent found much, so either Im even n00bier at searching then I thought, or Im missing something thats totally elemenary (probably both ;)).

Ive just set up my Ubuntuserver, and finding the CLI-only interface interesting. Ive had some experience using terminal from earlier use, but also often had a GUI to rely on. Last time I did this was on OpenSUSE 10.3 where some YAST-function did it for me, but I dont wanna go back to that place again (hate the package-managing, long live apt-get).

So, typical half-cheap Linux server. Asus MB, Intel C2D, 2GB of RAM, Areca ARC-1220 S-ATA-Raid-controller and so on.
I did the install on 4x1TB Samsung F1 disks in Raid5, but found out when I added up all my JBODs I would be out of space before all my backup would be done, so I bought another two 1TB-disks and expanded the raid and volume, no problems there. Now, I have to grow my ext3 to use the new space.

```
oyroy@igor:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             19222656   1156852  17089244   7% /
tmpfs                  1028356         0   1028356   0% /lib/init/rw
varrun                 1028356       684   1027672   1% /var/run
varlock                1028356         0   1028356   0% /var/lock
udev                   1028356      2792   1025564   1% /dev
tmpfs                  1028356         0   1028356   0% /dev/shm
/dev/sda3            2862375700 1975883892 741091432  73% /home
``` and ```
oyroy@igor:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 4999.9 GB, 4999999651840 bytes
255 heads, 63 sectors/track, 607881 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      267350  2147483647+  ee  GPT
/dev/sda2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d45af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

``` /dev/sdb is just a JBOD that Im done with, but havent disconnected yet.

So, my question is (finally), how do I grow my /dev/sda3 to include the remaining 2TB? I would prefer to do this while still running, so I can do online-expanding later on when adding more disks. 

Starting up parted:
```
oyroy@igor:~$ sudo parted
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) check
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that
another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and
removing the old backup)?
Fix/Cancel?

```is it just to go forward from here? Then I read somewhere that parted cant work on a mounted partition, which means I have to shutdown my server and do it from a LiveCD. I can do that, but it should be a way to do this without having to reboot, I just need some help as to how.

Anyone got a suggesion for this n00b? :D

---

### Post by avtolle on 2009-01-29
Have you attempted to unmount the partition in question?

---

### Post by greyfox1 on 2009-01-29
I believe you will always have to unmount a partition before you can edit it like you want to do here.  However this doesn't always mean you have to use a Live CD (this is only if you need to resize the partition where your OS lives).  Since you want to resize the partition mounted at /home, I believe you can do it fairly easily.

What you could do is use gparted (gksudo gparted or Applications->Administration->Partition editor if you have it installed; sudo apt-get install gparted to install it). Gparted will allow you to edit partitions via a GUI which would likely be easier for you.

You'd have to unmount the partition before editing it, which I believe you can do through gnome or via command line (sorry I'm at work on a Windows machine so I can't verify what commands you may need) then start gparted.  Gparted makes it fairly easy to edit  your partitions.  Hope this helps!!

---

### Post by oyroy on 2009-01-29
Well, Im running Ubuntuserver 8.10, and it has no GUI as far as I can tell ;) (nothing in Ctrl+Alt+F7), so seems using gparted might be a problem, and that Im stuck with parted (the CLI-version).

---

### Post by greyfox1 on 2009-01-29
Oh, my mistake.  I skimmed over the part where you said that :P

Well the procedure will be a bit different, but I believe you'll still be able to do what I recommend (unmount the partition, edit it, remount it without rebooting).  Good luck!

---

### Post by oyroy on 2009-01-29
So, just do the regular «sudo umount /dev/sda3» command and use parted? With the Fix it asks for in parted, should I just do that, or what is that really? I it just an error that arrives as I grew the Raid?```
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) check
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that
another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and
removing the old backup)?
Fix/Cancel? Cancel

```

---

### Post by oyroy on 2009-01-29
```
umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
oyroy@igor:~$

```

What will be neccesary to unmount /home? Doesnt most of what I do go there? Would it be a better choise to have my storage on something else then /home, so I just have home on a small partition with / and keep a total different system for all my stuff?

I also read something about *resize2fs* beeing able to expand a system already mounted. Anyone have any experience with it?

---

### Post by bumanie on 2009-01-29
You would be better off booting you computer via a live cd; either ubuntu or the dedicated gparted live cd ( I personally prefer the latter) and then you will have less issues as no partitions will be mounted. If you use ubuntu live cd, once open to the desktop, open terminal and type > sudo apt-get install gpartedYou will find gparted under System --> Administration --> Partition editor. Open the partition editor and you should be able to do what you want with the partitions. To get gparted live cd go [here]("http://gparted.sourceforge.net/download.php").

---

### Post by oyroy on 2009-01-29
Ahh, so Im ending up with having to reboot the system. I knew about that option, and Ive used it before. I was just hoping there was a way to do it on-line. Doesnt matter that much right now, but later, if I get Apache and MySQL and such up and running, it would have been great to do such stuff without having to turn off the system.

Well, once I get my 600GB of lossless music over from my External HD its fixing time. After that its sorting through my directories and clean up my dSLR-Raws and get a crontab working on external-drive backup as well. Gonna be fun!

Thanks for the help :)

---

