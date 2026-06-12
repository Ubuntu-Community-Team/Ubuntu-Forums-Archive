---
title: "Question about removing Ubuntu from a dual boot machine"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by jmundinger on 2009-09-30
Recently, I began to experiment with Linux.  I had a loptop that was found new life as my learning tool.  Previously, I had cleaned it up and, when reinstalling XP had partitioned the hard drive.  Then, I put Debian/Lenny in the second partition.  Having done that, I decided that I didn't need XP on that machine and, so I deleted the partition in which Windows had been installed and used that space to install Ubuntu 9.04.  This was working well for me - comparing the differences between the two systems and getting familiar with working in the terminal window.  Unfortunately, all this was more excitement than the old laptop could handle.

But, I liked Ubuntu enough that I wanted to keep working with it.  So, I decided to install Ubuntu on my desktop so that I could continue getting familiar with it.  The desktop has two hard drives (part of my solution to a previous major system failure).  I had the second hard drive partitioned, with XP installed in a small partition (for use only in the event of another crisis) and the rest of it as space for redundant backups.  I deleted that partition and used it for the Ubuntu installation and everything seems to be ok.

Now, I have a question - that I probably should have asked before I gave the jaunty jackalope a new home.  What happens to the MBR if I either uninstall Ubuntu or if I use the disk manager in Windows to delete the partition in which Ubuntu has been installed?  I have no plans to remove Ubuntu but am curious to know the implications in the event that I did.

---

### Post by pawhtiobo on 2009-09-30
Hi :)

If you remove Ubuntu, Grub will not show or give an error, you will need de XP CD, boot the CD, use the recovery console, boot in to the XP instalation with the administrator password and execute the command **fixboot** and **fixmbr**, reboot...everyting should be fine :)


see ya...

---

### Post by jmundinger on 2009-09-30
Thanks for the prompt reply.

> **pawhtiobo said:**
>  If you remove Ubuntu, Grub will not show or give an error, 

I thought that would be the case

> **pawhtiobo said:**
>  you will need de XP CD, boot the CD, use the recovery console, boot in to the XP instalation with the administrator password and execute the command **fixboot** and **fixmbr**, reboot...everyting should be fine :)

For some reason, that answer does not give me a lot of confidence.  The few times that I have tried to use it, the recovery console didn't seem to want to do much.

If your suggestion didn't work, I suppose that a person could install XP to the partition in which Ubuntu had been installed and that would create a new MBR??

---

### Post by bumanie on 2009-09-30
> If your suggestion didn't work, I suppose that a person could install XP to the partition in which Ubuntu had been installed and that would create a new MBR??If I understand your premise, windows would probably not be too happy with that. Windows works best as the first OS on the first hard drive, it is possible to get it to boot from other areas, but it much more difficult than if windows is as described previously. By the way, the method described by pawhtiobo does work fine. There is also super grub disk that can re-write a windows compatible mbr if windows console doesn't work for some reason.

---

### Post by starcannon on 2009-09-30
> **jmundinger said:**
> 
For some reason, that answer does not give me a lot of confidence.  The few times that I have tried to use it, the recovery console didn't seem to want to do much.


In this case, Windows Recovery Console, and the fixboot and fixmbr command do work as expected. 

+1 to the solution, I have personally used this same solution, and it does indeed work as intended.

---

