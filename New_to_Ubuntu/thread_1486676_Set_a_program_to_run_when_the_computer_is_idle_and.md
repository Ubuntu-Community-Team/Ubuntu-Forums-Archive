---
title: "Set a program to run when the computer is idle and to exit nicely when user returns."
date: 2010-05-18
forum: New to Ubuntu
---

### Post by brallan on 2010-05-18
Anyone know of a way to get something to start up when the computer goes idle for more than 5 minutes (or when the screensaver starts) and then exits cleanly when done or when a user returns, the screensaver turns off, or the computer is no longer idle? I can't find anything inside of the screensaver, power management, or startup programs. 

I guess this might have something to do with init.d or runlevels? They are things of which i have a vague notion.  If there is no GUI, please be gentle. I know how to use the terminal but I have never written (or used) a shell script.

Basically, I am interested in running an rsync backup to a network drive, which will require first mounting the drive, then making a copy to it, as described in [this post]("http://www.uluga.ubuntuforums.org/showthread.php?t=1032394"). 

i would also need to know if there is a way that all this can exit cleanly, like say finish the file it is currently writing before stopping rsync, and then unmount the network share before exiting.

---

### Post by brallan on 2010-10-11
bump

---

