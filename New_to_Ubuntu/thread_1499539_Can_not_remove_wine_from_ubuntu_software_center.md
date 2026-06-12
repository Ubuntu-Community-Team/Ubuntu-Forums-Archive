---
title: "Can not remove wine from ubuntu software center"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by rudysuryanto on 2010-06-02
I want to reinstall playonLinux. First step, I want to remove playonLinux. But when I try remove playonLinux from ubuntu software center, appear message: the previous installation is not complete. Then playonLinux, wine can not remove from ubuntu software center.
Where is the problem?
Thank's.

---

### Post by goinglinux on 2010-06-02
> **rudysuryanto said:**
> I want to reinstall playonLinux. First step, I want to remove playonLinux. But when I try remove playonLinux from ubuntu software center, appear message: the previous installation is not complete. Then playonLinux, wine can not remove from ubuntu software center.
Where is the problem?
Thank's.

It may be that the installation of PlayOnLinux failed. You could try this:

Open a terminal, type (or copy and paste this text): 

[FONT="Courier New"]sudo apt-get update | sudo apt-get install -f[/FONT]

You will be asked to enter your password, then this should clear the failed installation and let you reinstall.

---

### Post by david.burlingame on 2010-06-02
System > Administration > Synaptic Package Manager

Then type "wine" in the search area without quotes

Right click on the version you would like to remove.  You should be able to install wine1.2 + wine1.2-gecko while you are there.

Hope that helps :)

---

### Post by Jakiejake on 2010-06-02
> **rudysuryanto said:**
> I want to reinstall playonLinux. First step, I want to remove playonLinux. But when I try remove playonLinux from ubuntu software center, appear message: the previous installation is not complete. Then playonLinux, wine can not remove from ubuntu software center.
Where is the problem?
Thank's.

Package Manager?

---

