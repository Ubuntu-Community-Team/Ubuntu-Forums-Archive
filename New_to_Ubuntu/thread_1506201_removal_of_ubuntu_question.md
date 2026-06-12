---
title: "removal of ubuntu question"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2010-06-10
So I installed ubuntu on someone's computer for them to try for a while.  They've decided it's not for them.  So how do I go about getting rid of it?  I didn't install with wubi.

I know that I can just delete the partitions from within windows 7 and the OS itself will be gone, but what about dealing with GRUB?  What do I need to do to make it boot straight into windows and ignore GRUB?

---

### Post by anewguy on 2010-06-10
According to the web, this still works with Windows 7 as well:

search the net for a free download called "mbrfix".  Download and unzip it while booted in Windows, read the htm file for usage info, the run it.  This will replace the mbr so that grub isn't there.  After that you can just remove your linux partitions.

Dave ;)

---

### Post by Mark Phelps on 2010-06-10
Another approach, which I recommend, is that you do the following:
1) boot into Win7 and use the Backup function to create and burn a Win7 Repair CD
2) Boot from the Repair CD, select command mode, and enter "bootrec.exe /fixmbr".

That will replace the MBR on your drive with one compatible with Win7.

For more info, see the link below:

[http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

After that, you should be able to boot directly into Win7 with no problems.

---

