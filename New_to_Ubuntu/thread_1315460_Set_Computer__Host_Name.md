---
title: "Set Computer / Host Name"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Hendersons Relish on 2009-11-05
Just installed 9.10 & can't see where to set the computer's name! HELP!

---

### Post by Sarmacid on 2009-11-05
The name should be in /etc/hostname

---

### Post by Hendersons Relish on 2009-11-05
Sorry - I'm a newbie - is there a way to set this through the GUI interface please?

---

### Post by Barriehie on 2009-11-05
/etc/hostname is a simple text file.  Not aware of a GUI way to set it.  
```

Accessories > Terminal > gksudo gedit /etc/hostname

```
type in the hostname - ctrl-s (save) ctrl-w (close) ctrl q (quit)

---

### Post by nikhilup on 2009-11-05
Go to System>Administration>Users and Groups
There you can change the computer name.

---

### Post by Hendersons Relish on 2009-11-05
Many thanks Sarmacid & Barriehie - I'm a new convert from Windows (sorry) so have gotten out of the command-line habit.

Your pointers have worked - many thanks!

PS If anyone does know the way to do it through the GUI......

---

### Post by Hendersons Relish on 2009-11-05
Nikhilup - I can't see where you set the computer name where you've pointed - any more help please?

---

### Post by RealG187 on 2009-11-19
Did Ubuntu always use /etc/hostname?

My Comptia Linux book says to use "/etc/sysconfig/network" Fedora uses that. But the file there has more than the hostname, it has a line with "NETWORKING=yes"

---

### Post by lisati on 2009-11-19
> **RealG187 said:**
> Did Ubuntu always use /etc/hostname?

My Comptia Linux book says to use "/etc/sysconfig/network" Fedora uses that. But the file there has more than the hostname, it has a line with "NETWORKING=yes"

The /etc/hostname sounds right, I think it's also stored in another file somewhere as well that will need to be checked. (I'm in Vista at the moment doing a defrag so can't check quickly). I also remember seeing a GUI option on one of the menu items a few versions of Ubuntu ago, but can't remember exactly where at the moment.

---

### Post by RealG187 on 2009-11-20
I think it was under Administration --> Network

But 9.10 has no option to change the hostname.

---

