---
title: "Change volume label in fat32 partition"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by adit on 2010-10-22
I have a partition in hard disk drive (/dev/sda4) formatted with fat32.  Current volume label is "MYNAME".  I want to change it to "MyName"

---

### Post by Paqman on 2010-10-22
There may be an easier way, but I know Gparted can change the label on a volume. It's in the repos, and comes preinstalled on the LiveCD.

---

### Post by adit on 2010-10-22
I tried it under windows vista.
And also tried the following command.
```
:~$ sudo mlabel -i /dev/sda4 ::
Volume label is MYNAME
Enter the new volume label : MyName
```
No use.
In the sidepane "Places" in nautilus it is shown as MYNAME

---

### Post by adit on 2010-10-22
Tried to rename with gparted also.  Same problem

---

### Post by yetiman64 on 2010-10-22
Try and do a logout and then log back in. I have noticed on occasion that labels won't change in the places menu and nautilus sidepane until you do so.

---

### Post by ironic.demise on 2010-10-22
System > Administration > Disk utility.
Find you're disk drive (sda, should be described as something like 500gb disk)
click it
In the window with the disk drive details click the volume you want to change (sda4, should have MYNAME written on it, it's the long bar that names all volumes, just click yours)

then click "edit filesystem label"
and type what you want.

---

### Post by adit on 2010-10-22
In response to post#6
That also done.  Same problem. The volume label does not accept lower case letters at all.
Now I have a doubt. Is fat32 filesystem case insensitive when labelling the volumes?

---

### Post by plucky on 2010-10-22
> **adit said:**
> In response to post#6
That also done.  Same problem. The volume label does not accept lower case letters at all.
Now I have a doubt. Is fat32 filesystem case insensitive when labelling the volumes?

My USB stick is FAT32 and the Label has upper and lowercase letters.

Do you have it mounted in /etc/fstab file with the label specified?

---

### Post by ironic.demise on 2010-10-22
His problem may also be an autorun.inf setting.
on the root of the stick check the autorun.inf for a line "LABEL=MYNAME"

---

### Post by adit on 2010-10-24
I solved the problem by
1) Back up the partition
2) Delete the partition
3) Create filesystem
```
sudo mkfs.msdos -n MyName /dev/sda4
```
4) Finally restore from the backup
It is a 30 GB partition.  The entire process took 2 hours.
As far as known to me there are no tools (either in unix or in windows) to change the volume label of fat32 partition in a case sensitive manner.

---

### Post by coffeecat on 2010-10-24
> **adit said:**
> As far as known to me there are no tools (either in unix or in windows) to change the volume label of fat32 partition in a case sensitive manner.

Theoretically, you can't but Acronis Disk Director in Windows somehow manages to get lower-case letters onto FAT32 partition labels. Which may be  of little use to you.

Frustratingly, I'm sure I've done it in Ubuntu, somewhat by accident, but I can't remember how. I just tried in Maverick's Gparted and that didn't work.

---

### Post by coffeecat on 2010-10-24
> **adit said:**
> I solved the problem by
1) Back up the partition
2) Delete the partition
3) Create filesystem
```
sudo mkfs.msdos -n MyName /dev/sda4
```4) Finally restore from the backup
It is a 30 GB partition.  The entire process took 2 hours.

I've discovered how I did it in the GUI. Rather than simply trying to label the FAT32 partition in Gparted, use Gparted to create a new partition table on the drive first. Then create a FAT32 partition. Then label it. The proof is in my screenshot.

Of course, you'll still have a several-hour backup and restore to contend with if there's data to preserve.

---

### Post by HermanAB on 2010-10-24
DOS volume labels (and a few other things in DOS and Windows) are upper case only.

---

### Post by adit on 2010-10-24
> DOS volume labels (and a few other things in DOS and Windows) are upper case only
When I create filesystem with 
```
mkfs.msdos -n MiXedCaSe /dev/sda4
```
the case is preserved whether I access the filesystem from unix or windows.

---

### Post by tajiknomi on 2010-10-24
[SIZE=2]*Note that while labeling your disk...U should **Unmount** it first*[/SIZE]....(using-GPARTED)

---

### Post by Vishal Agarwal on 2010-10-24
If you have the window/Dos installed then u can use "label" command through command prompt.

---

### Post by cjv8888 on 2010-10-24
Try the instructions here:

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

which includes renaming FAT32 drives.

---

### Post by kazimof on 2010-12-02
gparted worked for me by dismounting the FAT32 USB stick and running it as superuser thus:

```
sudo gparted
```

---

### Post by MestreLion on 2010-12-27
I stumbled upon this issue when Ubuntu suddenly stopped automounting my USB on **/media/<label>** and started mounting on **/media/<UUID>** instead, apperentely for no reason. Nautilius showed the partition as "16GB Filesystem" instead of using the label, as if there was none.

I cleared and re-set the label on gparted, it worked, monting and nautilus were back to /media/label, but now trapped in that annoying uppercase issue. 

Somehow, trying some commands, ***i was able to restore the proper case without deleting and re-creating the partition, thus preserving all the data. No need to back and restore*** :D

Here how i did:
- clear the label (may use gparted for this)
- set it using either **dosfslabel** or **mlabel** (or both, not sure which actually fixed it)

To check:
```

sudo dosfslabel <device>
sudo mlabel -i <device> -s ::
sudo blkid

```To set:
```

sudo dosfslabel <device> <label>
sudo mlabel -i <device>  ::<label>

```**Warning**: after fiddling with these commands, filesystem always got corrupted. Heres how i fixed it:

```

 sudo fsck <device> -r

```Hope this helps!

---

### Post by Troop116rules on 2012-08-29
> **MestreLion said:**
> i was able to restore the proper case without deleting and re-creating the partition, thus preserving all the data. No need to back and restore :D

Here how i did:
- clear the label (may use gparted for this)
- set it using either **dosfslabel** or **mlabel** (or both, not sure which actually fixed it)

To set:
```

sudo dosfslabel <device> <label>

```

I am sorry for reviving the topic, but I wanted to assess MestreLion's confusion on what command to set the label.

All I did, after clearing the label in GParted (which is done by setting the label to null, that is, no characters at all. GParted handles this as clearing the label.), is run this:
```
sudo dosfslabel <device> <label>
```
This set the correct label with lowercase letters. It seems FAT labels cannot be 'changed' without forcing uppercase letters. But GParted can do more than change. It can reset/clear the entire label, thus allowing dosfslabel to set the label to the wanted text.

Note: Don't use GParted to add the label after clearing. GParted uses mlabel by default to set the label, which I've seen have issues setting labels with lowercase letters on existing partitions.

---

