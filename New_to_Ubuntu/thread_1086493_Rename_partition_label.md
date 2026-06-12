---
title: "Rename partition label?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by kramer65 on 2009-03-04
Hello,

I've got one partition which is when mounted always "/media/disk". I now want to rename that to "Opslag". I found this thread about it and tried their method of:
```
sudo mv /media/hdb1 /media/share to renane the mount point in /media.
and then sudo nano /etc/fstab
```
for my own thing. However, after I unmounted the partition and typed
```
sudo mv /media/disk /media/Opslag
```
it says (translated from Dutch) "mv: can't find status of &#8216;/media/disk&#8217;: File or folder doesn't exist".

That is pretty obvious since I had to unmount it for this to work.

Does anybody know how else I can rename this partition?

---

### Post by Archmage on 2009-03-04
Sorry, is this a harddisk or a removable medium?

I would simply make the mount-point and then change the /etc/fstab to reflect the change.

---

### Post by jaminux on 2009-03-04
Easy.

Terminal:

sudo apt-get install gparted

gksudo gparted

pick the device you want, unmount the partition

right click on the partition, click label, rename and you're done

GParted is a lot easier for partitioning than the terminal in my opinion.

---

### Post by rolnics on 2009-03-04
Here's a link to [device-partition-labeling]("http://www.debuntu.org/device-partition-labeling#ext") i found it after getting annoyed with trying to work out which partition on my hd's was which.

---

### Post by kramer65 on 2009-03-04
@jaminux

I opened gparted and when I right click the partition (it is unmounted) I don't get an option of labeling. I get Erase, Remove, Format as, Flags, Check, and Information (loosely translated from Dutch to English).

In the Station menu (4th from the left  in the main menu) I get the option of setting a partition label in which I can set some kind of msdos partition label which will erase everything from that drive as well. Is that the option I need?

---

### Post by Elssha on 2009-05-06
Something similar:
    I just installed 9.04 on a laptop with 2 extra partitions (one for storage, one for XP) after getting it back from bestbuy. Both are fat32 (ntfs wasn't an option), created during the install. Now they are called by their size and restricted to root mounting/etc. 
I only want one of them to automount, and I want to change their names to something other than their size. Anyone know how to change the restrictions to let reg user mount/unmount/rename/etc the partition drives and treat them like other 'removable' media as they were back when I ran Hardy? Thanks, and much appreciated ^_^

---

