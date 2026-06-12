---
title: "how to auto-mount Windows partition?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by bsmith1051 on 2009-11-05
I moved partitions around on my new Windows laptop, then installed Ubuntu 9.10 in a dual-boot configuration.  All that works fine (though GRUB2 stopped working at one point and needed to be reinstalled from the LiveCD?...)

My question is if there's a simple way to set the Windows partition to auto-mount.  I've done some searching and I know there's a way to edit config files to make this work, but shouldn't there be a simple graphical tool, too?  I was surprised Gparted didn't do it.  Is there some GUI I haven't found yet? 

Any suggestions are appreciated!

---

### Post by sisco311 on 2009-11-05
ntfs-config: [http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows")

---

### Post by Mark Phelps on 2009-11-05
Word of caution is in order ...

If you're going to auto-mount an MS Widows OS partition (especially Vista), would be best to mount it read-only, not read-write.

Mounting it read-write increases the risk of partition corruption, and should that happen, you won't be able to boot into the OS to run chkdsk to repair the filesystem.

Not saying it WILL happen, because NTFS-3G does a pretty good job of handling NTFS filesystems, but it's best to be careful to avoid problems.

---

### Post by bsmith1051 on 2009-11-05
> **sisco311 said:**
> ntfs-config: [http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows")
Thanks!  But does this require me to install a separate "NTFS-3G" driver?  Or, does it piggyback on the existing driver (which may be 'ntfs-3g' for all I know) ?

---

