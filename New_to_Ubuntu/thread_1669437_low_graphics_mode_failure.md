---
title: "low graphics mode failure"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by gandalf69 on 2011-01-17
10.04 has been running OK with ATI video card with default Ubuntu driver. 
Today on startup I get a message about running in low graphics mode...Run Ubuntu ...for one session....Stand by one minute while display restarts. After that the screen checks get as far as ....Checking battery state... and hangs.
So there is no access into Ubuntu. 
 I used Synaptic to remove Evolution yesterday, could that have deleted something needed?
I can boot from the live cd.
Do I need to re-install?

---

### Post by cariboo on 2011-01-17
Boot in recovery mode, and once at the menu select Failsafe X, and press enter, you should be taken to the desktop.

To get to the grub menu if you don't see it hold down the shift key during post.

---

### Post by gandalf69 on 2011-01-17
> **cariboo907 said:**
> Boot in recovery mode, and once at the menu select Failsafe X, and press enter, you should be taken to the desktop.

To get to the grub menu if you don't see it hold down the shift key during post.


Thanks. Recovery mode? It is not an option, only F2/Del, F6, F11 are available. 
Holding Shift down during POST caused Grub Loading to appear once out of many tries. But then it just reverted to the low graphics mode. So I didn't get to find out what GRUB is. 
 
There is a recent post regarding restoring configuration that mentioned saving the contents of the HOME/name/folders. Mine has lots of folders with X on them.

---

### Post by gandalf69 on 2011-01-18
After reading a heap of other related posts, I attempted to remove  xorg.conf
The result was:
rm: cannot remove '/etc/X11/xorg.conf': No such file or directory.

Time to re-install?

---

### Post by gandalf69 on 2011-01-18
SOLVED 

see **Recover my system + repair to get GUI**

---

