---
title: "Trying to understand partition behavior better"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Leiden on 2011-01-28
I have just installed Ubuntu 10.10. It's my first true encounter with linux and I must say I am very pleased with how things work. 

Nearly everything works fine now, but it wasn't in one go. Having been a lifelong MS Windows user there are still some concepts I need to adapt to. But really wanting to understand the underlying mechanics I hope you guys can explain me the following. 

Some weird stuff happened cause of my first partitioning attempts.

I had the following partitioning scheme

/dev/sda = 250GB harddrive

1. /dev/sda1 was a primary partition. 44GB. / was the mounting point. ext4 filesystem. 
2. /dev/sda2 was a primary partition. 200GB. /home was the mounting point. ext4 filesystem
3. /dev/sda3 was a primary partition. 6GB. swap.
4. And then there is a 300GB external usb harddrive (/dev/sdb1 I figure) still having the ntfs file system. 

In that setup /home wouldn't mount during boot and my CD-rom wouldn't mount anything after login. My feelings told me it had to do with my partitioning scheme somehow so I changed it into:

1. /dev/sda1. primary partition. 44GB. / mounting point. ext4 filesystem. 
2. /dev/sda2. extended partition. 200GB. 
3. /dev/sda5. logical partition. 194B. /home mounting point. ext4 files system.
4. /dev/sda6. logical partition. 6GB. swap
5. And again the 300GB external usb harddrive  (still /dev/sdb1)

This seems to have made all previous problems disappear (/home not wanting to mount on boot and CD-ROM not mounting anything). But I can't figure out why (all docs seemed to say that in single os setup marking partitions primary would be best) and also I am not sure I am currently left, with the best possible partitioning scheme.

Could anyone explain me what is/was going on with this?

---

### Post by QLee on 2011-01-28
> **Leiden said:**
> I have just installed Ubuntu 10.10. It's my first true encounter with linux and I must say I am very pleased with how things work. 

Nearly everything works fine now, but it wasn't in one go. Having been a lifelong MS Windows user there are still some concepts I need to adapt to. But really wanting to understand the underlying mechanics I hope you guys can explain me the following. 

Some weird stuff happened cause of my first partitioning attempts.

I had the following partitioning scheme

/dev/sda = 250GB harddrive

1. /dev/sda1 was a primary partition. 44GB. / was the mounting point. ext4 filesystem. 
2. /dev/sda2 was a primary partition. 200GB. /home was the mounting point. ext4 filesystem
3. /dev/sda3 was a primary partition. 6GB. swap.
4. And then there is a 300GB external usb harddrive (/dev/sdb1 I figure) still having the ntfs file system. 

In that setup /home wouldn't mount during boot and my CD-rom wouldn't mount anything after login. My feelings told me it had to do with my partitioning scheme somehow so I changed it into:

1. /dev/sda1. primary partition. 44GB. / mounting point. ext4 filesystem. 
2. /dev/sda2. extended partition. 200GB. 
3. /dev/sda5. logical partition. 194B. /home mounting point. ext4 files system.
4. /dev/sda6. logical partition. 6GB. swap
5. And again the 300GB external usb harddrive  (still /dev/sdb1)

This seems to have made all previous problems disappear (/home not wanting to mount on boot and CD-ROM not mounting anything). But I can't figure out why (all docs seemed to say that in single os setup marking partitions primary would be best) and also I am not sure I am currently left, with the best possible partitioning scheme.

Could anyone explain me what is/was going on with this?

You must have in some way misunderstood a "problem". Those two schemes would both work for Ubuntu. The only real difference is that you have 6GB unaccounted for in the second scheme (what was previously swap on a primary according to your post). The OS doesn't care if on a primary or logical partition.

---

### Post by The Cog on 2011-01-28
Did you re-format sda2 at some point after installing? Re-formatting will change the partition UUID, which is what recent versions of Linux use to locate the partition to mount (see /etc/fstab). That's the only thing I can think of that might have stopped sda2 from mounting at /home.

Both the above partitioning schemes look OK to me. Maybe I would have chopped that 44G into two 22G partitions, leaving one unused for now, so I could install the next version there to try out without trashing my existing install. The only reason my system is over 10G is because it has Doom3, UT and UT2004 installed, and they're quite big games.

---

### Post by srs5694 on 2011-01-28
The Cog's suggestion that you might have reformatted the /home partition makes sense. Other possibilities include manual editing of /etc/fstab or an error while setting up the partitions (say, forgetting to set the mount point for the partition you intended to be /home). In fact, there are quite a few possible causes, but they all have one thing in common: Something different between your current setup and your previous one other than the use of logical partitions vs. primary partitions. Since you've wiped your previous configuration, nobody will ever know what happened to cause problems last time.

---

