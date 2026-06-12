---
title: "Recover Reformatted HD with testdisk"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by andyzammy on 2009-12-19
Hi all again!
As the thread title states, i have somehow reformatted an external HD, and would just like some clarification before i plunge the red button to reduce further risk of losing all my data.

>   Recovery of reformated partition

If the partition has been reformated to another filesystem (FAT32 formated as NTFS or vice-versa),

    * run TestDisk,
    * select the harddisk, the partition type
    * choose Advanced
    * select the partition
    * choose Type,
    * enter the value corresponding to the previous filesystem
    * choose Boot
    * choose RebuildBS
    * List
    * If you can see your files, choose Write and confirm
    * In Analyse, choose to rewrite the partition with the correct partition type. 

This is what i have from the testdisk site, and is exactly what i need in order to recover my data.

However, i'm unsure about the specifics of 'partition type' selection, for the HD's current status (i'm assuming it doesn't even matter because from what i gather i'm going to change it to its previous state anyway - am i correct?): i've never reformatted it, it's been as i first bought it. in the selection option i leant toward the "intel" because i suspected it was a fat32 FS. However, when it comes to choosing "Type" after selecting intel, there are numerous versions of FAT32 and i really don't know which one it could have been, or what the common choice is.

i went for the first "FAT32" i could find, (0b), but second time i tried the "current" type (0c).. both times, it searched for a FAT table, and after a little while found some files. even though i don't recognise any of the files it found, the fact that it could see files (while there are none currently on this new (re)formatted HD) means that they're those i was looking for. is this a safe assumption?

now i didn't choose "write" and confirm because i just wanted to make sure that if i write and confirm will this recover *all* of my data? also, after i do this "write" and "confirm" thing, do i also have to do as the last bullet point in the quote suggests? (choose to rewrite the partition with the correct partition type)

thanks for your time,
zammy

---

### Post by lkraemer on 2009-12-20
How about trying this before working on your hard drive.

Get your camera, and an empty media card.  Take some pictures.
Delete the pictures.  Then use testdisk to see if you can 
recover the pictures.  The procedures should be very similar 
except you will need to rebuild the Drive info with testdisk.
Any training you can do with the camera's media will be useful.
Heck even format the card with pictures, and recover that first.

lk

---

### Post by andyzammy on 2009-12-20
> **lkraemer said:**
> How about trying this before working on your hard drive.

Get your camera, and an empty media card.  Take some pictures.
Delete the pictures.  Then use testdisk to see if you can 
recover the pictures.  The procedures should be very similar 
except you will need to rebuild the Drive info with testdisk.
Any training you can do with the camera's media will be useful.
Heck even format the card with pictures, and recover that first.

lk

thanks for the tip, i tried it with an mmc card (only thing i have i can freely mess about on) but testdisk wouldn't show it as a drive - it only gave me the option to select my HD's. is there a way of forcing testdisk to look at a particular /dev/xxx..?

---

### Post by lkraemer on 2009-12-20
I am correct.  I just stuck in my Memory card in my reader, and used testdisk to
cruise around on the memory stick, but no files were deleted or existing.

You should be able to do the same.  My device automatically showed up
as /dev/sdc because it was in the card reader.


lk

---

### Post by andyzammy on 2009-12-21
> **lkraemer said:**
> I am correct.  I just stuck in my Memory card in my reader, and used testdisk to
cruise around on the memory stick, but no files were deleted or existing.

You should be able to do the same.  My device automatically showed up
as /dev/sdc because it was in the card reader.


lk
yours must have been a usb reader, mine is an integrated reader... anyway i borrowed a memory stick which it could see and tried to reproduce the steps (started with a few small txt files) but it didn't work.

can you please write down the steps you took so i can copy it parrot fashion, when i follow the steps from that wiki it concentrates on something like "boot sector" which i thought was strange because i'm trying to find files on the actual partition.

i tried going through analyse but it either didn't find any files or it found a weired one called "75.C0A" which i don't recognise and i think is a nonsense pile of 1's n 0's it thinks is a file..

i can't tell you how i managed it but on one attempt it did dig up 2 (only 2!) files of what must have been 1000's. i was able to copy them over but what about all the rest of the files? also, because i have the best part of 500 Gig of data on the HD i don't want to copy all the files over to recover them (and couldn't if i wanted to - not enough space on my other HD's), but just repair the partition.

---

### Post by lkraemer on 2009-12-21
Guides:
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

The last portion of the first guide is what you want.
READ all of the guides before doing anything.

You will most likely need to boot from LiveCD, then install testdisk.  Gparted will already be installed.
Then you will need another drive that can be used to for storage of any files you recover.  BE SURE to
use Gparted to locate which drive is located where, and make good notes so you don't create more damage.
Then when you are ready you can use testdisk and/or photorec to rebuild and recover the files.

It might be a good idea to try all of this on an old USB Flash drive, just so you know exactly what you
are doing.  I'd get a 256 Meg USB Flash Drive, partition it, format, and copy files to it, then format it again 
and give that a test before trying to recover your data and take the chance of losing it.

lk

---

### Post by andyzammy on 2009-12-21
> **lkraemer said:**
> Guides:
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

The last portion of the first guide is what you want.
READ all of the guides before doing anything.

You will most likely need to boot from LiveCD, then install testdisk.  Gparted will already be installed.
Then you will need another drive that can be used to for storage of any files you recover.  BE SURE to
use Gparted to locate which drive is located where, and make good notes so you don't create more damage.
Then when you are ready you can use testdisk and/or photorec to rebuild and recover the files.

It might be a good idea to try all of this on an old USB Flash drive, just so you know exactly what you
are doing.  I'd get a 256 Meg USB Flash Drive, partition it, format, and copy files to it, then format it again 
and give that a test before trying to recover your data and take the chance of losing it.

lk

This is what i've been trying to say,
i've already come across and read all of these, and when i tried to follow the last portion of the first guide, it didn't work for me when i tried it on a usb stick. i wasn't even able to view the missing files after i reformatted the memory stick, never mind recover the partition.

photorec works in a fashion, but it will be useless to my recovering the HD files - for one, the names are all lost, so going through 500 gig will take longer than i have left to live (i have lots of source code on the HD and putting all that together will be impossible) and for another thing, like i mentioned in my previous post, i don't have another 500 gig storage medium to recover my files to. The only ideal solution for me is to recover the HD to its former form, which with testdisk, is supposed to be super easy according to all i've found recently through google, but for some reason i'm unable to get to work.

i don't need to boot from livecd because the HD i messed up isn't my primery one i boot ubuntu from, just an external media HD.

analysing the mem stick seems to bring no joy at all. it can only ever find the partition that i reformatted with the memory stick with. it won't find the previous format, and so won't list any files from that format.

using the boot sector recovery option in the advanced section is the same. i just can't recover the files i put onto the memory stick prior to reformatting it.

---

### Post by lkraemer on 2009-12-22
Well, if it doesn't work for you then I'd say you're at the point
where a purchase of some recovery software is worth more than
spending another three or four days messing around.  After all 
your recovered software must be worth that small cost compared
to the loss of time and code.  Some of the recovery software
will let you see the files, but not recover all of them until
you purchase.  Google can help you locate those.

I don't know what else to suggest.

lk

---

### Post by andyzammy on 2009-12-22
thanks for your help lkraemer. before i do that i would like to try one more thing before i go get professional help though.

i tried to rebuild the boot sector to the HD i am trying to restore, and it did show me some valid files (though i don't recognise them, the fact that it can recognise some files i seem to be doing ok - i'm just worried that i can't see *all* of my files.

i pressed "write", but now i can't mount the HD in ubuntu (though can still access it in testdisk) - the error was "can't read superblock".

when i go to the advanced section of testdisk now it says "A valid FAT boot sector must be present in order to access any data; even if the partition is not bootable."

i now notice that there is a "repair FAT" button (though i can't remember if it was there before).

[http://www.cgsecurity.org/wiki/Advanced_FAT_Repair](http://www.cgsecurity.org/wiki/Advanced_FAT_Repair)

reading the bottom section tells me that messing with this runs the risk of losing my files if it doesn't work, but by the sound of it, this is what i need to do in order to repair my HD. pressing the "repair FAT" button gives me options from which FAT tables to remove corrupted clusters from.

how do i know which one to choose? and if i should do both or not (i don't even know if i'm able to do both, having not tried it yet..)

i'm at the point now where i rebuilt the boot sector and doing this found some files. is "repair FAT" the next step to take? which FAT table do i modify? is there a way to back these up before i mess with them so i can restore them if it makes it worse?

---

