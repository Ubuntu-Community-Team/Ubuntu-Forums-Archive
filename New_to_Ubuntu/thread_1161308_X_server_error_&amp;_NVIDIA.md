---
title: "X server error &amp; NVIDIA"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-05-16
Hi all,

I upgraded a week ago to Jaunty from Hardy (via Intrepid) and everything seemed to be working well.  Yesterday, my husband logged out and received a message stating ```
Could not start the X server (your graphical environment) due to some internal error.
Please contact your system administrator or check your syslog to diagnose.
In the meantime this display will be disabled .  Please restart GDM when the problem is corrected.
```It's taken me until now to get the system back up and running; an unconnected (I assume) problem was preventing Ubuntu from loading.

I rebooted in recovery mode and chose the fix for graphics problems, which gave me a brief message about over-writing customized configuration files.  My desktop display is now off-centre. There's a black band down the left of the screen, and the right-hand side is missing; I can only just access the corner of the "Shut Down" icon and any scroll bar is off the screen.

NVIDIA X Server Settings says ```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```Before I do this, how can I check whether this is what caused the original problem?  The error message told me to check my syslog, but I'm still such a newbie I don't know where to find it, or what to look for if I do locate it!

I'd be most grateful for any assistance.

---

### Post by SuperSonic4 on 2009-05-16
Did you try ```
sudo nvidia-xconfig
``` in a terminal? Not sure about your original problem - sometimes it solves itself out with a reboot. If you want to restart gdm first then it would be ```
sudo /etc/init.d/gdm restart
```

---

### Post by Bearly Able on 2009-05-16
Thanks, SuperSonic4.  It's not that I don't know how to run nvidia-config, just that I don't want to do it if it's going to land me back with the same problem again.  I'd like to understand why things went awry in the first place.

---

### Post by SuperSonic4 on 2009-05-16
I can't be sure, did you use the Hardware Drivers first time around?

---

### Post by Bearly Able on 2009-05-16
I'm pretty sure I was using them with Hardy, so presumably the upgrade continued to use them.  The fact that the display is askew now suggests I must have been; running from the Live CD gives me the same lop-sided display.

[Edit] I've just thought to look at the Hardware Drivers, which shows version 180 as the recommended version, and has a message at the bottom that "A different version of this driver is in use".  Any help?

---

