---
title: "Howto disable CD frontpanel eject button?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by rbm0307 on 2009-11-09
Hi,  My 16 month old is very active and continually presses the frontpanel eject button on the CD drive follwed by tugging as hard as possible on the tray.  The machine is my MythTV frontend and, anticipating the next question, I can't move the machine out of reach of the boy. I need to disable this button execpt when I need to use it.

I realize that if a process is using the drive, ejecting the CD tray is prevented.  Is there a simple Linux command to issue that will occupy the drive, and that is easy to stop to regain control of the drive?  TIA.

Robert

---

### Post by jimmy the saint on 2009-11-09
You might try an apple style slot feeding drive.

---

### Post by LowSky on 2009-11-09
setcd

its in the repos or here
[http://packages.ubuntu.com/karmic/setcd](http://packages.ubuntu.com/karmic/setcd)

---

### Post by rbm0307 on 2009-11-09
Thanks for the suggestion Lowsky.  Setcd will manipulate CD flags that determine CD behaviour but it doesn't have an option to lock the drive.  The -l, -o and -c flags will not stop the frontpanel button from operating the tray.  In the end, it's not stopping the tray from opening.  I'm still searching for a solution.

> **LowSky said:**
> setcd

its in the repos or here
[http://packages.ubuntu.com/karmic/setcd](http://packages.ubuntu.com/karmic/setcd)

---

### Post by anewguy on 2009-11-09
Not sure there is going to be a software solution where the drive is empty or has a disk in but is not mounted and in use.  Disabling the eject hardware-wise is not the easiest solution - the switch is usually part of the circuit board - but if worse came to worse it may be a solution for you.  You then would need to use the little pin-hole to open the drawer, but this might keep the little one out as long as they don't see you putting something in the pin hole.  Not an elegant solution, but possible.

Dave :)

---

### Post by rygar on 2009-11-09
Solution is here:
[http://ubuntuforums.org/showthread.php?t=1167416](http://ubuntuforums.org/showthread.php?t=1167416)

basically, type "eject -i on" at the terminal to lock, "eject -i off" to unlock.

---

### Post by anewguy on 2009-11-09
I haven't checked the above thread, so this may be a duplicate of what rbm0307 is already pointing you to, but I did find this tool:

[http://cdctl.sourceforge.net/](http://cdctl.sourceforge.net/)


Dave :)

---

### Post by anewguy on 2009-11-09
In above post, meant to say "what Rygar is pointing you to" not "what rbm0307 is pointing you to".  In addition, Rygar has the simplest most elegant solution and it's already in your system.

Dave :)

---

