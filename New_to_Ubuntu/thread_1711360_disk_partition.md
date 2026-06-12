---
title: "disk partition"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Willye on 2011-03-21
Hi all, my ubuntu is 10.04, i have a usb 500GB disk with NTFS, i would like to create an ext4 partition of 50GB, is there a way to create a partition without clear the data that i have saved on it, i mean, the remaining space of ntfs ?

---

### Post by benfred on 2011-03-21
Hi Willye,

I'm a bit of a beginner so take this with a grain of salt. You should be able to use Gnome Partition Manager (gparted) to do this - look for it in the Ubuntu Software Center. Once installed its in the System\Administration menu.

Once you've got it running you should be able to shrink the ntfs partition and add a new one in the newly unallocated space.

Hope that helps!
Ben.

---

### Post by Willye on 2011-03-21
Hi Benfred, i tried to use gparted but it clean all entire disk   :)

---

### Post by Sidewinder1 on 2011-03-21
Just a word of advice; prior to shrinking the ntfs partition, make certain that you defrag it, at least once, twice wouldn't hurt. Just one of many things that I've learned the hard way. Don't ask... :)

HTH,
Side

P.S. If you're using win 7, I have read that using win partition editor is best for shrinking; but I have no first hand experience with "7".

---

### Post by Sidewinder1 on 2011-03-21
Ooops... to late...

---

### Post by tarps87 on 2011-03-21
> **Willye said:**
> Hi Benfred, i tried to use gparted but it clean all entire disk   :)

Did you delete the partition or try and resize it?

---

### Post by benfred on 2011-03-21
> **Willye said:**
> Hi Benfred, i tried to use gparted but it clean all entire disk   :)

Oh dear! I did something similar with a Windows 7 ntfs partition earlier today without problem.

Perhaps if you could post a screenshot of gparted with details of what you've done so far someone with more expertise might be able to help you.

Best Regards
Ben.

---

### Post by Willye on 2011-03-21
OK buddies, may thanks, i have used gparted, i had an issue using it, 'cause is necesary to umount the device first and after shrink the device and create a new space formated as ext4


:D

---

