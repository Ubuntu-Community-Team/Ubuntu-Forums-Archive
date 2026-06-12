---
title: "Qimo"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-08-30
Does anyone know if I can install QIMO alongside ubuntu (as you would with xfce etc) and just choose which to run at the login screen?

TIA

G

---

### Post by cariboo on 2010-08-30
You can install as many operating systems as you space for, grub2 will detect them all and add them to the boot menu.

---

### Post by GaryTheCat on 2010-08-30
I was hoping to install it as an option at the login screen once I'd selected Ubuntu from Grub - seems to work fine but if I'm honest, I'd like to be able to do it without the annoying xubuntu splash screen and login screens

---

### Post by GaryTheCat on 2010-09-01
bump

---

### Post by egalvan on 2010-09-01
> **GaryTheCat said:**
> can install QIMO alongside ubuntu (as you would with xfce etc)


Are you talking about 

*install QIMO alongside ubuntu*  as in a **totally distinct Operating System**? Such as Windows/SuSE/Fedora?


or

*install QIMO alongside ubuntu* as in a **different session**?  Such as Gnome/KDE/xfce?



>  and just choose which to run at the login screen?


The login screen will depend on how QIMO is installed.

In the first instance, GRUB will be the login screen that lets you choose OS's.

In the second instance, the Session Manager will be the login screen that lets you choose sessions.
Which session manager is working depends on which one your install has enabled
KDM or GDM or whichever...
this is a changeable option... as is the background/graphic.


From your description of the xfce screen, it sounds  as if you have a "session"-type install.
I don't recall at this moment where the session manager option is set.
Also, it **IS** possible to bypass/blank almost all the login screens and username/pasword prompts...
this will let your machine go from "power-on" to desktop without user interaction.
[B]BUT THIS IS A [COLOR="Red"]VERY UN-SECURE METHOD[/COLOR] OF RUNNING LINUX
[COLOR="Red"]AND IS NOT RECOMMENDED[/COLOR].[/B]
if the machine is not connected to the Internet, this is much less a problem, of course.

---

