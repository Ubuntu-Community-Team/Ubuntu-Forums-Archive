---
title: "Need to reinstall ubuntu"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-02
I use windows xp and I installed ubuntu last night as a dual boot, my first time installing linux, and Ive been having various problems with it. Ive been told on another forum that the problem is I didn't set a big enough partition for ubuntu during installation and the partition is literally full with just the OS so I (or any of my apps) can't create any files.

So I want to uninstall ubuntu completely and then reinstall it with the correct partition size. From what Ive read the procedure to do this is to -
1) First reset the MBR back to what it was before I installed linux
2) Boot from the ubuntu livecd
3) Use the gparted tool to completely delete the ubuntu partition
4) Reinstall ubunutu?

Is that procedure correct? And do I need to format anything after deleting the ubuntu partition in step 3 or can I simply go ahead and reinstall?

---

### Post by kylehotchkiss on 2009-07-02
I would just pop in the Ubuntu CD, make the partition larger from there if I were you. You could also reinstall to there. I would also defrag windows before shrinking it too much, I just feel like data is safer that way when the NTFS resizer does it's thing.

---

### Post by ajgreeny on 2009-07-02
There is absolutely no need to restore the windows MBR unless you want to do a couple of defrags just to make sure that windows is well placed on the disk.

How much space did you make available for ubuntu?  The gnome default system takes about 2.3GB, but then you need space to add appliactions you install, and for your own files, so a minimum of 10GB would be OK just to try out the system.

If you find that it is as good as I think itm is, you will probably end up shrinking your windows partition right down and increasing the ubuntu partition.  As an example, I started several years ago on a 160GB disk with 20GB for ubuntu and the rest for windows.  It is now the other way round, 20GB for windows and the rest for ubuntu, which is my main OS.

---

### Post by ltwinner on 2009-07-02
Well I actually would prefer to do a fresh install as Im not 100% sure some of the problems are down to the partition being full. I would like to have a completely fresh start so to speak. So with that im mind is the procedure I outlined in my first post the correct way of doinig it?

---

### Post by ltwinner on 2009-07-02
> **ajgreeny said:**
> There is absolutely no need to restore the windows MBR unless you want to do a couple of defrags just to make sure that windows is well placed on the disk.

How much space did you make available for ubuntu?  The gnome default system takes about 2.3GB, but then you need space to add appliactions you install, and for your own files, so a minimum of 10GB would be OK just to try out the system.


I just selected the defaults all the way through installation as I presumed everything would be fine. However the default partition size was 2.5Gb, I can't understand how the ubuntu installer would have that as the default when every newcomer that goes with the default option would then end up in the position I am in with no space left for anything else.

I didn't add ubuntu onto a disk that has been running windows for months/years. I had just formatted the drive and made a fresh install of windows xp, then I installed ubuntu. So I dont think it should be too much of an issue restoring the windows mbr. I really just want a fresh start with ubuntu as my initial experience has not been good and I HAVE to use linux as I want to do all my web development open source.

---

### Post by ajgreeny on 2009-07-02
> **ltwinner said:**
> Well I actually would prefer to do a fresh install as Im not 100% sure some of the problems are down to the partition being full. I would like to have a completely fresh start so to speak. So with that im mind is the procedure I outlined in my first post the correct way of doinig it?
Not quite.  As I said, there is no need to restore the winMBR, just to remove it again with your ubuntu install.

Run the ubuntu live CD and run Partition Editor to shrink the win XP partition and then delete the ubuntu partitions to make free space of whatever size you want.  Now install ubuntu and when you get to the partitioning stage, choose to install into that free space.

Good luck.  It probably sounds more difficult than it actually is, but try it out and come back again if you need to.

---

### Post by ltwinner on 2009-07-02
> **ajgreeny said:**
> Not quite.  As I said, there is no need to restore the winMBR, just to remove it again with your ubuntu install.

Run the ubuntu live CD and run Partition Editor to shrink the win XP partition and then delete the ubuntu partitions to make free space of whatever size you want.  Now install ubuntu and when you get to the partitioning stage, choose to install into that free space.

Good luck.  It probably sounds more difficult than it actually is, but try it out and come back again if you need to.

Well that makes sense and doesn't seem too difficult. I would still like to know about uninstalling it completely though as a couple of people told me I should try out various distro's and find one that suits me best. And I dont want to have several distros installed at once, I want to try em out one at a time. So can someone tell me the procedure for uninstalling ubuntu? Is what I posted in my op correct?

---

### Post by papenpj on 2009-07-02
Regardless of it you remove ubuntu or not, likely when you install a new distro it will overwrite the MBR anyways and likely give an option to change partitions.

---

### Post by ajgreeny on 2009-07-03
> **papenpj said:**
> Regardless of it you remove ubuntu or not, likely when you install a new distro it will overwrite the MBR anyways and likely give an option to change partitions.
+1.
Just install over the ubuntu partitions you already have, It generally will not matter which distro you choose they will all do more or less the same.  Just a few could cause you problems, eg fedora which uses (or used to use) lvm and it was a pain to me, anyway.  Perhaps it is easier now, though the last time I looked at it I did not like it one bit compared to Ubuntu.

---

