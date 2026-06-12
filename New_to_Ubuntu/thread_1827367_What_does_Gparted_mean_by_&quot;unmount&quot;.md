---
title: "What does Gparted mean by &quot;unmount&quot;?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-08-17
Hi,
    I'm trying to tidy up my HDD partitions and delete an old unwanted swapfile using Gparted.  You can see it there as sda5 in my attached "GParted3.png".     
But when I try to delete it,  GParted tells me I must first "unmount" my higher number logical partitions.    Can anyone explain what it means by "unmount" here?    See my attached "Delete-sda5.png".   I'm running GParted from a Live CD so none of the partitions I'm working on are "mounted" in the sense that I understand the term mount. 
What would I have to do to get rid of this sda5?    Would deleting it cause my sda6 and sda7 to be automatically renumbered to sda5 and sda6?    I hope not! 
Any explanations welcomed.    Thanks   :)

---

### Post by lmarmisa on 2011-08-18
I agree that the message is not logical.

Try to select Swapoff on the active swap partition /dev/sda7 and check if gparted allows you to delete the old swap partition /dev/sda5. Finally select Swapon.

---

### Post by bigpayne69 on 2011-08-18
As far as the partitions go, when one of them is mounted, it means that the partition is being actively used by the OS. If your using a gparted live cd, then all the partitions should be unmounted by default. If I remember correctly, I had the same problem before, I think you have to right click the swap partition and change it so that it is no longer swap space before you can delete it.

---

### Post by Paqman on 2011-08-18
> **Sleepy-zz-John said:**
> I'm running GParted from a Live CD so none of the partitions I'm working on are "mounted" in the sense that I understand the term mount. 


It's a little quirk of the way the LiveCD works.

The LiveCD automatically looks for and mounts an available swap partition, to improve performance. If that swap partition is inside an extended partition (as in your case) then the whole extended partition gets marked as in use. This prevents you from modifying any partitions within it.

As mentioned above, right click > "swapoff" to unmount your swap partition and free up your extended.

---

### Post by ankspo71 on 2011-08-18
Hi,
I believe you need to unmount both the swap (sda7) and extended partition (sda3) to be able to delete the unwanted swap partition (sda5). Gparted can't work with partitions if they are in use by the system (mounted).

If Gparted is still being being difficult to unmount the paritions...
Try opening your terminal and paste the following into it to turn swap off:
```
sudo swapoff -a
```
This should unmount all swaps and their extended partition(s) which contain your logical swap partitions.

Now restart gparted and try again. It should now show the partitions as unlocked (unmounted), and you will be able to delete the unwanted swap.

Here is a semi-related topic:
[http://gparted-forum.surf4.info/viewtopic.php?id=6260](http://gparted-forum.surf4.info/viewtopic.php?id=6260)

---

### Post by Sleepy-zz-John on 2011-08-18
Thanks for all the replies, folks!   Unfortunately I can't test any of them out at the moment because I've fallen into deeper water since my o.p. by installing a Win XP in my empty sd1.    As far as Windows and Gparted and even my Natty Live CD are concerned this operation has completely wiped out my Natty and both swapfiles and my HDD is now showing empty in Gparted and in Natty's live installation.    But they are all liars because I can still see everything existing there when I run testdisk.   Once I've got this discrepancy sorted out and I can see all my partitions in GParted again,  I hope to report back on this thread.

---

