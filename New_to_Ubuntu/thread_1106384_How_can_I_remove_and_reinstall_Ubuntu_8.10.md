---
title: "How can I remove and reinstall Ubuntu 8.10?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by billslink on 2009-03-25
Hello,
I installed Ubuntu a few weeks ago within  XP Pro, which was one of the options. I told it to allocate 15 gigs for Ubuntu. I am having all kinds of problems with this Ubuntu installation. Originally it said I needed a password just to get onto Ubuntu when I didn't recall ever setting one up. I finally worked through that problem with the help of people on the forum. Now I am unable to get my wireless working because it tells me the new password that I set up is not recognized as authorized for administrative functions, etc. With this in mind, I would like to just remove this installation of Ubuntu and reinstall it and hopefully I won't have all of these kinds of issues next time. I would much prefer to not have to wipe the disk and also reinstall XP Pro and all of the software I have loaded on the disk, as well. Pleased give me some direction to achieve this. Also, when I redo this istallation with the Ubuntu ISO CD, are there any other things I should do concerning partitioning choices this time to try to get it installed in a better way?  I am very interested in Ubuntu, but I am thinking starting over will likely be the easiest solution for someone as unfamilar with this operating system, as myself. Thank you in advance for whatever help I receive concerning trying to achieve this successfully.

---

### Post by B4RR13N705 on 2009-03-25
Just put de CD and reboot the pc, in the partition part, format the ubuntu partition and resize it if you want, the proceed with the instalation! :popcorn:

---

### Post by logos34 on 2009-03-25
> **billslink said:**
> Hello,
I installed Ubuntu a few weeks ago within  XP Pro, which was one of the options. 

You must mean Wubi.  Uninstall following [these instructions.]("http://wubi.sourceforge.net/faq.php#use")

Then insert the ubuntu install cd and choose either 'Guided' option (which will shrink XP for you) or 'Manual'.  The latter assumes you have already shrunk XP (which you can do beforehand on the live cd desktop (System>admin>partition editor).  Then you must specify minimum of / (root) and /swap partitions

---

### Post by justinram22 on 2009-03-25
Here is what i would do, but this is me.

1. I'm assuming you know how to boot from a CD?? Anyway, boot from your Ubuntu Live CD

2. Select english and follow the set-up to the partitining.

3. Ok, now here is an IMPORTANT Part, im assuming that you didn't mess up your hard drive and make many partisions? (sorry for spelling??) Anyway, i'll assume that you have 3 partitions.
    
    A. NSFT (I think that is windows? something close to that lol)
    B. Swap (Should be smallest)
    C. ext2 (should be 15 gigs worth)

4.  Just simply select the ext2 and do a guided, and there ya go, and this should still allow GRUB to reconigze XP.


*Notice* Sorry for the bad spelling! I'm only 13 but WAY into computers!

---

