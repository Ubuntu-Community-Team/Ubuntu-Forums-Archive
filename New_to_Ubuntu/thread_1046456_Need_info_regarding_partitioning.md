---
title: "Need info regarding partitioning"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-01-21
I've been using ubuntu through wubi to try it out and like it a lot, but it seems to be a slower than what it should be. I think it is because it is running on top of windows and my computer is about 4 yrs old. Am I right?

slowdown times are when using Add/Remove..., Synaptic, videos and large applications.

Will installing ubuntu directly on the disk solve the lagging?

For the partition: I defragmented my disk under XP but some of the files aren't placed on the left and stay on right (on the disk graph). Will they be erased if when installing, on the partition menu, I use all the right side for the ubuntu partition?

Also, if I partition my disk and decide I don't want ubuntu, can I reformat my disk with only one partition for XP?

Sorry it's a long one... Thank you!

---

### Post by kestrel1 on 2009-01-21
Never used the Wubi install, but from what I understand it should increase the speed of Ubuntu if it is on it's own dedicated partition.
Not sure about the second part of your question, maybe someone else will answer that.
If you decide you didn't want Ubuntu You can format it's partition/partitions or give the space back to Windows. The only thing is that Grub will still be on your MBR, so you would want to restore the Windows boot loader in the MBR. From memory this can be done from a recovery console & typing: ```
fixmbr
```
This link gives more info:
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---

### Post by ibuclaw on 2009-01-21
> **sylvainrb said:**
> I've been using ubuntu through wubi to try it out and like it a lot, but it seems to be a slower than what it should be. I think it is because it is running on top of windows and my computer is about 4 yrs old. Am I right?

slowdown times are when using Add/Remove..., Synaptic, videos and large applications.

Will installing ubuntu directly on the disk solve the lagging?

For the partition: I defragmented my disk under XP but some of the files aren't placed on the left and stay on right (on the disk graph). Will they be erased if when installing, on the partition menu, I use all the right side for the ubuntu partition?

Also, if I partition my disk and decide I don't want ubuntu, can I reformat my disk with only one partition for XP?

Sorry it's a long one... Thank you!
Wubi, as I understand it is a virtual filesystem seated ontop of another filesystem. So it is my guess that yes, installing Ubuntu for real will solve your issue with loading large applications. Though I've never used Wubi, so I can't really say how much different it is to the actual install.

And in all my experience of using the Windows Defragmenter. I can honestly say that I tend to ignore it now. It doesn't even give a good representation of your filesystem (Your hard drive is a circle, not a line).

As long as you have ran the defragmenter once, this should be sufficient without you needing to worry. The only time when resizing an NTFS partition has ever been a problem has been with Vista (to which it is recommended that you use Vista's own resize utility to shrink it).

As with partitioning, I recommend that you use the partitioning utility on the LiveCD to shrink the NTFS filesystem, (make about 15-20GB of empty space) and install Ubuntu in the free space.

Regards
Iain

---

### Post by -kg- on 2009-01-21
I'm making the assumption that you have XP loaded, as you said the computer is 4 years old:

> For the partition: I defragmented my disk under XP but some of the files aren't placed on the left and stay on right (on the disk graph). Will they be erased if when installing, on the partition menu, I use all the right side for the ubuntu partition?

No, they won't.  During the resizing process the files that are in the target area (i.e., the area that you are trying to free by resizing) will be moved to the left into free space inside the partition.  The same happens when you move a partition from one location to another.  It will take more time to complete the operation, since the files must be moved to a new location, but it won't delete them.

> Also, if I partition my disk and decide I don't want ubuntu, can I reformat my disk with only one partition for XP?

You can reverse the above process, deleting the Ubuntu partitions and expanding the existing partition back into that space, using the whole disk.  Be aware, though; you will still have GRUB as the bootloader.  This will be fine, but if you happen to want the Windows bootloader instead, you will have to reinstall it.

I'm pretty sure that GRUB can be left as the bootloader in the MBR, though.  You'll probably have to do a little modification on it, making Windows the default OS to boot (since you will no longer have Linux at that point), and you might want to decrease the timeout so as to quickly boot Windows rather than having to click it, but it should work fine.  Otherwise, restoring the Windows bootloader isn't overly difficult.

For a good explanation of the Partitioning process, see:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by sylvainrb on 2009-01-21
specs for my laptop: 
~1.7GHz for processor
Dual 256MB of RAM (512MB total?)
~50GB HD

Is that enough for ubuntu to run fine (meaning faster than XP)?

Doing a backup of Ubuntu will save all of my settings, programs/drivers installed, themes, etc... or will I have to redo everything after doing the partition?

Thanks for the previous help!

---

### Post by jerome1232 on 2009-01-21
Fine yes that should be fine, faster than XP? I doubt it, you have to remember XP is like 10 years old, it can run on lower spec'd systems than Ubuntu 8.10 with a full blown gnome install can.


If you want to get things more snappy I would actually recommend switching to xfce for you DE (Desktop Enviroment) or just using an alternate Window manager.

I personally use iceWM for my window manager and I guarantee you this machine could blow the socks off of windows xp when it comes to speed. (Login window to usable desktop is 1 second.)

---

