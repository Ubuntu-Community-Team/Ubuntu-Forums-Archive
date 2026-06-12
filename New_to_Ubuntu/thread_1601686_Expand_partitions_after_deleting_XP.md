---
title: "Expand partitions after deleting XP"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by DoctorTim on 2010-10-20
Machine is a Fujitsu LIfebook T.  I had installed 10.04 many months ago as a dual boot with XP.  I find myself using the XP OS less and less (read never) and used gparted to delete the windows partition. Updated grub and all is well.  Would like to use the 38 GB of disk space I freed up for music and movies in linux, but cannot figure out how to expand the existing partitions.  Do I have to boot from a thumb drive and use disc manager to resize my existing partitions and swap file?  Are there instructions to do so (used search but found not much in the way of specifics).  Thanks in advance,
Tim

---

### Post by psusi on 2010-10-20
Yes, you have to boot from some other disk ( cd or usb stick ) so the partition is not in use, then gparted can resize it.

---

### Post by DoctorTim on 2010-10-20
Thanks
Will do and check back
Tim

---

### Post by srs5694 on 2010-10-20
Another option, which is safer but possibly less flexible, is to use the former XP space as one or more new partitions. You'd use GParted or mkfs to create Linux filesystems on those partitions, then mount them and either use them as new empty space or move existing files to them and remount them at some suitable location. This could be awkward or it could work very well, depending on the sizes of all your partitions and how much data you've got.

---

### Post by drs305 on 2010-10-20
This post discusses expanding /. You are removing rather than shrinking Windows but much of it still applies:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by DoctorTim on 2010-10-20
I'm now at home,running from a live boot disc and still can't seem to get this done.  Will give this another shot,but I seem mired in gparted not being able to combine two partitions or to expand one into unused space...

Help?

---

### Post by drs305 on 2010-10-20
Two things to watch for. 

Even from the LiveCD, swap is mounted. You have to unmount it before moving things around. Highlight it, then Partition, Swapoff.

Also, are you trying to combine the space in a primary partition with that of a logical partition? That can't be done. They are two separate containers. you can either copy the logical into a primary partition or into unallocated space by making another primary partition, or shrink the primary partition to a small value, expand the extended partition to the left, and then expand the logical partition to the left.

If you post a screenshot of what you see in GParted we can probably spot your problem.

---

### Post by DoctorTim on 2010-10-20
Here's a screenshot.
[ATTACH]172980[/ATTACH]

  The unallocated space is where XP was.  It is also where I would like to expand the swap space to 4GB (2GB RAM) and the file space.  When I try to do so there are max sizes set for each and I do not understand how to expand them.
[ATTACH]172981[/ATTACH]

  like sda5 is 18735...
Can this be easily changed?
Tim

---

### Post by psusi on 2010-10-20
The other partitions are contained inside sda3, so you need to resize that one first by expanding it to the left.

---

### Post by DoctorTim on 2010-10-20
Genius!
Thanks,
working now
Tim

---

### Post by DoctorTim on 2010-10-20
What is the sda2 partition formatted as NTFS?  Should I expandthis while I am at it?
Tim

---

### Post by psusi on 2010-10-20
> **DoctorTim said:**
> What is the sda2 partition formatted as NTFS?  Should I expandthis while I am at it?
Tim

It's your drive, you tell us ;)

---

### Post by srs5694 on 2010-10-21
> **DoctorTim said:**
> What is the sda2 partition formatted as NTFS?  Should I expandthis while I am at it?

Chances are it's the Windows Recovery Environment partition, which is used on many Windows installations as an emergency boot recovery tool -- if Windows becomes unbootable, you can use it to run CHKDSK or whatnot on the main drive. Sometimes it seems to be involved in booting Windows regularly, too, but I'm a bit foggy on the details.

To be sure you don't have any important files on that partition, you could mount it and see what's on there.

BTW, given the apparent drive sizes, I'd recommend doing as I suggested in my earlier post, but with an added detail: I'd create a new partition in the (now) free space and use it as /home. This will require moving your current /home directory to the new space and modifying /etc/fstab. There are numerous Web-based tutorials on how to do this, such as [this one.](http://www.ibm.com/developerworks/linux/library/l-partplan.html) I believe there's an Ubuntu-specific one, too, but I don't have a URL handy.

Using a separate /home partition has several advantages. Most importantly, you can easily wipe out your current installation and re-install fresh without affecting your user files. This is useful in some emergency situations, if you want to do a fresh install to start clean without whatever cruft you've accumulated, or if you want to switch from Ubuntu to some other distribution. As stated in my earlier post, doing it this way is also safer, since partition resizing operations that alter the start of a partition are much riskier than those that alter the end of a partition. Creating a new partition in free space is, if not completely risk-free, much less risky than altering an existing partition.

---

