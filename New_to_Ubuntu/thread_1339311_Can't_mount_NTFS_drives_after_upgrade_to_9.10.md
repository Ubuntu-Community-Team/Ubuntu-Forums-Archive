---
title: "Can't mount NTFS drives after upgrade to 9.10"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-11-27
For some reason, I cannot access my NTFS drives any more since I upgraded to 9.10.

When I click on one of my NTFS drives, I now get the error message:
> **Could not mount [drivename]**
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

Does anyone have any idea what I should do? I've looked up the URL mentioned by the error message, but it's written in geek.

---

### Post by coffeecat on 2009-11-27
Hmmm. Must be one of these endless Jaunty > Karmic upgrade glitches that keep getting reported because NTFS partitions mount just fine in the four machines I've done fresh installs to.

I don't see that this will help but try marking the 'ntfs-3g' package for reinstallation in Synaptic. Although, tbh, it sounds as though something has gone wrong with the udev rules for automounting. Or is it hal? :? I can't keep up, and anyway that would be beyond me.

> **Roger Allott said:**
> it's written in geek.

:lol:

---

### Post by Roger Allott on 2009-11-27
> **coffeecat said:**
> 
I don't see that this will help but try marking the 'ntfs-3g' package for reinstallation in Synaptic.

It was worth a try, but as expected it didn't resolve the problem.

---

### Post by coffeecat on 2009-11-27
Well - I found something that *might* help. See post #4 in this thread:

[http://ubuntuforums.org/showthread.php?p=8187227](http://ubuntuforums.org/showthread.php?p=8187227)

Better get your geek/English dictionary out. :wink: But I see that devicekit-disks is the villain here, not hal or udev. :sigh:

The only other thing I can suggest is to boot up with the live 9.10 CD and see if you can mount the NTFS drives OK in that. If you can, then it was clearly a problem with the upgrade and you might want to consider a fresh install. I hate suggesting fresh installing because in theory everything is fixable, but.... Food for thought.

---

### Post by Roger Allott on 2009-11-27
> **coffeecat said:**
> Well - I found something that *might* help. See post #4 in this thread:

[http://ubuntuforums.org/showthread.php?p=8187227](http://ubuntuforums.org/showthread.php?p=8187227)

Better get your geek/English dictionary out. :wink: But I see that devicekit-disks is the villain here, not hal or udev. :sigh:

The only other thing I can suggest is to boot up with the live 9.10 CD and see if you can mount the NTFS drives OK in that. If you can, then it was clearly a problem with the upgrade and you might want to consider a fresh install. I hate suggesting fresh installing because in theory everything is fixable, but.... Food for thought.

Thanks for that, but I had to reboot my system and have just returned to the thread.

It would seem that Bill Gates is now writing code for Ubuntu, because the reboot fixed my problem. Well, sort of - fixed in a Windows-type of cobbled together way. I've now got 8 NTFS drives visible, and I seem to be able to read and write to 4 of them. The other 4 seem to be duplicates without their aliases.

---

