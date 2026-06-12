---
title: "Installation and partioning of Dual Boot installation."
date: 2010-12-30
forum: New to Ubuntu
---

### Post by OldBoy44 on 2010-12-30
Hi all,
I have purchased a C.D. of Ubuntu 10.04 which should arrive in a few days. I am a complete newbie and a little confused about a dual boot installation. I intend to follow the advice for manual partitioning as in -  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

1. I am right in assuming that following that method would install a home partition?
2. What in simple instructions do I have do do to finalize the installation after installing the partions. I am not sure what to do about the Boot Manager. The article quotes Vista - I have X.P.

After having a dual boot for a few months, I may well choose to go for a complete install.
3. Would my Ubuntu files be transferable to the new installation?

Thanks very much,  :)

---

### Post by d3ngar on 2010-12-30
Hi,

In answer to 1) - Yes, that should do it. It's actually very easy to install Dual Boot. I have had it for years before finally moving to an all Linux.

Here are some things to consider:
 - Install Windows first on a small partition
 - then install Ubuntu on another small parition
 - create a third partition (preferably NTFS) that you can access as a 'file drive' for both OS and put all your files in there. (NTFS doesn't limit files to 2GB and can be accessed by both Linux & Windows)

2 - You won't normally have to play around with the boot manager if you install it the Windows first way. GRUB is the default boot loader for Ubuntu and you should be able to install that from guides on the web.

3 - You won't have to do a 'complete install'. You simply delete the Windows partition and merge the free space into the Linux / file drive paritions as you please. 'gParted' is the programme you want to have a look at. Pretty easy to use, I would think.

Best,
Chris

---

### Post by OldBoy44 on 2010-12-30
Thanks very much for your help Chris,

Am I right in saying GParted can be accessed on the live Disk?

Cheers,  :p

I have just found a lot of help at - [http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)

I will mark this thread as solved.

  :popcorn:

---

