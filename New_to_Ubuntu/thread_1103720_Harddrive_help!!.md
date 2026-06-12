---
title: "Harddrive help!!"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2009-03-23
After resetting up my harddrive to have a spare 100 gb for XP. All seemed to had went smoothly until XP told me it couldn't install. So I decided to look back at gparted and Ill post a screen of what I get. Booting from terminal it says ```
spence@spence-desktop:~$ sudo gparted
======================
libparted : 1.8.9
======================
Can't have overlapping partitions.

```

I can still boot into Ubuntu fine. I have my partitions setup as follows.
Its a 400 gb hdd. 270gb /home. 10gb /. and 120gb ntfs. HELP

---

### Post by Xiong Chiamiov on 2009-03-23
That screen says that hda is blank.  Please post the output of
```

sudo fdisk -l

```

---

### Post by SpenceMakesSense on 2009-03-23
Ya I knew that part. Thats why I was confused because I could still boot into ubuntu and use my home partition

```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbcbcd60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       31548   253409278+  83  Linux
/dev/sda2           31549       48641   137299522+   5  Extended
/dev/sda3           47506       48641     9124888+  82  Linux swap / Solaris
/dev/sda5           31549       46276   118302628+   e  W95 FAT16 (LBA)
/dev/sda6           46277       47505     9871911   83  Linux

Disk /dev/sdf: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0008892a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        7624     1951728    b  W95 FAT32

```

---

### Post by SpenceMakesSense on 2009-03-23
bump

---

### Post by BGFG on 2009-03-23
What was the exact message XP gave ? seems you have FAT and not ntfs allotted to your Xp install.

---

### Post by SpenceMakesSense on 2009-03-23
Well I cant be exact because it was REALLY long. But it said that it was not able to install to that partition and to go back and try another one. So I those to delete that partition(while in windows install) and retry it with a format and it gave me the same message

---

### Post by Therion on 2009-03-23
> **SpenceMakesSense said:**
> Well I cant be exact because it was REALLY long. But it said that it was not able to install to that partition and to go back and try another one. So I those to delete that partition(while in windows install) and retry it with a format and it gave me the same message
I'm not sure how to fix it, but just look at the [Start] and [End] numbers for your partitions:  When you do, I think you'll see pretty quickly that your partitions appear to overlap.  I'm not sure how that could have happened but things start to bork at the "end" of /sda2 since /sda3 starts pretty much right in the middle of it...

---

### Post by BGFG on 2009-03-23
recently when re-installing Xp it gave me the same message actually tried to delete my ext3 filesystems, It seems when it's installing it tries(at least it seems to me, to me) to remove any other FS found. In my case i was lucky and could simply physically disconnect my drive,(last resort) :)

Try to format the partition to Ntfs through gparted then attempt the install again. i would suggest also that you check a few tutorials on installing xp AFTER Ubuntu, as Xp will overwrite the MBR and you will have to restore grub.

unless you need to game or do something with adobe products, I'd suggest VirtualBox as a viable alternative.

---

### Post by SpenceMakesSense on 2009-03-23
well as a last resort what If I just copied all the contents of my /home directory onto a different harddrive(which is all I really care about) and then reformatted it and copied the contents back into my new /home. Though I dont have a harddrive bigger then my home directory on hand this seems like a big enough issue that it may be easier to just do that

---

### Post by aeiah on 2009-03-23
> **Therion said:**
> I'm not sure how to fix it, but just look at the [Start] and [End] numbers for your partitions:  When you do, I think you'll see pretty quickly that your partitions appear to overlap.  I'm not sure how that could have happened but things start to bork at the "end" of /sda2 since /sda3 starts pretty much right in the middle of it...

i disagree. the numbers seem to add up to me. bear in mind that 'extended' isnt actually really a partition, but a container for the partitions to go in.

i dont understand why it's FAT 16 though. by the looks of things your FAT16 partition (sda5) is approx 60GB, however google tells me that FAT16 can only be of 2GB or less in size per partition. perhaps windows is getting confused and doesn't recognise the file system properly? try formatting it under linux as FAT32, NTFS, or as unallocated and see if windows regains it's brains.

---

### Post by BGFG on 2009-03-23
Why not put Xp on the other drive? you could then set the Ubuntu drive as the first boot device in your BIOS then add XP to grub, effectively dualbooting :)

---

### Post by SpenceMakesSense on 2009-03-23
> **aeiah said:**
> i disagree. the numbers seem to add up to me. bear in mind that 'extended' isnt actually really a partition, but a container for the partitions to go in.

i dont understand why it's FAT 16 though. by the looks of things your FAT16 partition (sda5) is approx 60GB, however google tells me that FAT16 can only be of 2GB or less in size per partition. perhaps windows is getting confused and doesn't recognise the file system properly? try formatting it under linux as FAT32, NTFS, or as unallocated and see if windows regains it's brains.

Well how would I do that if qparted reads the whole harddrive reads as unallocated?

---

### Post by SpenceMakesSense on 2009-03-23
> **BGFG said:**
> Why not put Xp on the other drive? you could then set the Ubuntu drive as the first boot device in your BIOS then add XP to grub, effectively dualbooting :)

Well If i were to do that i would just borrow one from a friend.

---

### Post by BGFG on 2009-03-23
> **SpenceMakesSense said:**
> Well If i were to do that i would just borrow one from a friend.

i see. have you re-scanned in qparted ? the entire drive is seen as unallocated ?

---

### Post by SpenceMakesSense on 2009-03-23
ya(see screen shot) rescanning does snothing

---

### Post by aeiah on 2009-03-23
well as daunting as it sounds, we know one program reads your hard drive that you could use: fdisk :D

be careful of course. you should be able to find lots of info on the net for formatting partitions with fdisk and other commandline tools

---

### Post by SpenceMakesSense on 2009-03-24
could someone possibly point me in the direction of a tutorial to use fdisk ?

---

