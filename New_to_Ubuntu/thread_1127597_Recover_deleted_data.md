---
title: "Recover deleted data"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by romihim on 2009-04-16
i have ubuntu on my laptop ,installed on ext3 filesystem .i have a fat32 data parition (to store all my data) . Today i accidentally deleted one of my important folders(used shift delete :( ) from the fat32 drive. 
how i could recover my data  back ?
in windows i could have used soft like recuva .is der ny ubuntu counterpart ?
or any other way out ./
plz help me out of the situation .

very urgent!!! .

---

### Post by steve101101 on 2009-04-16
try this [http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

---

### Post by northern lights on 2009-04-16
First off, stop writing to and/or modifying the disk/partition immediately!

---

### Post by romihim on 2009-04-16
i have unmounted the filesystem, and mounting it only when i try to recover data with some soft , or any manual i get on the net .

---

### Post by steve101101 on 2009-04-16
> **northern lights said:**
> first off, stop writing to and/or modifying the disk/partition immediately!

+1

---

### Post by romihim on 2009-04-16
thanks for the quick reply .
tried foremost before, itgave some errors wen used it for first time...
trying it again with  this manual....
hope this time it works ..

---

### Post by lkraemer on 2009-04-16
romihim,
First thing is DON'T write to that FAT32 Partition.

Then Download UBCD and SystemRescueCD ISO's.  Burn the ISO's
as Disk at Once (DAO) and at 4x or 8x.  SystemRescueCD has testdisk
included.

Boot from the LiveCD, run testdisk on that partition, and you should
be able to recover the files in that folder.  Photorec is another
Linux program the will recover your files.

Good Luck.

lkraemer

---

### Post by romihim on 2009-04-16
as a last option(if every thing else fails) i  am considring this option  :-

(1) install xp  on  one oof my empty partitions on lappy .
(2) as my data drive is fat32 , so i could use xp softs to recover  the data .
(3) as xp will over write grub , recover the grub ...

but this is quite a lenghty process . 
and plz comment the procedure .

---

### Post by northern lights on 2009-04-16
```
sudo apt-get install testdisk
```

---

### Post by romihim on 2009-04-16
> **lkraemer said:**
> romihim,
First thing is DON'T write to that FAT32 Partition.

Then Download UBCD and SystemRescueCD ISO's.  Burn the ISO's
as Disk at Once (DAO) and at 4x or 8x.  One of these has testdisk
included.  (I forget which).

Run testdisk on that partition, and you should be able to recover
the files in that folder.  Photorec is another Linux program
the will recover your files.

Good Luck.

lkraemer
i have two queries :-
(1)Is test disk the main soft to recover files?? . if that's the case then i can install testdisk on ubuntu and try it. 

(2)wat do u mean by disk at once?
burning both the software in one disk, if not then how to use both of them simulataneously, or any one would do(in which case- ubcd should be the one -having testdisk utility ) .
i have slow internet, so will take bit of time to dwnld the iso's ...
dwnlding them now  .

---

### Post by northern lights on 2009-04-16
> **romihim said:**
> i have two queries :-
(1)Is test disk the main soft to recover files?? . if that's the case then i can install testdisk on ubuntu and try it.
see above.

> **romihim said:**
> (2)wat do u mean by disk at once?When recording data *Disc-at-Once*, all tracks / files are recorded without stopping the laser and the disc is closed.

---

### Post by lkraemer on 2009-04-16
romihim,
Typically when troubleshooting you will want to boot from a LiveCD,
and troubleshoot Hard Drives etc, from the LiveCD.

Both UBCD (Ultimate Boot CD) and System Rescue CD are downloaded as
ISO files.  When you burn them in Linux with, say K3B, you select
DAO and a slow burn speed.  (You may want to burn then with XP
with Nero or Easy CD Creator.....I forget what those commands are)

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

When the ISO's are burned, You boot SystemRescueCD and finally get
to testdisk.  From testdisk you recover the files.

UBCD is another utility you may want to check out.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Another option is to just install testdisk in Ubuntu, which has already
been stated.

lkraemer

---

### Post by romihim on 2009-04-16
nothing going right for me today .......
used foremost with command 
sudo foremost -avT /dev/sda1 
-- it started processing files
and ended with error 
no space to write data ..

before running foremost i had 5-6 gb of empty space .
and now ........ 0 bytes
and no file is written in output folder(wer foremost shpuld have written the data ) .
i have just deleted a 600 mb file from home folder ,yet showing 0 bytes free ....
waat to do now ???

---

### Post by ajgreeny on 2009-04-16
Several years ago I recovered a load of files on a neighbour's computer using a magazine cover CD give-away called Fast File Undelete.  In my case it ran from a floppy, remember those, I still have one and it can be jolly useful.  It appears to still be available but at a cost, so you may want to try the suggestions of others first, and keep this one up your sleeve as a last resort.

---

