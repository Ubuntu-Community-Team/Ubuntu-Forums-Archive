---
title: "Format USB Drive (possibly using gparted)"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by StuM on 2010-05-18
Hi,

Please could someone help me format my USB drive.  As you can see from the screenshot below, the files systems have gone a bit screwy.


[IMG]http://i.imgur.com/ZITVA.png[/IMG]


From reading on the forums it seems gparted is the tool for this, but I don't understand what I need to do.  A lot of the options are greyed out when I select one of the partitions.

---

### Post by jrothwell97 on 2010-05-18
Your drives appear to still be *mounted* - i.e. tied to the file system through a folder that acts as a junction to that device. You need to unmount the drive before you format it, and you can do that quickly using gparted - right-click the two partitions with the keyring next to them, and from the menu select "unmount".

---

### Post by StuM on 2010-05-18
> **jrothwell97 said:**
> Your drives appear to still be *mounted* - i.e. tied to the file system through a folder that acts as a junction to that device. You need to unmount the drive before you format it, and you can do that quickly using gparted - right-click the two partitions with the keyring next to them, and from the menu select "unmount".

I did try that, and have done so again, but it doesn't seem to unmount.  Nothing changes, and the only options on the right click menu are: Unmount, Manage Flags and Information.

---

### Post by jrothwell97 on 2010-05-18
> **StuM said:**
> I did try that, and have done so again, but it doesn't seem to unmount.  Nothing changes, and the only options on the right click menu are: Unmount, Manage Flags and Information.
Hmm.

Have you tried unmounting the drives using your file manager? Exit GParted for the moment, and then right-click the icons on the Desktop for the existing partitions. There should be an "unmount" option in there - give that a go.

---

### Post by philinux on 2010-05-18
How about using the System>admin>disk utility.

---

### Post by StuM on 2010-05-18
> **jrothwell97 said:**
> Hmm.

Have you tried unmounting the drives using your file manager? Exit GParted for the moment, and then right-click the icons on the Desktop for the existing partitions. There should be an "unmount" option in there - give that a go.

I seem to have cracked it.  There wasn't an unmount option... but a 'eject' or 'safely remove hardware', both of which did unmount so to speak.  But once I re-plugged to get it to show up in gparted or on the desktop the same problem occurred.

But one of the other right-click menus (possibly preferences) gave me an option to unmount the partitions.  Which I've now done and after deleting them are now left with 4GB of unallocated space.  Which file system should I now select to format it with?  FAT32?  (I want it to work on both Linux and Windows machines)

**Edit**: Noting philinux's comments... The Disk Utility is exactly what I used, which I came across somehow through the right-click menus.

---

### Post by jrothwell97 on 2010-05-18
If you want to work with Linux and Windows machines, you can use FAT - however, I'd strongly recommend reformatting it in Windows as NTFS. This is because NTFS is more fault-tolerant, can deal with bigger partitions, and is generally a lot better. Ubuntu can read and write to it, but you need to use Windows to format it initially.

---

### Post by StuM on 2010-05-18
> **jrothwell97 said:**
> If you want to work with Linux and Windows machines, you can use FAT - however, I'd strongly recommend reformatting it in Windows as NTFS. This is because NTFS is more fault-tolerant, can deal with bigger partitions, and is generally a lot better. Ubuntu can read and write to it, but you need to use Windows to format it initially.

Okay, that makes sense.  Thanks for all the help. Problem solved.

---

### Post by philinux on 2010-05-18
Disk Utility can format it to NTFS.

In fact I just formatted my 4gig stick.

---

### Post by jrothwell97 on 2010-05-18
> **philinux said:**
> Disk Utility can format it to NTFS.
I stand corrected - thanks.

---

### Post by StuM on 2010-05-18
> **philinux said:**
> Disk Utility can format it to NTFS.

In fact I just formatted my 4gig stick.

So it can.  I've just formatted my 4gig stick too :)

Thanks again.

---

