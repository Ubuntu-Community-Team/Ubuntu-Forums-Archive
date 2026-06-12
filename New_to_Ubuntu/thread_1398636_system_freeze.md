---
title: "system freeze"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by norm_lin on 2010-02-04
I just installed ubuntu 9.10 for the second time.  The first time my screen and mouse froze so I erased the hard drive and reinstalled with a new disk.  Same problem.However, when I use the live disk in lieu of installation the problem disappears.After installation I seem to have about one minute before the freeze to work with.  I'm trying to learn Linux but with no experience with this OS. I'm helpless.  If anyone cares to send simplified helpful they would be appreciated.  BTW this is a home built computer running an Intel e220 dual core CPU with 2GB of ram.  Also tried installing Fedora 12  and did not experience these problems.  This is coming from the same computer using separate hard drive windows.

---

### Post by chaanakya_chiraag on 2010-02-04
First of all, try to use Alt-PrintScreen REISUB instead of holding the Power Button.  Also, does Ubuntu work again after logging on or does it fail to boot?  When the system locks up, press Ctrl-Alt-F1 to enter a terminal.  Login and type ```
dmesg
```Note down the last lines and copy them into this forum.

---

### Post by *Raz0r* on 2010-02-04
Disable Compiz Fusion or Visual Effecrs.
System-Preferences-Appearance-Visual Effects and select None and close it. That should stop it your computer from freezing.

---

### Post by norm_lin on 2010-02-05
> **chaanakya_chiraag said:**
> First of all, try to use Alt-PrintScreen REISUB instead of holding the Power Button.  Also, does Ubuntu work again after logging on or does it fail to boot?  When the system locks up, press Ctrl-Alt-F1 to enter a terminal.  Login and type ```
dmesg
```Note down the last lines and copy them into this forum.

Thanks for input. ctl alt f1 won'y work. screen freezes completely.  
suspect I may have harddrive problem as well.  Will get new drive and try again. Again thanks for the input

---

### Post by chaanakya_chiraag on 2010-02-05
Hmmm...it seems like the whole system is freezing up, which either indicates a Kernel Panic or a hardware problem.  If it really were a Kernel Panic, the system would not boot again, which means it's probably a hardware problem.

---

### Post by sheem on 2010-02-05
Not sure if this will help but when I had a freeze problem I removed my video card,dusted it off, reinserted making sure it was fully seated and no more problems. But I see you had no problems with the live cd or the other distro.....just an option that's all

---

