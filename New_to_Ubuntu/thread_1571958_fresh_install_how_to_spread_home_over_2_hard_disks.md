---
title: "fresh install: how to spread /home over 2 hard disks?"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by luca.it on 2010-09-10
Hello
just started with ubuntu (10.04).
During install, I tried to partition the pc, which has 2 hard disks (sda and sdb). During the install, I chose manual partitioning, and set up the following;

sda1= /
sda2= /home 
sda3 (extended) and sda5=swap

then, heavily guessing, I made the

sdab one single partition with '/homesdb' as mount point.

NOTE: have to admit that even after a couple hrs browsing the net, I wanst able to understand what a mount point is, and therefore how to use it. So, as to the partitioning reported above, I just tried, inventing.... My INTENTION was in fact to have the most part of sda dedicated to /home, AND also to have sdb fully dedicated to /home. I actually even tried to assign /home both to sda2 AND sdb, but as I kinda expected it wasnt allowed. 
So I opted to give sdb the '/homesdb' monunt point -- but have no idea what that exactly means.

Here it is the situation. As Im writing, ubuntu is actually installing on the laptop, so I have no idea what's going to happen. It is reaching now 48%, seems to work... (:

So, is this the right way to handle the double HD situation?

(PS: for the moment I havent even tried to make a more sophisticated install with more partitions like /boot, /var, etcetera; I feel first I must understand this mount point thing.)

Regards, Luca.

---

### Post by endotherm on 2010-09-10
there are a number of options, but i would look into using mount points, links, or if you really wanna get into it, raid0 (it makes 2 disks appear as one, but if you lose one, you lose the data off both. )

as for a mount point, think about windws for a minute. if you open my computer, you see drives like A:\, C:\, etc. think of these as mount points. the drive c is mounted to the location "c:\" if you want you can think of my computer itself as '/' (just conceptually, they actually work quite differently.)

in linux, things work a little differently, in that all mount points must be within the partition "/" (root). 

if you want to look at your mounted volumes, just open a terminal and type 'mount'.
here is a couple lines from mine:
```

/dev/sda1 on / type ext4 (rw,errors=remount-ro,acl)
/dev/sdb1 on /home type ext4 (rw,acl)

```first the physical drive named /dev/sda1 will be mounted as the root. all other drives must be mounted to some folder within / . / is the mount point for sda1.

next, now that root is mounted,  we mount my home partition (on physical disk /dev/sdb1) to /home, so /home is the mount point for sdb1.

as for your space issue, it comes down to how you store your data. if a lot of the files in your home will all be in the same directory (lets say ~/archive), then you could move that directory to the new drive, and then mount it to ~/archive. the files would Appear to be in the same place, but would actually be on the other drive. or you could mount the new drive whereever you want, and us a link  (like a shortcut in win) to make the archive appear to be in your home, when it;s actually in /media/sdb1 or whatever

---

### Post by oldfred on 2010-09-10
Some more info:
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions. Not for NTFS

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

I prefer to have a separate partition as /data (you can call it anything) and have most of your data in the separate partition (I have almost all but the hidden folders & files that are used for user settings). You can directly mount it in /home or link folders. I created in /data the same folder structure as /home - Documents, Downloads, Pictures, Music etc and then link each of those folders into /home.

Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by srs5694 on 2010-09-10
Another view on mount points: They're just directories (normally empty) that serve as entry points to partitions. That is, if you create a separate partition for /home, it will be mounted on the /home directory. Thereafter, when you access a file in /home (say, /home/luca/data.txt), the OS looks on the partition you set aside for /home for the file, but it drops the path to the mount point itself *within* that partition -- some /home/luca/data.txt is actually luca/data.txt on the /home partition.

I'm not a fan of oldfred's approach of using a separate /data partition for user data. That's the *whole point* of a /home partition, after all, so why complicate matters with symbolic links? Just create a separate /home partition and use it the way it's been used in Unix and Linux for decades.

In terms of combining two partitions so that they can both be accessed under /home, there are several possible solutions:


[LIST]
[*]**LVM** -- Logical Volume Management (LVM) enables you to merge two or more partitions on the same or different disks into what's known as a *volume group,* which serves as a holding area for *logical volumes.* Even if a volume group consists of many partitions on multiple disks, it's viewed as a single storage space, so you can create logical volumes that are larger than any one component partition. Thus, LVM is a very flexible way to do what you want; you can combine your two partitions together and then allocate a logical volume and mount it as /home. Unfortunately, Ubuntu doesn't make working with LVMs easy, but it can be done.
[*]**RAID** -- A Redundant Array of Independent Disks (RAID) configuration lets you combine multiple partitions into a single storage area that's used more-or-less directly. RAID and LVM have some similar features, but RAID is mostly designed to improve reliability, speed, or both, whereas LVM increases the flexibility of managing disk space. As with LVM, Ubuntu doesn't make managing RAID very easy.
[*]**Mounting one inside the other** -- If your username is luca, you can mount one of your user-data partitions as /home and then mount the other inside your home directory (say, /home/luca/foo). This approach is relatively easy, but inflexible -- the space inside /home/luca/foo will be fixed, so if you run out of space in that directory you'll have to move some files outside of that directory (or vice-versa if /home fills up).
[*]**Using a separate mount point and symbolic links** -- You could do something like what oldfred suggests and mount one partition at /home and the other somewhere outside of your home directory (/home/data or /data, say). You can then either use these spaces directly or create symbolic links. For instance, you could create /data/foo and /data/bar subdirectories and then create symbolic links from /home/luca/foo to /data/foo and from /home/luca/bar to /data/bar. This can be a bit more flexible than the previous solution, since you can move entire directories from one partition to the other; but it's not nearly as flexible as an LVM solution and it's rather inelegant. Moving directories back and forth can also take time, particularly if these are large partitions holding large files (like system backups or video files).
[/LIST]


Personally, I favor LVM for this sort of situation; however, as I said, Ubuntu doesn't make using LVM easy. (FWIW, Fedora makes LVM much easier to set up and use.) If you're interested in using LVM, you can try Googling "Ubuntu LVM;" that turns up a bunch of hits for me, although I haven't bothered reading through them to find one I consider good for new users. If you're not comfortable with the extra hassles of setting up LVM, you'll have to go with one of the last two options. (RAID is a possibility, too, but it's got the same set of drawbacks as LVM and LVM is more about flexibility, which is what you want.)

---

### Post by achase79 on 2010-09-10
I use lvm on my computer for this exact reason.  If you are using the standard Ubuntu installer you have to separate your root (/) directory as a separate partition from the lvm partition on the first disk.  This is because the standard kernel will not boot when the root is in the Logical Volume Group.

---

