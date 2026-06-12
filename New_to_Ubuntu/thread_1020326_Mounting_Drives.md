---
title: "Mounting Drives"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Spheric on 2008-12-24
Noob alert. I'm playing around with a fresh(ish) install of Gutsy Gibbon Ubuntu for the PS3 (version 8.10) on a friends PS3. Well, I've got it up and running, problem is that I followed an online tutorial for changing the screen resolution in my kboot.conf file, and dropped in a line

$ linux="/boot/vmlinux initrd=/boot/initrd.img video=ps3fb:mode:5 root=UUID-..."

Now when it boots it hangs up with a syntax error pertaining to the UUID-... as a syntax error. I was going to go back in through a livecd we have, and remove the UUID part of the code(should fix the problem right?) but I can't figure out how to properly mount the filesystem for the PS3. I have the options for ps3da, ps3da1 through to ps3da5 (2 not included) and can't get my live cd to pick up the filesystem.

How does one mount a PS3 drive properly through a 8.10 Ubuntu Live CD?

---

### Post by Xiong Chiamiov on 2008-12-24
[It seems]("http://ubuntuforums.org/showthread.php?t=893135") that the PS3 uses an encrypted FAT partition.  I don't know, however, about the partition that you created (I assume you created one when you installed Ubuntu?); it might just be ext3?

---

### Post by Spheric on 2008-12-24
> **Xiong Chiamiov said:**
> [It seems]("http://ubuntuforums.org/showthread.php?t=893135") that the PS3 uses an encrypted FAT partition.  I don't know, however, about the partition that you created (I assume you created one when you installed Ubuntu?); it might just be ext3?

Possibly.. I'll have to try it. 

I scanned with cat /proc/partitions
and it popped up with 

ps3da
ps3da1
ps3da3
ps3da5

The PS3 created the 10GB partition for the second OS, though, so I'm not too sure on what the filesystem looks like.

---

