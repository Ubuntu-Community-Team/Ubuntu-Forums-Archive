---
title: "Sessions and Configuration files"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-01-05
I starting having problems with my Xfce desktop. The panels from Gnome would appear on top of the Xfce panels. I was thinking of R&R the OS but instead this was sugested:
> 
Instead of a reinstall, you can add a new user and see whether that helps.
It sounds like your "sessions" and user configuration is "just a little messed up".
OK, I created a new user and that worked. Xfce is back to normal and Gnome works great also, the panels are back in their place. So what is my next step?

Is there a way to fix the user config file or should I just keep the two profiles? BTW the new "user" does not have sudo priviledges :o

---

### Post by northern lights on 2009-01-05
> **mayagrafix said:**
> OK, I created a new user and that worked. Xfce is back to normal and Gnome works great also, the panels are back in their place. So what is my next step?You could have probably just uninstalled *gnome-panel*. Should have done it also.

> **mayagrafix said:**
> BTW the new "user" does not have sudo privileges :oLog into your old account, open your terminal emulator of choice and run```
sudo usermod -G NEWUSER,adm,dialout,cdrom,plugdev,lpadmin,admin,sambashare NEWUSER
```where NEWUSER should be replace by your new user's login name.

---

### Post by wizard10000 on 2009-01-05
You might have a whole buncha fun trying to find out which files need to be changed.  Here's what I did last time I messed up a profile -

1. Create a new user (you already did this).

2.  Add the new user to the 'admin' group so you can use sudo.

3.  Log on as the new user and move a bunch of the old user's profile to a safe place - mainly  all ~/.gconf* and ~/.gnome* directories plus the files ~/.ICEauthority and ~/.Xauthority

Hope this helps -

---

### Post by northern lights on 2009-01-05
Redundant.

Darn 502 Proxy overload.

---

### Post by mayagrafix on 2009-01-05
> **northern lights said:**
> You could have probably just uninstalled *gnome-panel*. Should have done it also.

Thanks for the info :KS How should I go about uninstalling Gnome-panel? with Synaptic Package Handler or apt-get?

---

### Post by northern lights on 2009-01-05
Either way.```
sudo aptitude purge gnome-panel
```should do it.

Check how many packages it wants to remove though. In Ubuntu w/ GDM, gnome-panel is obviously part of the desktop metapackage and attempting to remove it will remove gnome completely. This should not be the case for XFCE, but I'm not certain and can't check right now. Hence, check how many and what extra packages are to be removed before hitting "Y".

---

