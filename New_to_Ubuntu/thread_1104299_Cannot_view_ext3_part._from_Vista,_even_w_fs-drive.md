---
title: "Cannot view ext3 part. from Vista, even w/ fs-driver"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by rift321 on 2009-03-23
Hardware: new IBM T400 laptop

Installed: Dual-boot Vista Business x64 & Ubuntu 8.10 amd64

I installed FS Driver on my new laptop (both in non-compatibility-mode, and also in XP compat. mode), but Vista still does not see my Ubuntu EXT3 partition at all, even from disc manager, and even after reboots.

Any thoughts?

---

### Post by kanikilu on 2009-03-23
FWIW, I wasn't able to get this working either. I have Vista Home Premium 32bit and Ubuntu 8.10 32bit. For now I'm just using a shared/common FAT32 partition...not a very pretty workaround, but it'll do for now.

---

### Post by egalvan on 2009-03-23
From the fs-driver website...

[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)

 [B][I]Large inodes

The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes.
 Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and 
create the Ext3 file system again.
 Give the mkfs.ext3 tool the -I 128 switch.
 Finally, restore all files with the backup.[/I][/B]

Let's all "tip" our software authors!

ErnestG

---

### Post by rift321 on 2009-03-23
Thanks!  looks like this is solved...

---

### Post by c0mp13371331337 on 2009-04-17
I just recently installed Vista Ultimate x64 and was burned by the fact that ext2ifs doesn't support inode sizes larger than 128 bytes.  So far, the closest thing I've been able to get working (aside from reformatting with a smaller inode size or creating a separate fat32 partition) has been to install Total Commander ([http://www.ghisler.com/](http://www.ghisler.com/)) and the ext2 + Reiser plugin for it ([http://www.ghisler.com/plugins.htm#filesys](http://www.ghisler.com/plugins.htm#filesys)).  Gotta use a completely separate file browser to browse through your linux drives, and it only supports reading, not writing, but other than that it works fairly well.

---

### Post by nimonika on 2009-05-19
> **rift321 said:**
> Thanks!  looks like this is solved...

Did you manage to actually get this working. I am struggling with a similar problem.

---

### Post by Martiini on 2009-10-23
> **c0mp13371331337 said:**
> I just recently installed Vista Ultimate x64 and was burned by the fact that ext2ifs doesn't support inode sizes larger than 128 bytes.  So far, the closest thing I've been able to get working (aside from reformatting with a smaller inode size or creating a separate fat32 partition) has been to install Total Commander ([http://www.ghisler.com/](http://www.ghisler.com/)) and the ext2 + Reiser plugin for it ([http://www.ghisler.com/plugins.htm#filesys](http://www.ghisler.com/plugins.htm#filesys)).  Gotta use a completely separate file browser to browse through your linux drives, and it only supports reading, not writing, but other than that it works fairly well.

This totally works!!

---

