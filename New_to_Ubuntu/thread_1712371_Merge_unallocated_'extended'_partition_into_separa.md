---
title: "Merge unallocated 'extended' partition into separate into NTFS partion"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Pureferret on 2011-03-22
Hi guys, I've searched the web for my specific problem but I can't find an answer to my specific problem.

I have just installed Ubuntu 10.04 onto my HDD, alongside Win7 and a 'media' partition, both of which are 'separate' as it were, and NTFS. Now when I installed Linux I wasn't paying much attention, and I shrank the 'media' part' down to 200GB leaving 450GB for Ubuntu, not making the Ubuntu partition 200GB (the minimum is would let me at the time) and keeping the media part' at 400GB.

Now what I want to do is shrink the Ubuntu extended part' down to say 150GB and make the media back up to 500GB, however I can't shrink the extended partition in GPartEd, I can only play with the sub partitions (Ext4, unallocated and linux-swap) leaving the extended partition at 450GB ish.

So how can I merge some of the 'extended' unallocated space onto my 'media' partition?
I've attached a picture so you can see the situation.

p.s I've installed Ubuntu so I can write/run some code for my uni work, and the deadline is monday, so quick responses would be especially appreciated!

---

### Post by tordeu on 2011-03-22
I guess gparted does not know how to resize the partition, because how could it resize a partition which includes partitions? I assume it does not know what to do in this case (If you would tell it resize it to 200GB, how should it do it? Should it just take the unallocated space or should it resize the ext4 to 100GB and just reduce the unallocated space to achieve the 200GB?)

You could try to use gparted to move the ext4 partition of Ubuntu to the right, so that the unallocated space is not in the middle between the ext4 and the swap, because this way you will probably not be able to use it.

EDIT: I assume you use the gparted included in the live cd? Try using [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) instead.

---

### Post by Dutch70 on 2011-03-22
Since you're on a time limit I'll try to help. 

AFAIK you've got 2 options.
1. Delete the Ubuntu partition, redo your partitioning scheme & reinstall Ubuntu with the set up you want. (Ubuntu installs don't take long.)
2. Use the unallocated space to create another media/data partition, or just whatever you want to call it. You can still format it as NTFS and will have acess to it from windows & Ubuntu. You may find that a very useful option.

If you have time, you may want to see if someone else has a better idea, I could be overlooking something.

Edit: You may want to try deleting your swap partition, then see if it will let you resize the extended partition. If it doesn't work, Swap is easy enough to re-create. Remember you can't work on a partition while you have it mounted.

---

### Post by tordeu on 2011-03-22
I am not sure either, but moving the ext4 to the right and then resizing the extended partition with the System Rescue CD should be a possibility.

---

### Post by Quackers on 2011-03-22
I would say that both of the above options would be good.
Unfortunately, as the gparted screenshot shows, you may need to run a chkdsk on the sda2 partition (which I presume is your main Windows installation). The orange triangle may signify an error. This could have been caused by resizing that partition. Does Windows still boot ok?

---

### Post by Pureferret on 2011-03-22
@Tordeu, yes that does make sense. I used GPartEd on a CD I burnt myself, though I doubt it makes much difference. I will try to move the partition with the GPartEd programme, and if it doesn't work I'll try and use the SysResCd option

@Dutch, I'll keep those as a fall-back option if the SysResCd doesn't work, cheers.

@Quackers, Thanks I spotted that but didn't think much of it. It's the main Win7 partition but it's not been resized. Not sure what the ! triangle means.

Thanks again guys!

---

### Post by tordeu on 2011-03-22
If it works and you got the free space next to your windows partition, I would prefer resizing the ntfs-partition of your media center from within Windows. Some people have problems when resizing ntfs partitions with gparted and doing it from Windows seems to be the safest option.

---

### Post by Dutch70 on 2011-03-22
To find out what the triangle is, right click it & select "information"

You can't actually click the triangle, but it will select that partition. It's Just easier to explain that way.

---

### Post by Pureferret on 2011-03-23
Moving the extended sub partitions totally worked. I didn't think it would but when I re-ran GPartEd it saw the unallocated space as a new partition  separate from 'extended'

Moving the media drive now but planning to resize the C drive in windows as advised

Aweseomsauce, all sorted :D

---

### Post by tordeu on 2011-03-23
That sounds awesome. I hope that everything will be like you want it to be, once you resized the partition in Windows.

---

### Post by Dutch70 on 2011-03-24
> **Pureferret said:**
> Moving the extended sub partitions totally worked. I didn't think it would but when I re-ran GPartEd it saw the unallocated space as a new partition  separate from 'extended'

Moving the media drive now but planning to resize the C drive in windows as advised

Aweseomsauce, all sorted :D

Nice! Glad to hear it's working like you want. 
Let us know the end result & don't forget to mark this thread "solved" when you're satisfied, so others can learn from your experience. 

Best regards

---

