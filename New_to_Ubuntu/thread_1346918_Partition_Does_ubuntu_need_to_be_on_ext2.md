---
title: "Partition: Does ubuntu need to be on ext2?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-05
Hi I just partitioned my hard drive - just to make sure - the partition I made for ubuntu is ext2 - is that ok?

Ext2 rather than NTFS - 

Thanks

---

### Post by mikewhatever on 2009-12-05
Yes, ext2 is ok, but ext3 is preferable. NTFS is a Windows only file system.

---

### Post by halitech on 2009-12-05
Ext2, ext3, ext4, any of them is fine. Will the drive just be used for storage on a linux machine?

---

### Post by sandyd on 2009-12-05
do you mean ext3/ext4?
and no. ubuntu cannot be installed on NTFS/FAT partitions.
however, it can be installed on...
reiserfs, xfs, ext2, ext3, ext4, and a whole lot others.

---

### Post by aysiu on 2009-12-05
NTFS cannot be used.

I don't see why you would pick Ext2 over Ext3 or Ext4, though.

---

### Post by listerdl on 2009-12-05
> **halitech said:**
> Ext2, ext3, ext4, any of them is fine. Will the drive just be used for storage on a linux machine?

Not storage - it would be used to actual host the ubuntu OS - i.e. partioning 15 gig for the latest ubuntu on ext2

Thanks :)

---

### Post by halitech on 2009-12-05
> **listerdl said:**
> Not storage - it would be used to actual host the ubuntu OS - i.e. partioning 15 gig for the latest ubuntu on ext2

Thanks :)

If you are going to be installing the OS fresh, leave it unformatted and let the partitioner do the formatting for you and use ext3 or ext4 which is now available.

---

### Post by listerdl on 2009-12-05
> **halitech said:**
> If you are going to be installing the OS fresh, leave it unformatted and let the partitioner do the formatting for you and use ext3 or ext4 which is now available.

....hhhmmm....

It is formatting it now....do you think I would be wise to cancel the operation?

Basically what I am trying to do is dual boot W7 and the latest ubuntu with shared data storage.....

---

### Post by halitech on 2009-12-05
> **listerdl said:**
> ....hhhmmm....

It is formatting it now....do you think I would be wise to cancel the operation?

Basically what I am trying to do is dual boot W7 and the latest ubuntu with shared data storage.....

you will need more then a single partition to install ubuntu (or any linux really). You will need a swap space and a partition for / and optionally you can create a seperate /home. For the shared storage, use NTFS as windows cannot read EXT3/4 natively but *nix can read NTFS.

note: you cannot use NTFS partitions for your /home folder

---

### Post by listerdl on 2009-12-05
> **halitech said:**
> you will need more then a single partition to install ubuntu (or any linux really). You will need a swap space and a partition for / and optionally you can create a seperate /home. For the shared storage, use NTFS as windows cannot read EXT3/4 natively but *nix can read NTFS.

note: you cannot use NTFS partitions for your /home folder

So what the best way to dual instal W7 and ubuntu?

---

### Post by halitech on 2009-12-05
> **listerdl said:**
> So what the best way to dual instal W7 and ubuntu?

Personally it depends on what you are using Windows for. If you are using it for games, install windows first and create 2 partitions in the windows installer, leave the second partition empty and not formatted. As far as size, depends on the size of the drive. If you want windows just for a few non-game reasons, install Ubuntu to the entire drive and install Virtualbox and install windows as a virtual machine.

---

### Post by issih on 2009-12-05
For the ubuntu system itself you probably want ext3 or ext4 as others have already said (not that ext2 won't work)

As for the shared storage bit, I'm pretty sure ubuntu can read and write to ntfs partitions out of the box now (if not its only a minor install), so an ntfs partition should do the job of being bulk storage for both OS's, alternatively you can get tools to allow you to read ext2/3 (not 100% sure about 4) partitions under windows, (e.g. [http://win2fs.sourceforge.net/](http://win2fs.sourceforge.net/))

Because of the state the box was in when I first installed ubuntu (yonks ago now) my mythtv box has a partition with the OS on it(ext4) another for /home (ext3) and several ntfs partitions (one for an age old xp install, one for video, one for music and a couple of others for well stuff.

I can see everything from ubuntu, and all the ntfs ones are visible under xp.

Its certainly doable, but you may want to make sure you understand about how to mount the various partitions during the install, unless you want to leave them to be dynamically mounted as and when you want them.

Hope that helps

---

### Post by listerdl on 2009-12-05
If I get it wrong can it cause lasting damage to the machine?

---

### Post by halitech on 2009-12-05
> **listerdl said:**
> If I get it wrong can it cause lasting damage to the machine?

nope, just means you'll need to do it again :)

---

### Post by The Cog on 2009-12-05
> **listerdl said:**
> If I get it wrong can it cause lasting damage to the machine?

Not physical damage. But it you choose the wrong option in the Ubuntu installer, like "Erase the entire disk..." you could accidentally wipe windows. Always back up your important data first, just in case. You should have a backup anyway of course.

The easiest way to do it is to use the Windows disk manager to make some free space - un-partitioned space, and then tell the Ubuntu installer to use the largest free space. It will then create and format the partitions it wants in that space.

---

