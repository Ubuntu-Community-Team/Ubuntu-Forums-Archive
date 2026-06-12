---
title: "4GB Flash Drive only allows 2GB. Verbatim Store nGO"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by crjackson on 2009-08-08
A friend of mine gave me a 4GB USB drive to install Ubuntu Live for them to test.  The 4GB drive is seen only as a 2GB drive.  How can I fix this?

Point me in the right direction please...

---

### Post by rlogan on 2009-08-08
Has the drive been partitioned into 2Gb parition and 2Gb left unformatted ?

Check it with Gparted would be where I would start

---

### Post by crjackson on 2009-08-08
No, not that simple.  Even Unpartitioned it only reads as a 2GB device.  I've tried it on 4 different systems. Hardy, Jaunty, XP, and Vista all show the same.

---

### Post by corncob on 2009-08-08
I don't know if this has anything to do with your problem if you've repartitioned, reformatted and everything else, but I have had these pen drives showing a lot less space than they were supposed to have.  The problem I found was a hidden .Trash file that had everything in it that I had deleted from the drive.  In the VIEW menue, check SHOW HIDDEN FILES.
I also found that Gparted won't repartition a drive until you unmount it.
One last thought: Who says its a 4GB drive?

---

### Post by Vakman on 2009-08-08
> **corncob said:**
> I don't know if this has anything to do with your problem if you've repartitioned, reformatted and everything else, but I have had these pen drives showing a lot less space than they were supposed to have.  The problem I found was a hidden .Trash file that had everything in it that I had deleted from the drive.  In the VIEW menue, check SHOW HIDDEN FILES.
I also found that Gparted won't repartition a drive until you unmount it.
One last thought: Who says its a 4GB drive?

I agree with the trash file idea but I think they would have noticed that, unless he/she is on Windows then I don't think they would have missed the file. And it probably says on the drive that it is a 4GB drive. Then again if it was unpartitioned then nothing would be on it and then there would be no trash file.

---

### Post by lswb on 2009-08-08
I have run into a number of usb drives and sd cards that were fakes or counterfeits, not sure what to call them. They are labeled for instance 4GB or 16GB or whatever and their internal structure has been modified so that some system checks will show a capacity agreeing with the label, but when you try to store data on them they actually have a capacity less than stated, and you start getting errors. You can google up a better description of these fakes if you want more info.

---

### Post by crjackson on 2009-08-09
I have googled it and I must not be using the right search phrase because I don't find much on the subject.  I do remember reading of the problem before here on the Ubuntu Forums but now I can't find that either.  I know there is a solution but it escapes me.  Multiple re-partitioning and formating does nothing.  It sees the drive as 2GB without any partitions or format at all.

---

### Post by crjackson on 2009-08-09
Any other ideas?

---

### Post by kerry_s on 2009-08-09
are you sure it's 4gig ?

i would zero it out & then use gparted to format it.

```
 dd if=/dev/zero of=/dev/?
```

use "sudo fdisk -l" to find what its listed as, on mine it's /dev/sda.

---

### Post by crjackson on 2009-08-10
> **kerry_s said:**
> are you sure it's 4gig ?

i would zero it out & then use gparted to format it.

```
 dd if=/dev/zero of=/dev/?
```

use "sudo fdisk -l" to find what its listed as, on mine it's /dev/sda.

Thanks, I've go to take it back to the owner right now.  If he is upset I'll see if he'll let me have it back to try this.

---

