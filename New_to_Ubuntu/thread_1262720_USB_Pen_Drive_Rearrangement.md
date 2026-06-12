---
title: "USB Pen Drive Rearrangement"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Matuku on 2009-09-10
I've recently put a copy of Ubuntu on my USB drive so I can boot into it on any computer if needed. However it, as of course it would, has cluttered up the root of the drive with folders, etc. I use the drive for file storage as well and this is a pet peeve of mine that the root folder doesn't look tidy. I was wondering if there was anyway to move it all into a folder or whether that would seriously mess up the ability to boot.

---

### Post by bumanie on 2009-09-10
As long as you are using grub-legacy on the usb drive,[ this]("http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_") may help

---

### Post by Matuku on 2009-09-10
Hmm, but this would only move the boot option to another partition, not the main files, folders, etc. Or am I missing what you're getting at?

---

### Post by bumanie on 2009-09-10
Sorry, I think I missed your point. I was thinking that you were after a separate boot partition, but I guess not. Sorry I got on the wrong track. If you want a separate /home where all the files can be kept, away from the /root files, this would be possible, but is easier to arrange during initial installation. You cold look at [this]("http://www.psychocats.net/ubuntu/separatehome") and see if it is what you are looking for.

---

### Post by Matuku on 2009-09-10
I don't think I explained the issue very well, sorry about that; it's basically that the USB Drive now looks like a mess when opened in Windows (or any Linux system other than the one on the USB drive itself) due to all the files and folders that Ubuntu creates so it can run. I was just wondering whether, if I moved all of those folders from "/" to, say, "/Ubuntu/" on the pendrive whether this would mess up the ability to boot from it (I'm guessing yes) and if so what I would need to correct it. It's more an aesthetic than practical issue; I just don't like opening up the pendrive and seeing so many files, etc. Just a pet peeve.

I'm basically looking to make it be:
/Storage      (where I store all my personal files)
/Ubuntu       (where all the things needed to boot ubuntu would be)

Rather than, as it is now:
/Storage
/.disk
/drivers
/casper
/isolinux
.
.
.
on and on

---

### Post by ukripper on 2009-09-10
yes this would indeed mess up the ability to access root partition and is not recommended action.

---

### Post by Matuku on 2009-09-10
Another option I guess would be to partition it so one is storage and one is ubuntu...

---

### Post by bumanie on 2009-09-10
I think want you want would destroy your ability to boot from the usb drive - a separate / and /home would help reduce the clutter a little, other than that, I can't see what else you can do whilst still keeping the usb drive bootable.

---

