---
title: "Loading ndiswrapper module at boot causes problematic gnome startup"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by Cjmovie on 2008-07-05
The problem here is similar, but different, from those listed in other threads that may come up related to this one.

I use ndiswrapper to get access to my wireless card (a D-Link G510 PCI card; it's revision A, the Marvell chipset w8300). It works, for the most part, rather well. It's easy to get running, doesn't complain, and I can connect to any wireless network I need to. So after getting it to work, I installed the aliases and modprobe config, etc. (-m, -mi, -ma options for ndiswrapper control program).

However, trying to start the computer with it set to be loaded automatically by modprobe causes problems when starting gnome. After logging in and waiting a minute or so, an error about gnome-settings appears. It says the last error was related to no reply from something else, that themes etc. will probably not work. The dialog appears stuck to the top left of the screen with no window decoration, and the "OK" button on it is not clickable. The mouse cursor is the default X cursor (as in, the "X" shape from the X system). Even after leaving for a relatively long time (an hour or so) gnome still does not load. The only things visible are the error message in the window, a gradient background, and the mouse cursor. The mouse does react to movement, but not to button presses. Also, attempting to change to a virtual console and use sudo or certain other commands (such as ifconfig or iwconfig, or modprobe) causes the console to freeze. The only way to unfreeze it is to kill bash from another terminal.

Renaming the ndiswrapper.ko module to .ndiswrapper.ko to force modprobe into not being able to load it allows a normal boot, and then renaming it after boot and modprobe-ing it into the kernel allows it to work. Problems only show up if it is loaded at startup. For the time being, I have adopted unloading and renaming it at the close of each ubuntu session. I then change the name back and reload it after a successful login.

The problem occurs with both -16 and -19 variants of the current kernel version in 8.04 (2.6.24-XX-generic). The system is fully up to date and no other problems are visible. Any ideas on fixing?

Thanks,
CJ

---

### Post by Cjmovie on 2008-07-06
After a bit more searching, I seem to have found that sudo uses sockets for it's authentication. Based on this, I believe that the issue has to do with the ndiswrapper module messing up with all system sockets somehow. This would explain the appearance of the gnome-settings error as well, as this relies on local socket connections to work.

So it seems the issue is ndiswrapper is messing up sockets of all types. Any ideas?

---

### Post by malignor on 2009-06-23
> **Cjmovie said:**
> After a bit more searching, I seem to have found that sudo uses sockets for it's authentication. Based on this, I believe that the issue has to do with the ndiswrapper module messing up with all system sockets somehow. This would explain the appearance of the gnome-settings error as well, as this relies on local socket connections to work.

So it seems the issue is ndiswrapper is messing up sockets of all types. Any ideas?I'm having exactly the same problem.
This is also discussed, **but never resolved**, in numerous other threads.

[http://ubuntuforums.org/showthread.php?t=875955&highlight=W8300]("http://ubuntuforums.org/showthread.php?t=875955&highlight=W8300")
[http://ubuntuforums.org/showthread.php?t=1194772&highlight=W8300]("http://ubuntuforums.org/showthread.php?t=1194772&highlight=W8300")
[http://ubuntuforums.org/showthread.php?t=885847&highlight=W8300]("http://ubuntuforums.org/showthread.php?t=885847&highlight=W8300") (look for earl79)
[http://ubuntuforums.org/showthread.php?t=993275&highlight=W8300]("http://ubuntuforums.org/showthread.php?t=993275&highlight=W8300")

After reading all these (and starting one of those myself, with no replies), I'm getting this sinking feeling...

---

