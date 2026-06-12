---
title: "Cant find folders!"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Xavant on 2010-04-09
Hi i'm new to linux. I just set up ubuntu on my computer, i have some music and movies on my secondary slave hdd, but i cant find the folders for it, It doesn't make any sense becouse combined these folders are over 160gb and if i go to properties on the hdd it shows that it only got 5gb left of free space (200gb hdd). The folders i can see are 35gb combined, Can anyone help me, Thx

---

### Post by adam22 on 2010-04-09
Maybe they are hidden? Try View>Show hidden folders (or ctrl+h i think).

---

### Post by Xavant on 2010-04-09
Nope not it :/

---

### Post by byStanderone on 2010-04-09
...is your secondary hdd in ntfs, if so install ntfs-3g

---

### Post by Xavant on 2010-04-09
> **byStanderone said:**
> ...is your secondary hdd in ntfs, if so install ntfs-3g

i think so. ntfs-3g? further explination would be appreciated :)

---

### Post by themusicalduck on 2010-04-09
To install ntfs-3g, open a terminal (Applications > Accessories > Terminal) and type ```
sudo apt-get install ntfs-3g
``` or if you'd rather use a graphical interfaace, open Synaptic (Preferences > Administration) and search for ntfs-3g.

---

### Post by tsp_2177 on 2010-04-09
> **themusicalduck said:**
> To install ntfs-3g, open a terminal (Applications > Accessories > Terminal) and type ```
sudo apt-get install ntfs-3g
``` or if you'd rather use a graphical interfaace, open Synaptic (Preferences > Administration) and search for ntfs-3g.
i'm having the same problems too i can locate a lot of files on my computer using wine but i still can't access a lot of my school files and don't know why o and the ntfs 3g didn't help me at all unfortuantely :(

---

### Post by Xavant on 2010-04-09
> **themusicalduck said:**
> To install ntfs-3g, open a terminal (Applications > Accessories > Terminal) and type ```
sudo apt-get install ntfs-3g
``` or if you'd rather use a graphical interfaace, open Synaptic (Preferences > Administration) and search for ntfs-3g.

Did that, still not working :(

---

### Post by themusicalduck on 2010-04-09
> **tsp_2177 said:**
> i'm having the same problems too i can locate a lot of files on my computer using wine but i still can't access a lot of my school files and don't know why o and the ntfs 3g didn't help me at all unfortuantely :(

Where are the files saved? On a Windows partition?

If you need to find your documents folder, then you need to open your windows partition in the file browser on Ubuntu (not on Wine).

If you have vista or win7, go to /Users/*username* and you should be able to find stuff in there.

I think for winXP it's in /Documents and Settings/, but I can't remember exactly and can't check at the moment.

For the OP's problem, all I can think of is running a disk check. I think you can do it using Disk Utility or gparted if you install it.

---

### Post by Xavant on 2010-04-09
its not a windows partition. at least i have never set up any opp system on this hdd, it's just a slave drive and has always been

---

### Post by tsp_2177 on 2010-04-09
> **themusicalduck said:**
> Where are the files saved? On a Windows partition?

If you need to find your documents folder, then you need to open your windows partition in the file browser on Ubuntu (not on Wine).

If you have vista or win7, go to /Users/*username* and you should be able to find stuff in there.

I think for winXP it's in /Documents and Settings/, but I can't remember exactly and can't check at the moment.

For the OP's problem, all I can think of is running a disk check. I think you can do it using Disk Utility or gparted if you install it.
ok thank you i will try that right now

---

### Post by tsp_2177 on 2010-04-09
it worked! thanks so much lol i've been trying to figure that out for a week now i was thinking i had to use wine to do that

---

### Post by Xavant on 2010-04-09
I just figured something out, I'm from Iceland and we use characters like í,ó,æ,ð,á and ú.
I cannt use those characters in folder namiing, could that be a reason why i'm not seeing the folders? the two folders missing have some of those characters!

---

### Post by tsp_2177 on 2010-04-09
> **Xavant said:**
> I just figured something out, I'm from Iceland and we use characters like í,ó,æ,ð,á and ú.
I cannt use those characters in folder namiing, could that be a reason why i'm not seeing the folders? the two folders missing have some of those characters!
i would think that it could be a problem with those characters in there, do you have an operating system that you could possibly go back and change them to see if they will show up then?

---

### Post by Xavant on 2010-04-09
> **tsp_2177 said:**
> i would think that it could be a problem with those characters in there, do you have an operating system that you could possibly go back and change them to see if they will show up then?

i can put the hdd in my dads computer and change it, hope that it's the problem =)

---

### Post by tsp_2177 on 2010-04-09
> **Xavant said:**
> i can put the hdd in my dads computer and change it, hope that it's the problem =)
hopefully let us (well them lol i've only been using ubuntu for like 2 weeks) if that didn't work

---

### Post by byStanderone on 2010-04-10
...perhaps you can also install ntfsprogs, am not sure if there are some dependencies needed from it...it's worth a try.

---

### Post by dunkar70 on 2010-04-10
Have you mounted the drive? With Windows, drives automatically get assigned a drive letter. With Linux, you need to create a mount point and mount the drive.

Type: ```
sudo fdisk -l
```You will get a list of drives and partitions like the sample below:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b8ef2f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2557        2678      979965   82  Linux swap / Solaris
/dev/sda2               1        2556    20531038+  83  Linux
/dev/sda3            2679        9729    56637157+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b8ef2f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2557        2678      979965   82  ntfs
/dev/sdb2               1        2556    20531038+  83  fat32
/dev/sdb3            2679        9729    56637157+  83  ntfs

Partition table entries are not in disk order


```Your second drive will appear similar to /dev/sdb or /dev/sdc with the partitions like /dev/sdb1, /dev/sdb2, etc. [COLOR=Red]Note: If you are using IDE drives instead of SATA, the drive format may be hda instead of sda.[/COLOR]

For each partition you want to mount, do the following:
Identify the partition location, for example: /dev/sdb3
Identify the file system, for example: vfat, ntfs, ext2, etc.
Create a mount point: ```
sudo mkdir /mnt/sda1
```Mount the partition (make sure you use the right file system type and partition:```
 sudo mount -t ntfs /dev/sda1 /mnt/sda1
```

---

### Post by Xavant on 2010-04-10
fixed =) i had to put the hdd in another computher with windows and change thee í,ó characters to i,o =)

---

