---
title: "Expanding ubuntu partition"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by simcaster on 2010-02-05
I installed ubuntu nbr on a 13 gb partition on an xp netbook with 160 gb of hardrive space.  I'd like to expand the ubuntu partiton to 115 gb leaving the xp partition with 30 gb.  I booted into the live usb and resized the xp partition([http://img641.imageshack.us/img641/2135/screenshotfa.png](http://img641.imageshack.us/img641/2135/screenshotfa.png)) now i have a 30 gb xp partition, 100 gb of unalocated space and a 15 gb ubuntu partition.  It was all great until i got to this step, when i try to merge the unalocated space with the ubuntu partition it doesn't work.

Any helpful advice?

---

### Post by drs305 on 2010-02-05
Take a look at this guide for expanding the / partition:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")
Start about half way down the post.

The most likely scenario is that you are trying to move space across an extended partition border. You must first expand the extended partition, then expand your system partition.

Another common problem is not unmounting the swap partition first. The swap partition will be mounted even if using the LiveCD. 

Refer to the guide; if you still have problems or questions please post the results of "sudo fdisk -l"  (lowercase L) or even better a Gparted screenshot.

---

### Post by simcaster on 2010-02-05
> **drs305 said:**
> Take a look at this guide for expanding the / partition:
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
Start about half way down the post.

The most likely scenario is that you are trying to move space across an extended partition border. You must first expand the extended partition, then expand your system partition.

Another common problem is not unmounting the swap partition first. The swap partition will be mounted even if using the LiveCD. 

Refer to the guide; if you still have problems or questions please post the results of "sudo fdisk -l"  (lowercase L) or even better a Gparted screenshot.
Looking at the guide, it says to "drag the border of the partition" i'm not really getting what that means.

screenshot:[http://img641.imageshack.us/img641/2135/screenshotfa.png](http://img641.imageshack.us/img641/2135/screenshotfa.png)

---

### Post by drs305 on 2010-02-05
> **simcaster said:**
> Looking at the guide, it says to "drag the border of the partition" i'm not really getting what that means.

screenshot:[http://img641.imageshack.us/img641/2135/screenshotfa.png](http://img641.imageshack.us/img641/2135/screenshotfa.png)

If your hands are steady ;-) , you can place the cursor on the left light blue border and drag it to the left. It's just a GUI way of changing the size of the extended partition  and is really fast. You can also do it in the size boxes. Click on /dev/sda3 in the lower panel, then select Partition > Resize from the top menu. In the size boxes, just keep increasing the size of the extended partition until it fills all the unallocated space.

---

### Post by simcaster on 2010-02-05
> **drs305 said:**
> If your hands are steady ;-) , you can place the cursor on the left light blue border and drag it to the left. It's just a GUI way of changing the size of the extended partition  and is really fast. You can also do it in the size boxes. Click on /dev/sda3 in the lower panel, then select Partition > Resize from the top menu. In the size boxes, just keep increasing the size of the extended partition until it fills all the unallocated space.
I can't seem to drag the border and the option to resize sda3 is greyed out.

---

### Post by drs305 on 2010-02-05
I mentioned swap has to be unmounted. Your depiction shows swap (sda6) is still mounted. Highlight sda6 and unmount it (right click, Unmount). The "key" icon next to sda6 (and sda3) should go away. If you still show sda3 mounted (key icon), unmount it as well.

---

### Post by simcaster on 2010-02-05
> **drs305 said:**
> I mentioned swap has to be unmounted. Your depiction shows swap (sda6) is still mounted. Highlight sda6 and unmount it (right click, Unmount). The "key" icon next to sda6 (and sda3) should go away. If you still show sda3 mounted (key icon), unmount it as well.
Thanks a lot, it worked.

---

