---
title: "Can't partition hard drive?"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Nicneven on 2009-09-14
Hi, 
My husband and I recently became interested in using Ubuntu, but we haven't jumped in completely because we mainly use our computers to play MMORPG games, namely Lord of the Rings Online, which unfortunately seem to be difficult to get to run under Ubuntu (so far).
 
Anyhow, he was able to do a dual boot install on his system with no trouble, but when we tried to do the same on my computer, we don't get the option to partition the hard drive. The install disk wants to use the whole drive, it doesn't seem to "see" the Windows installation.
 
The drive I am using has Windows Vista Business on it and is a SATA 500 gig drive. 
 
Help?
 
thanks!

---

### Post by viktara on 2009-09-14
Hi,

If you select the 'places' menu in ubuntu, under computer does it list your windows partition?

Otherwise, I do know some manufacturers used to ship their systems with windows pre-installed and use unusual partition layouts. That could cause an issue too.

Also, opening a terminal and giving
```

fdisk -l
```

Should show you all the partitions on your drive.

HTH


Vik

---

### Post by supererki on 2009-09-14
sudo fdisk -l 
i would say.
but if you want something easier then gparted
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
is pretty straight forward tool.

---

### Post by MelDJ on 2009-09-14
> **Nicneven said:**
> Hi, 
My husband and I recently became interested in using Ubuntu, but we haven't jumped in completely because we mainly use our computers to play MMORPG games, namely Lord of the Rings Online, which unfortunately seem to be difficult to get to run under Ubuntu (so far).
 
Anyhow, he was able to do a dual boot install on his system with no trouble, but when we tried to do the same on my computer, we don't get the option to partition the hard drive. The install disk wants to use the whole drive, it doesn't seem to "see" the Windows installation.
 
The drive I am using has Windows Vista Business on it and is a SATA 500 gig drive. 
 
Help?
 
thanks!

why not try using wubi?

---

### Post by Nicneven on 2009-09-14
Thanks for the answers! Soon as I get home I will check them out. I thought of using wubi, but would really rather NOT have my Unbuntu having anything to do with windows at all if possible. The goal is to eventually scrap windows altogether :P   and if it wasn't for gaming, it would be already done.  Soon as we get LOTRO to run under Ubuntu.......

---

### Post by MelDJ on 2009-09-14
this might help if you install with wubi and then want to remove windows: [https://answers.launchpad.net/ubuntu/+question/7194](https://answers.launchpad.net/ubuntu/+question/7194)

---

### Post by oldfred on 2009-09-14
While a problem with gparted was solved years ago, it is still safer to use Vista to shrink the Vista partition. Defrag your Vista install, even twice if possible. Then shrink the Vista partition from within Vista using Disk Management. Some like to shrink in steps to make sure it boots if they are making a large adjustment. Vista sometimes writes data near the end of the partition which makes it more difficult to shrink.

If using gparted you should have the round to cylinder unchecked for Vista or Win7 to prevent problems. The Ubuntu partitioner should not have any problems with Vista partitions, so I do not understand why it does not see your Vista.

---

### Post by soldier4jesus on 2009-09-14
Hey,
Here are some directions on partioning the hard drive in Vista.

1. To create a new partition (Vista calls it a "volume"), click the Start button, type diskmgmt.msc, and press <Enter> to open the Disk Management utility. 

2.To create space for a new volume, right-click an existing volume and choose Shrink Volume. Vista will calculate the amount of space you can regain and will open a dialog box where you can enter the size of your new volume. (You'll also see the total size before the shrink, the maximum shrink available, and the size of the old volume after the shrink.) 

3.After shrinking, right-click the new "Unallocated" space represented in the program and choose New Simple Volume. 

4.Then follow the wizard's steps to create and format your new volume. When you're done, you'll see your new volume represented in Disk Management's graphs. Note that you can shrink only volumes that use the NTFS drive format. Your new PC's drive is almost certainly NTFS.


This came from PC World's website.  Here's the link if you want to read more about it.


[http://www.pcworld.com/article/132079/partitioning_a_hard_drive_in_vista.html](http://www.pcworld.com/article/132079/partitioning_a_hard_drive_in_vista.html)

Thanks!!
Wesley

---

