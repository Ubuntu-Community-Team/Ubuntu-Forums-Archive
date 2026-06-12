---
title: "Move free space to increase home partition using gparted"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by shankhs on 2008-12-29
hi guys I have only 3.35 GB left in my /home partition , so I tried to use gparted to increase the size of /home. I have attached the picture of the status of my various partitions.As you can see that free space is just before the /home partition so when I click my home partition I get "Resize/Move" button greyed out????:confused:
I made the free space ext3 logical partition then tried to resize but still everything is grey(do not work).
Moreover as you can see the / and /home partition are consecutive so I think I first have to insert the free space between / and /home partition the resize the /home partition.Is this possible using gparted?
What do you guys think?
Please help.
Thank You.

---

### Post by taurus on 2008-12-29
You can not resize a partition while you are still using it.  Therefore, you have to use gparted from either LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by Barriehie on 2008-12-29
So at this point the unallocated space before your /home is now formatted?

Barrie

---

### Post by -kg- on 2008-12-29
> I made the free space ext3 logical partition then tried to resize but still everything is grey(do not work).

> So at this point the unallocated space before your /home is now formatted?

That would be my question also.  If you have "made the free space ext3 logical partition then tried to resize," then you have created a new partition in that free space.  You cannot format the free area, even in an Extended partition.  If you have formatted that space, then you have created a logical partition there, and as such will not be able to expand your /home partition into it.

Read the [How To Partition]("https://help.ubuntu.com/community/HowtoPartition") page for a thorough explanation of the procedures.

<edit>  Taurus is also correct.  You cannot do partitioning operations on a partition while it is mounted.  If you are trying to resize your /home partition from your installation, the /home partition will be mounted and cannot be unmounted.

You will need to run GPartEd either from your Ubuntu Live CD or from the GPartEd Live CD, as Taurus said.  Of course, if you *have* created another partition in the free space, you will need to delete that before you will be able to expand your /home partition, in any case.

---

### Post by shankhs on 2008-12-29
Thanx guys as per taurus I downloaded the live cd of gparted and gonna try it.
Barrehie and -kg- I meant to say was I tried to resize the unallocated space both after and before formatting but of no use.
I think taurus' suggestion makes sense , I am in /home and I want to resize it so I must use Live CD.
I will be back in half an hour as I have the ubuntu liveCD and will try to install gparted and resize while I am using live CD.

---

### Post by mkvnmtr on 2008-12-29
From what I see in the picture from the live disk you can enlarge into the free space with no problem. If you have created a partition there you will need to delete it so it looks like the picture you posted. If you have a live Ubuntu disk you can use that and have internet while you do it to ask questions.

---

### Post by shankhs on 2008-12-29
I am trying but I think I cannot resize the partition backwards(even after formatting the free space).I see that I can increase by clicking the arrow in gparted window and sliding it forwards but alas I dont have any free space at the end of my /home partition.Moreover it makes sense if my data is stored in /home partition from front to rear how can I resize the same partition from where the data storage started. 
-------------------****************+++++++++-------------
|unallocated space||`f'  /home `r'||/      ||unallocated|
--------------------------|
--------------------------My data starts here.
So how can I slide the `f' more left wont it result to inconsistency???
But hey look there is also a copy paste option when I right-click on any partition.......I dont know how to use it I think it might be helpful....Please help.
Thank You

---

### Post by mkvnmtr on 2008-12-29
OK I am working from memory  but  I believe if you click on your home partition and then on move/resize you will find three boxes. The one in the center will have the size of home. The one at the top will have the distance to the partition to the right ant the other will have the distance to the one on the left.Each little box has arrows going up and down. If you click or hold on the top arrow of the box for the size of your home partition if should enlarge the only way it  can go. Don't worry you can try it it is not going to do anything until later. when you have it set like you want you have to click apply twice. If you have done something wrong it returns an error.

---

### Post by shankhs on 2008-12-29
> **mkvnmtr said:**
> OK I am working from memory  but  I believe if you click on your home partition and then on move/resize you will find three boxes. The one in the center will have the size of home. The one at the top will have the distance to the partition to the right ant the other will have the distance to the one on the left.Each little box has arrows going up and down. If you click or hold on the top arrow of the box for the size of your home partition if should enlarge the only way it  can go. Don't worry you can try it it is not going to do anything until later. when you have it set like you want you have to click apply twice. If you have done something wrong it returns an error.
exactly. But the option to go back is greyed out so I suppose I cant move my partition left.Thats it.
Thanx everybody.Now I must boot from my hard disk.

---

### Post by mkvnmtr on 2008-12-29
The space that you want to move into is it still unformated free space or did you form a partition there?

---

### Post by -kg- on 2008-12-30
> 
Quote:
Originally Posted by mkvnmtr View Post
OK I am working from memory but I believe if you click on your home partition and then on move/resize you will find three boxes. The one in the center will have the size of home. The one at the top will have the distance to the partition to the right ant the other will have the distance to the one on the left.Each little box has arrows going up and down. If you click or hold on the top arrow of the box for the size of your home partition if should enlarge the only way it can go. Don't worry you can try it it is not going to do anything until later. when you have it set like you want you have to click apply twice. If you have done something wrong it returns an error.

exactly. But the option to go back is greyed out so I suppose I cant move my partition left.Thats it.
Thanx everybody.Now I must boot from my hard disk.

OK, I thought you were trying to increase the size of your home partition.  Why would you want to move your partition to the left?

mkvnmtr suggested a method that will work.  From:

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition")

> Resizing a partition can be done one of two ways: 

Changing the "New Size" or the "Free Space Preceeding/Following" sizes. This can most easily be done by changing the size of the partition itself. This is done either by using the up/down arrows to the right of the "New Size" window, or by directly editing the size itself in that Window. Alternately, you can shrink the partition by increasing the non-zero side of the partition in either the "Free Space Preceeding" or "Free Space Following" window.

(!) If you attempt to expand the partition by decreasing the non-zero side of the partition ("Preceeding" or "Following," depending on where the free space is), it will move the partition instead of increasing it's size. The same will apply if free space exists on both sides of the partition. See Moving A Partition for details. 

If there is unallocated space shown to ***either side*** of your /home partition, you can increase the size of the partition in the "New Size" window up to the maximum size that unallocated space allows.  GPartEd will not allow you to increase it beyond that maximum size.

Please do read the pages I have suggested, *especially* the page I've mentioned in this post.  The page in this post is a sub-page of the entire "How To Partition" page I mentioned in my post above and has to do specifically with what you're trying to do here.

---

