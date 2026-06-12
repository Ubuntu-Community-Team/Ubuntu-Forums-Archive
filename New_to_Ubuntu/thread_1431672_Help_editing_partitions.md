---
title: "Help editing partitions?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by karasuman on 2010-03-16
I messed up a little installing things on my new computer, and I need some help fixing the partition allocation.  I need very basic instructions on what to do and how using gparted.

My laptop came with Windows 7, which is on its own partition, and I'd like to leave it alone.  In the process of messing stuff up, though, I installed Ubuntu twice.  My "Places" menu shows waaaay too many places: a 67 GB filesystem which I'm pretty sure is the Windows partition and two others that seem to be remnants of the first Ubuntu install.  How can I get rid of these partitions?

I tried to use gparted, but I keep getting an error that the kernel was unable to understand information about changes.  Also, gparted asks me to unmount "all logical partitions" with a number higher than the one I'm trying to edit, but I don't seem to have the option to unmount anything.  I'm not sure how I made such a mess of things.

Basically, I want to have an Ubuntu partition, a Windows partition, whatever little partitions the computer needs to be happy and boot stuff, and that's it.  Help?

---

### Post by derekeverett on 2010-03-16
Logical partitions live inside Primary partitions.

Perhaps you are trying to un-allocate a primary partition without first un-allocating the logical partitions inside it?

---

### Post by srs5694 on 2010-03-16
We'll be better able to help if we have some basic information. Please start a Terminal (it should be an option in one of the menus) and post the output of the following commands:

```

sudo fdisk -l
df -h

```

The information from these commands will help us tell how your system is currently configured and what can be done about it.

---

### Post by derekeverett on 2010-03-16
There are also several g-parted video tutorials [[COLOR="Blue"]here[/COLOR]]("http://www.youtube.com/results?search_query=gparted+tutorial&search_type=&aq=0&oq=gparted").

---

### Post by karasuman on 2010-03-16
Here's the output of the commands:

```
beth@grumpy-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2da44573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
/dev/sda2   *          13        1288    10240000    7  HPFS/NTFS
/dev/sda3            1288        8937    61440000    7  HPFS/NTFS
/dev/sda4            8937       60801   416599585    f  W95 Ext'd (LBA)
/dev/sda5            8937       17068    65313156    7  HPFS/NTFS
/dev/sda6           17069       18172     8867848+  83  Linux
/dev/sda7           59373       60801    11478411   83  Linux
/dev/sda8           18173       57943   319460526   83  Linux
/dev/sda9           57944       59372    11478411   82  Linux swap / Solaris

Partition table entries are not in disk order
beth@grumpy-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             300G  3.1G  282G   2% /
udev                  1.9G  336K  1.9G   1% /dev
none                  1.9G  200K  1.9G   1% /dev/shm
none                  1.9G   92K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda5              63G   89M   63G   1% /media/3476ED8A76ED4CE4

```

I have successfully used gparted before, but this stuff about logical partitions?  I didn't know anything about that.  I guess I don't really know what I need to do more than I don't know how to do it.

---

### Post by derekeverett on 2010-03-16
If my understanding is correct, you can have many logical partitions inside 1 primary partition.

The primary partition must be created first and the logical partitions inside must be formatted the same as the primary.

---

### Post by srs5694 on 2010-03-16
First, about logical partitions: The Master Boot Record (MBR) partitioning system used on most x86 and x86-64 systems supports only four main partitions, which are known as "primary partitions." To use more than four partitions, you must create a special type of primary partition, known as an "extended partition," which serves as a placeholder for a third partition type ("logical partitions"). An extended partition can hold an arbitrary number of logical partitions. Note that derekevertt's claim that logical partitions live inside primary partitions isn't quite accurate, or at least it's not the usual way of stating the arrangement, since the carrier partition for logicals is normally referred to as an extended partition.

Now, as to your system: You've got three primary partitions (1-3), an extended partition (4), and several logical partitions (5-9). It appears that your Linux installation is on /dev/sda8. /dev/sda9 is swap space, so you don't want to delete that. /dev/sda6 and /dev/sda7 appear to be unused -- probably relics of those two previous installation attempts. You should be able to delete both of these partitions, either using fdisk (launch it as "sudo fdisk /dev/sda", use the 'd' option to delete the partitions, use 'p' to verify that you've done it right, and then use 'w' to save the changes; if you make a mistake, use 'q' to quit without saving your changes) or GParted. You may need to reboot before the computer recognizes the changes.

Unfortunately, this will leave the system with some space in an unavailable state. You can recover it by creating a new partition and then mounting it somewhere convenient; or you can reboot into an emergency system such as [PartedMagic](http://partedmagic.com/) and use GParted in that system to resize your main Ubuntu installation. Rebooting in this way is necessary because GParted can't resize any partition that's in use, and of course your boot partition is in use whenever you boot the computer.

---

### Post by srs5694 on 2010-03-16
> **derekeverett said:**
> If my understanding is correct, you can have many logical partitions inside 1 primary partition.

The primary partition must be created first and the logical partitions inside must be formatted the same as the primary.

This is only partially correct. First, as I just noted in my previous post, logical partitions reside inside an extended partition, which is a special variant on primary partitions.

Second, there's absolutely no requirement that logical partitions be formatted with the same filesystems as each other, and extended partitions are not formatted at all (doing so would wipe out the logical partitions contained within them).

---

### Post by karasuman on 2010-03-16
When I run gparted, I get this error right away:

```

The kernel is unable to re-read the partition tables on the following devices: -/dev/sda

Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access.
```

I have been getting a similar error since the first Ubuntu install I did on this machine.  During the partitioning process of the install, I had the option of ignoring the problem, so I did, and proceeded with the install.  

I definitely never encountered this when I did this before.  This isn't my first time installing Ubuntu on a computer with Windows, and I'm not sure what I did differently.  This is actually less complicated than when I set up my netbook: it came with XP, and I tried the NBR, a version specifically for the Aspire One, and regular Ubuntu before finally going back to the NBR (with a new install).  I somehow managed to clean up all of the extra partitions when I was done.  But I've never seen an error like that before.

I am indeed trying to get rid of sda6 and sda7.  I'm still not clear on what I should be trying to do, though.  If I attempt to delete them in gparted, I am asked to unmount all logical partitions with a number higher than X, and nothing happens.  

When I start gparted from the terminal and attempt these steps, I get the following errors:

```
Error informing the kernel about modifications to partition /dev/sda4 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda4 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy).  This means Linux won't know anything about the modifications you made until you reboot.  You should reboot your computer before doing anything with /dev/sda.

```

This is very similar to what I got during the partition allocation during the original install.

I'm sorry if I'm being dumb.  :-/  I really don't understand what I did wrong or how to fix it.

---

### Post by srs5694 on 2010-03-16
When you system is booted normally, one or more partitions will necessarily be in use. The way Linux works, it's difficult or impossible for the kernel to use new partitions on such a disk. This is what the error messages you're seeing are saying. Ordinarily, GParted is able to at least do its work when this happens, but for some reason, something about your installation (or maybe a bug in the specific version you're running) seems to be causing GParted to flake out over this issue.

I have two suggestions:


[list]
[*]Boot into the Ubuntu installer or an emergency disc system, such as the PartedMagic I mentioned earlier, and use its copy of GParted to do the work. In such an environment, your main disk won't need to have any mounted filesystems, so GParted should be happy to manipulate its partition table.
[*]Use fdisk to delete the partitions, as I described in my earlier post. The kernel still won't be able to re-read the new partition table, but fdisk should at least be able to delete the two partitions in question. You'll end up having to use an emergency disc to resize your Linux partition, though; or you could use fdisk to create a new partition, reboot, mount the new partition, and copy some of your installation onto it.
[/list]

---

### Post by oldfred on 2010-03-16
Most of the liveCD like to use a swap partition on the hard drive if they find one as it can speed things up. If the swap is inside the extended then the entire extended is seen as mounted. If you click on the swap partition you can swapoff, so it is not used or not mounted.

---

### Post by derekeverett on 2010-03-17
> **srs5694 said:**
> This is only partially correct. First, as I just noted in my previous post, logical partitions reside inside an extended partition, which is a special variant on primary partitions.

Second, there's absolutely no requirement that logical partitions be formatted with the same filesystems as each other, and extended partitions are not formatted at all (doing so would wipe out the logical partitions contained within them).

I was under the impression that logical and extended partitions were the same, thank you for correcting me here.

However, are you telling me that logical partitions can exist in the same extended partition and be formatted with different filesystem types?

---

### Post by mikodo on 2010-03-17
yup, I have Ext3 and Ext4 FS's as logical partitions in the same extended partition.

---

### Post by karasuman on 2010-03-17
I used fdisk to delete two of the partitions.  Rather than mess with reclaiming the space now...  Since Lucid comes out in another month or so anyway, and I'll probably want to do a clean install for that, maybe it would be better to figure out how to set up the partitions when I do that install.

I recall that there's a way to manually set the partitions; I used this in reformatting an external hard drive once.  Would it be too complicated to use for a installation?  Is there a way to get it to keep the partitions being used for Windows/whatever and make one new partition for the Lucid install?

---

### Post by oldfred on 2010-03-17
I like to control what is installed where so I always manually partition and use manual install where you select each partition, root, swap and if separate /home to use during the install process. 

I actually now have 3 root partitions - 9.04 which will become 10.04, Karmic and beta so I can test 10.04. I save my fstab and history from the last install to make it easy to remount and reinstall everything in the new install.

---

### Post by srs5694 on 2010-03-17
> **karasuman said:**
> I recall that there's a way to manually set the partitions; I used this in reformatting an external hard drive once. Would it be too complicated to use for a installation? Is there a way to get it to keep the partitions being used for Windows/whatever and make one new partition for the Lucid install?

I always do it this way; I don't trust installers to create an automatic configuration that I like.

That said, if I did the math right, you've only got about 19GB in that free space. That's enough space for a basic Linux installation, but you've got more like 300GB in your current Linux installation. If you're using even 10% of that space, 19GB won't be enough. OTOH, if you're using lots of disk space for personal files, you should be able to mount your current system and use its /home directory for your new system's home. (This would go a little more smoothly if /home were on its own partition, but it can be done even with /home on the root filesystem.)

---

### Post by karasuman on 2010-03-17
Oh, dear.  Things seemed to be fine until I restarted the computer, and then it was GRUB errors galore.  I finally booted from the Windows CD, completely reinstalled that, and then reinstalled Karmic.  (I thought it was generally easier to manage partitions when installing on a Windows machine as to installing Windows on a non-Windows machine, but Windows actually has a pretty nice partition editor now.  It's actually a lot easier to use than the one with Ubuntu...)

I don't know what happened or why, and I'm honestly a little afraid of ever upgrading.  We'll see if some of the Karmic stuff bothers me or not; so far, I miss Jaunty, and sort of wish I'd taken the time to install that instead.

Thanks for the help and the explanation of different kinds of partitions!

---

### Post by mikodo on 2010-03-17
> **karasuman said:**
> Oh, dear.  Things seemed to be fine until I restarted the computer, and then it was GRUB errors galore.  I finally booted from the Windows CD, completely reinstalled that, and then reinstalled Karmic.  (I thought it was generally easier to manage partitions when installing on a Windows machine as to installing Windows on a non-Windows machine, but Windows actually has a pretty nice partition editor now.  It's actually a lot easier to use than the one with Ubuntu...)

I don't know what happened or why, and I'm honestly a little afraid of ever upgrading.  We'll see if some of the Karmic stuff bothers me or not; so far, I miss Jaunty, and sort of wish I'd taken the time to install that instead.

Thanks for the help and the explanation of different kinds of partitions!

It appears you are going to be all right now. Without seeing the Fstab and or gparted dispays, I'm guessing Windows took 3 primary partitions for it self on it's install. Then when you installed Karmic it would have used the largest remaining unallocated space you left for it on the HD. If you didn't manually configure the partition(s) for the Karmic install, it would have installed everything as the 4th primary partition, ie, (/) and /home on it. This is an acceptable arrangement for a dist-upgrade in the future to Lucid, as long as you left enough space on the HD for Ubuntu to use. Linux/Ubuntu will work with this arrangement in GRUB, Windows would not have liked it if you had installed Linux/Ubuntu first; so again, it appears you are all right now.

Good Luck.

---

