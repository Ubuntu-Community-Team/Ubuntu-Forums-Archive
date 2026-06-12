---
title: "No instal or even Windowsl?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by PEC321 on 2009-05-23
I tried to re-install  XP after stuck with message "GRUB LOADING STAGE 1.5" after XP install message keeps repeating, is there anyway to format the HD, staring from scratch, no such option on BIOS.

---

### Post by balloooza on 2009-05-23
1. stick in the ubuntu disk
2. try without makeing changes... (I think that is what it is)
3. go in the UBUNTU menus, SYSTEM >> ADMINISTRATION >> partition editor

now, delete all the partitions you see (unluess that is you want to save your data, but I think, since you were reinstalling xp, you have made backups?!)

to delete them just click on one of the nice little boxes at the top of gparted, then press delete

THEN make a new partition, large enough for xp 20 gigs, for normal usage is allright, make that partition NTFS (it would be 20000 MB) then make annother partition, this one will be an ntfs also, large enough for your personal files (documents music, et cetera) (so about 40 GB or 40000for me, yours might be diferent this partition will also be NTFS

MAKE SURE YOU LEAVE 10 GB at the end. THEN make an E X T E N D E D(not PRIMARY!!) partition of 10 GB
then in that extended partition make 1 8GB EXT3 (filesystem, not ntfs), and a 2 GB swap (filesystem, also not ntfs) partition

then when all is done, hit apply, and wait a couple of minuits

This all sounds verrrry complicated, but trust me, it will make for easy ubuntu/windows co existance.

NEXT INSTALL WINDOWS_BEFORE_UBUNTU!!!!
use the 20 GB partition as the "C:" drive for windows install

then install ubuntu, and use manuel partitioning

find the 8000 MB partition, click on it (it will be /dev/sd(somthing)(some number) and after clicking on it, click edit (at the botom of the manuel partitioning window) and first check the format box [ ], then USE AS= EXT3 journaling file system and mount point of "/" (without quotes)

then go find your documents partition in the manuel partitioning window, !and click on [edit] again, then USE AS= NTFS and MOUNT POINT= /documents (accualy replace documents with whatever you like, make sure there is a slash before it!!)

Then install ubuntu!!!!



I recomend printing this out, and Good luck, this is a good opertunity to learn a whole bunch about computers

---

### Post by akimatsu123 on 2009-05-23
> **PEC321 said:**
> I tried to re-install  XP after stuck with message "GRUB LOADING STAGE 1.5" after XP install message keeps repeating, is there anyway to format the HD, staring from scratch, no such option on BIOS.

If you just want to format the entire hard disk and install windows xp, you can do that from the win xp install CD. although it's ugly, one of the steps in the blue screen and white text is a partition editor. just delete all of your new partitions and make a new partition. 

if you want to install ubuntu after win xp, don't create a new partition using your entire disk because then to install ubuntu later u need to re-partition your hard drives, which takes forever. leave some unpartitioned space, equivalent to how much you want to give ubuntu + swap.

---

### Post by PEC321 on 2009-05-23
> **PEC321 said:**
> I tried to re-install  XP after stuck with message "GRUB LOADING STAGE 1.5" after XP install message keeps repeating, is there anyway to format the HD, staring from scratch, no such option on BIOS.

Thanks tor the suggestions, but the problem is that nothing works, XP or Ubuntu, past the black screen with the message:GRUB LOASDING STAGE 1.5
                     GRUB LOADING PLEASE WAIT
                      ERROR22
This message after a clean XP install, neither XP or Ubuntu appear when booting. Some Windows BIOS give the Format option, unfortunately my Toshiba laptop doesn't. There is some bug, which I think would be removed with a HD Format and then a XP/Ubuntu re-install.

---

### Post by mehrotra.akash on 2009-05-23
try using gparted, delete all the partitions and use the xp installation disk to install

you will loose ALL your data

also, are you sure that boot from cd is the 1st option in your bios,dont think it should even reach grub till it starts booting from hdd

---

### Post by smurfgod on 2009-05-23
DBAN<-----Daryls boot and nuke

[http://www.dban.org/](http://www.dban.org/)

You will loose all your info on your HDD.Hope this helps.


smurf

---

### Post by Bartender on 2009-05-23
Sounds to me like the OP doesn't know how to go into BIOS and tell the PC to boot from the optical drive...

---

