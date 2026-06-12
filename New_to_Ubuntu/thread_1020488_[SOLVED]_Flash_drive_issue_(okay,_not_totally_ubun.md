---
title: "[SOLVED] Flash drive issue (okay, not totally ubuntu related)"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-24
I'm using my flash drive to move music from one computer to the other, and whenever I'm done with it, I delete the files and it says there's only 20 MB or so free (it's a 4G flash drive).  I figured out that there's a hidden file called .trash-1000 that always is left over for some reason, so I delete it.

Well now I'm getting the message "There was an error getting information about the files in the folder ".Trash-1000"." when I try to delete it, so if I can't delete it, my flash drive is basically useless.

Any suggestions?  Sorry for posting a non-ubuntu issue here, but I couldn't find flash drive forums that have actually been looked at in  the past 2 years.

---

### Post by newbee70 on 2008-12-24
> **tegnoto89 said:**
> I'm using my flash drive to move music from one computer to the other, and whenever I'm done with it, I delete the files and it says there's only 20 MB or so free (it's a 4G flash drive).  I figured out that there's a hidden file called .trash-1000 that always is left over for some reason, so I delete it.

Well now I'm getting the message "There was an error getting information about the files in the folder ".Trash-1000"." when I try to delete it, so if I can't delete it, my flash drive is basically useless.

Any suggestions?  Sorry for posting a non-ubuntu issue here, but I couldn't find flash drive forums that have actually been looked at in  the past 2 years.


** One way is to reformat your flash drive. **

---

### Post by swoody on 2008-12-24
When you delete something on your flash drive it will move it to that '.trash-1000' folder much like when you delete something from your computer, and it goes to the 'Trashcan'. When you unmount the drive it will empty the trash for you. Try deleting everything, and then unmounting the drive and remounting it - it should clear the .trash-1000 folder. If not, the drive may just write over the info that has been moved to the .trash folder when new info is written to the drive.

---

### Post by tegnoto89 on 2008-12-24
Sorry this sounds dumb, but I'm not sure how to go about reformatting a flash drive with ubuntu (so now it IS an ubuntu issue!)

---

### Post by northern lights on 2008-12-24
Either run ```
gksu gparted
```to open a GUI based partitioning tool or run [format]("http://www.terminalcult.org/manpages.php?manpage=format+&Search=Search") to format from CLI.

If gparted is not installed, run```
sudo apt-get install gparted
```once to set it up.

If you opt for command line formatting, run```
blkid
```to find out what device the USB flashdrive is. Then run ```
format /dev/sdXX
```for instance. For more information on the format command, see the man page (link above).

---

### Post by newbee70 on 2008-12-24
> **northern lights said:**
> Either run ```
gksu gparted
```to open a GUI based partitioning tool or run [format]("http://www.terminalcult.org/manpages.php?manpage=format+&Search=Search") to format from CLI.

If gparted is not installed, run```
sudo apt-get install gparted
```once to set it up.

If you opt for command line formatting, run```
blkid
```to find out what device the USB flashdrive is. Then run ```
format /dev/sdXX
```for instance. For more information on the format command, see the man page (link above).


**why not just format it through gparted?**

as long as you know which device it is. and in gparted you can left click on the device upper right and it will show all drives.

look at each one. since you know it is 4 gig.

left click on the device below the partition information.
then in the upper toolbar click on partition, then format to.

but you need a few extra files for gparted;

add remove gparted; then

use sudo apt-get install <filename> 

xfsprogs
xfs
ufs
reiserfsprogs
reiser4progs
ntfsprogs
jfsutils
hfsprogs
hfsutils
hfs
hfs+
jfs
dosfstools
e2fsprogs

---

### Post by northern lights on 2008-12-24
> **newbee70 said:**
> **why not just format it through gparted?**
First option I gave the OP...

> **newbee70 said:**
> but you need a few extra files for gparted;

add remove gparted; then

use sudo apt-get install <filename> 

xfsprogs
xfs
ufs
reiserfsprogs
reiser4progs
ntfsprogs
jfsutils
hfsprogs
hfsutils
hfs
hfs+
jfs
dosfstools
e2fsprogs
What wicked filesystems do you want the OP to format the flashdrive as? Most common for flashdrives are FAT filesystems. Mostly FAT32. gparted handles ext2/3 and FAT out of the box.

Further, gparted does not need to be reinstalled to add further filesystemprogs.

---

### Post by newbee70 on 2008-12-24
> **northern lights said:**
> First option I gave the OP...


What wicked filesystems do you want the OP to format the flashdrive as? Most common for flashdrives are FAT filesystems. Mostly FAT32. gparted handles ext2/3 and FAT out of the box.

Further, gparted does not need to be reinstalled to add further filesystemprogs.

** I agree if they are swapping between windows or other devices,** but I always load all formats just to make sure that if I need them in the future; I have them ready.

**for swapping between windows and linux I would use ntfs-3g "file size".**

---

### Post by northern lights on 2008-12-24
Please refrain from yelling.

No further comments - I don't have the time to flame.

Merry Christmas.

---

### Post by LowSky on 2008-12-24
FAT32 is the best options, NTFS and EXT3 are bad. NTFS is bad becasue it can casue a lock out if unmounted improperly. EXT3 has no native Windows support

---

### Post by northern lights on 2008-12-24
> **lowsky said:**
> fat32 is the best options, ntfs and ext3 are bad. Ntfs is bad becasue it can casue a lock out if unmounted improperly. Ext3 has no native windows support
+1

---

### Post by newbee70 on 2008-12-24
> **northern lights said:**
> Please refrain from yelling.

No further comments - I don't have the time to flame.

Merry Christmas.


Who is yelling?

if your talking about my bolding words "that is meant to show emp".
shouting as I remember it is all ** "Capitol letters". **

and a **"very merry Christmas to you too / and a happy new year".**

---

### Post by northern lights on 2008-12-24
> **newbee70 said:**
> Who is yelling?

[...]

and a **"very merry Christmas to you too / and a happy new year".**
Fair enough. Thank you, Sir.

---

### Post by tegnoto89 on 2008-12-27
Sorry to bring this up again -

I believe I have formatted it to FAT32 (that's what Gparted says), but what do I do now?  I tried moving some files over to it, but it's still called "USB Drive" instead of "GS Drive" (Geek Squad), and I can't put anything on it, it just doesn't do anything when I drag files over.

Note: before I formatted it in gparted, I tried doing in on my home computer with Windows XP, and it wouldn't format. I tried running the error checker, and even that wouldn't work.

---

### Post by tegnoto89 on 2008-12-27
Yay, nevermind, I got it!  Thanks guys!

---

