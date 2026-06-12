---
title: "Cannot logout successfully , please help me :S"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Dangger on 2009-09-15
Please help I cannot logout successfully to change user or session. It gets to 

*Checking battery state

and stays there for a long time until it goes to a black screen and eventually it says:

* Reloading system log daemon...

This problem is due to using the kdm display manager as default. It hangs the system when trying to log out. to solve it, partially, run

$ sudo dpkg-reconfigure kdm

and choose gdm as the default manager.

---

### Post by earthpigg on 2009-09-15
can you shut down and reboot normally?

---

### Post by Dangger on 2009-09-15
> **earthpigg said:**
> can you shut down and reboot normally?


Yes, and it only happened after I installed the KDE desktop and decided to keep it and removed gnome 

:S

---

### Post by Dangger on 2009-09-15
I have been able to replicate the problem. It is because of the kdm display manager. If it is chose as default it will prevent my machine from successfully logging out.

---

### Post by CampbellBoyd on 2010-05-05
I have a similar problem. I'm running 10.04. Hibernate does not work on my PC (and didn't with Windows XP) but not a problem. If I have more than one user logged on then switching user works fine but a logout causes a Black Screen of Death (at least its not blue). I'm not using the kdm display manager.

---

### Post by cojoco on 2010-06-26
I also *cannot* log out, I just get a black screeen.

I have this problem on *all four* of my AMD computers, one has ATI AGP card, two have NVidia PCI-E card, and one has NVidia on-board video.

All are running 10.04, and this problem has always existed since the first install.

I have been running Gnome, but I just tried with KDE, and this also has the same problem.

All have NVidia chipsets.

I can log into my computer via SSH from another and restart, but nothing I do from the keyboard allows me to select a TTY or another X session.

---

