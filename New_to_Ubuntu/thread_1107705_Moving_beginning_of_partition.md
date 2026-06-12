---
title: "Moving beginning of partition?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by gogetadbl on 2009-03-27
Hello,
I currently have several partitions on my hard disk.  The partition I'm looking to move is my /home partition which is located at the very end of the disk.  I would like to move it to left in GParted.  However, the left side of this partition is shaded in yellow so I can't move it left.  Is there a way I'd be able to increase this partition?

Thanks!!

Edit: 
Attached image.  the goal is to move sda7 and merge it with the unallocated space.  All this is done in the Ubuntu LiveCD.  When I double click sda7, the cursor won't move left, although I can resize it to the right all I want.  I can also move the swap left or right.  The thing I can't do with any partitions is move the cursor past the shaded area.

---

### Post by egalvan on 2009-03-27
A screen-shot would be of great helo in visualizing what you have..

Applications -> Accessories -> Take Screenshot

---

### Post by gogetadbl on 2009-03-27
> **egalvan said:**
> A screen-shot would be of great helo in visualizing what you have..

Applications -> Accessories -> Take Screenshot

I've attached it to the original post.  I should've thought of doing a screenshot earlier

---

### Post by drs305 on 2009-03-27
Yes, you can move it left to incorporate the adjacent free space. Doing so will require that the partition be unmounted. Since this is a system folder, that means you will need to boot to a liveCD, gparted CD or a systemrescueCD to perform this action with gparted. Expanding the partition left will also take a bit of time.

As with any partition action, make sure to back up your important files before performing this action.

---

### Post by mikechant on 2009-03-27
And when running from the LiveCD, you will probably need to 'unmount' the swap partition to do this operation - right click on the sda6 line and select 'swapoff'. Then you should be able to right-click on sda7 and select 'resize'.

---

### Post by gogetadbl on 2009-03-27
All this is done in the Ubuntu LiveCD.  When I double click sda7, the cursor won't move left, although I can resize it to the right all I want.  I can also move the swap left or right.  The thing I can't do with any partitions is move the cursor past the shaded area.

For example, originally I took off space from my sda5.  So I had to shrink the partition, move the swap left, and now I'm at this step.  I've just been using the GUI to click and drag the right end of the partition, but I can't click and drag the left end.

---

### Post by drs305 on 2009-03-27
If you select the unmounted sda7 and select Partition, Resize/Move, you should have a value in the "Free Space Preceeding" window. If you set that to 0 and then click on the "New Size" window does the size adjust to fill the entire available space?

If you have completed any other repartitioning operations it may be helpful to post another pic of your current situation.

---

### Post by gogetadbl on 2009-03-27
> **drs305 said:**
> If you select the unmounted sda7 and select Partition, Resize/Move, you should have a value in the "Free Space Preceeding" window. If you set that to 0 and then click on the "New Size" window does the size adjust to fill the entire available space?

If you have completed any other repartitioning operations it may be helpful to post another pic of your current situation.

The free space preceding field is greyed out with a value of 0 in it.  I don't see a New Size button anywhere.  The only thing I can do is make the partition smaller by moving the right edge to the left.  The left edge is unmovable.

---

### Post by plucky on 2009-03-27
Your extended partition is locked because the linux-swap partition is mounted.You need to select the swap partition and set swap to off.

That should unlock the extended partition and should then allow you to move the start of the sda7 partition into the un-allocated space.

Once the start of the partition has moved,you can then resize the partition.

Moving the start of a partition can take a long time as it has to move the data as well,so once started,you should let it finish.


Good Luck

---

### Post by louieb on 2009-03-27
Other that sda7 is close to full can't think of any good reason you should not be able to move it to the left. 

Might try this.

[LIST]
[*]Create a new partition in the unallocated space.
[*]Copy sda7 to the new partition.(Gparted can copy one partition to another)
[*]delete sda7
[*]grow the new partition to occupy the space that was used by sda7.
[/LIST]
Growing a partition to the left is pretty slow. Doing the create.copy... probably will be faster. Good Luck.

---

### Post by gogetadbl on 2009-03-27
> **louieb said:**
> Other that sda7 is close to full can't think of any good reason you should not be able to move it to the left. 

Might try this.

[LIST]
[*]Create a new partition in the unallocated space.
[*]Copy sda7 to the new partition.(Gparted can copy one partition to another)
[*]delete sda7
[*]grow the new partition to occupy the space that was used by sda7.
[/LIST]
Growing a partition to the left is pretty slow. Doing the create.copy... probably will be faster. Good Luck.


I was considering this, but would this not be risky?  Copying the partition to the part to the left would create sda8, then deleting sda7 and growing sda8 still leaves the name of that partition sda8, so won't my filesystem be messed up?

---

### Post by louieb on 2009-03-27
Is sda7 or sda5 the / (root) partition? If its sda5 you should be fine. 
If its sda7 you will have to change the UUID's in /boot/grub/menu.lst  and /etc/fstab.  If sda7 is your /home partiton then /etc/fstab will need changing.

You can get the UUID of a partition by using the live CD by
```
sudo blkid
```

---

### Post by gogetadbl on 2009-03-28
Hmm, so it turns out the Ubuntu Live CD can't do this like a GParted Live CD.  I can do this move just fine with the GParted liveCD.  Thanks for all the replies guys!

---

### Post by egalvan on 2009-03-29
> **gogetadbl said:**
> ...t turns out the Ubuntu Live CD can't do this like a GParted Live CD.
 I can do this move ... with the GParted liveCD.  
Thanks for all the replies guys!

The UbuntuLiveCD ( and many others) tend to have older versions of 
gparted...

The gparted LiveCD always has the latest version.

Case in point...

Ubuntu 8.04.x has a version of Gparted which has poor support for the LABEL function.

ErnestG

---

### Post by drs305 on 2009-03-29
> **egalvan said:**
> The UbuntuLiveCD ( and many others) tend to have older versions of 
gparted...

The gparted LiveCD always has the latest version.

Case in point...

Ubuntu 8.04.x has a version of Gparted which has poor support for the LABEL function.

ErnestG

This is true. On some of the older versions you must install ntfsprogs to be able to perform certain functions on ntfs partitions. Fortunately, this is not the case on newer releases of the GParted.

---

