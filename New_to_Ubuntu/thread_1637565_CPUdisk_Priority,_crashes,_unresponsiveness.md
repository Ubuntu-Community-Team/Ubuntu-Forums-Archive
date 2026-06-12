---
title: "CPU/disk Priority, crashes, unresponsiveness"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by alayoyo on 2010-12-04
From time to time a program will do a "slow crash". Everything gets SUPER laggy, lots of disk access, and the UI is too unresponsive to close the program or gracefully reboot. It isn't frozen: i can move a mouse to a location on the screen if you keep moving it for a 45 seconds. My computer is pretty new, 3 cores, 4gigs ram, etc. I'm not running a server, or background crysis or anything.

It seems to be programs which require disk access, such as running Disk Usage Analyser. 

Is there a way to lower priority for such things? In generaly Ubuntu seems less reliably able to keep the interface programs running as compared to my old xp box, where a ctr+atl+del and task kill was very usable. I have tried keeping system monitor and a terminal open but even switching programs is not available even waiting ~45 minutes.

I would prefer the general order of priority to be
UI and 'emergency' programs which would let me shut down a program gone awry>
web browser>
office apps, photo editor, etc>
file sharing>
utility programs> 
file operations from nautilus like moving media file to a different disk

but it seems the reverse is the case ATM.

any advice?

EDIT: For anyone who runs across this thread, I believe this is the VLC memory leak problem, as mentioned here: [http://forum.videolan.org/viewtopic.php?f=13&t=67478&start=30](http://forum.videolan.org/viewtopic.php?f=13&t=67478&start=30)

---

### Post by Rhubarb on 2010-12-04
I can't say I've tried this fix from experience, as I've got a nice quick SSD here.

But, it could be your Linux kernel giving too much priority to disk io / other processes.

There was a fix posted for just such a problem a few weeks back.
There's 2 ways to apply the fix:
[LIST]
[*]One is to patch / download a newer Linux kernel with the changes applied.
[*]The second is add a few lines to your ~/.bashrc file.
[/LIST]

I've just done a somewhat random search for relevant threads that should point you in the right direction:-
[Alternative to 200 line kernel patch]("http://ubuntuforums.org/showthread.php?t=1625233")
[Alternative To The 200 Lines Kernel Patch ]("http://ubuntuforums.org/showthread.php?t=1625046")
[~200 line kernel patch dramatically improves desktop performance ]("http://ubuntuforums.org/showthread.php?t=1623042")

If however your computer seems to slow down considerably regardless of disk io / cpu usage for ~ 1min at a time randomly, and you've got an nvidia graphics card, I recommend you download and install the latest nvidia drivers off nvidia's website (driver 260.19.21 works for me).

Hope one of those solutions does the trick for you.
- Otherwise you can play around with different task schedulers for linux (such as BFS) - which I have no experience with.

---

### Post by alayoyo on 2010-12-04
Hm, that might be it; it is specific to I/O. I think i will wait for the updated kernel for the improvement.

thanks.

---

