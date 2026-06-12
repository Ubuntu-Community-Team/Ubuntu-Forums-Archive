---
title: "if i swap back to ext3, will my system be bootable again?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-10-30
in my previous post i told of how i changed the file extension by mistake, now im asking, if i used Gparted Live CD to change th partition back to EXT3, would it be bootable again...or is downloading the 9.10 iso still the best idea?

---

### Post by QIII on 2009-10-30
If you changed, modified, added any file since the time you went to ext4, it would be in ext4 format and I suspect you would be buggered three ways from Sunday going back to ext3.  Maybe not.

If you upgraded to ext4 from ext3, you are OK.  All those files that were there under ext3 are still in ext3 format.  But ext4 is backwards compatible, so those files are still useable.

If you want to, you can update to GRUB2, which will have you with the two most noticeable changes (in terms of what you might see without worrying about the changes to system files) that come with Karmic.

That way, if you choose to upgrade to Karmic, you'll be all set.

(I'd still recommend a fresh install.  The consensus of most of us who have done this a few times is that upgrades are more problematic than fresh installs.)

BACK UP YOUR /HOME PARTITION WHEREVER IT LIVES before you do anything, by the way.

I would still recommend a fresh install, particularly if you have a separate /home partition.  If you don't, I would still recommend a separate /home partition.  Just set up your new partitions and create a /home partition.  It should be ext4 by default, but check it to be sure.  

Restore your /home partition.

I'm not sure, but I believe that the files in your old home partition, when put back into your new ext4 /home partition, would be put there in ext4 format.

Hmmm.   Something for me to research...

---

### Post by kansasnoob on 2009-10-30
Before making any more changes the first thing to do is to see what's there!

Boot the Live CD and when you're in the live desktop post the output of:

```
sudo fdisk -l
```

After that we'll figure out what partition to mount and chroot, then we can use the "ls ~" command to see what's readable!

---

