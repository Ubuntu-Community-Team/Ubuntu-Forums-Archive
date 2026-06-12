---
title: "What filesystem should I use?"
date: 2005-09-23
forum: Networking &amp; Wireless
---

### Post by winburne on 2005-09-23
Warning:  Noob asking questions!

On a fresh ubuntu install, I just installed a new HDD and am ready to format, mount, install/turn-on samba, etc.  My main goal is to have this machine be a fileserver for other (WinPCs) on my network - music, pictures, video, etc. 

I want to be able to access the drive later should I move it to a WinPC, so I think I should stay with FAT or NTFS.  Does this sound OK?  (I want to be able to read & write from any PC.)

Any better solutions?  Pros, cons?

Thanks for the help.
-Rob

---

### Post by mlomker on 2005-09-23
> Any better solutions?  Pros, cons?


Vfat would be best, then.  NTFS is read-only on Ubuntu.

There are tools that let you use an ext2 formatted drive on windows:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by winburne on 2005-09-23
Thanks, mlomker.  As you can see I finally got my install problems worked out (new mobo & ram).  On to step two...

Would you recommend ext2/3 over vfat?  [With that tool you mentioned, I'd be happy to use one of those - I like the idea of journalling and permissions.]

New Qs:
1) I would like to just create one partition (250GB) - maybe I need to use ext3?
2) Can I use the linux file permissions with samba to regulate WinUsers?

Thanks again - to the whole community.

---

