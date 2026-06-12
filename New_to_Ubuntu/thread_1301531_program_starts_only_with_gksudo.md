---
title: "program starts only with gksudo"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by Memyselfandi2 on 2009-10-26
Hello,

I tried to install Picasa for Linux on my Ubuntu 9.10/Gnome - system.
Everything seemed to be fine, but Picasa won't start when I click on the shortcut (something like /opt/bin/picasa). When I add the gksudo-command (like gksudo /opt/bin/picasa) Picasa starts. What can I do? Do I have to change permissions for directories or files? What groups need permissions?

Thank you for your help.

---

### Post by revanb on 2009-10-26
I've not tried picasa, but it is worth going into the System->Administration->UsersAndGroups option, then in your user settings under UserPriviledges tab see if anything there should be enabled...

Good luck!

---

### Post by philinux on 2009-10-26
> **Memyselfandi2 said:**
> Hello,

I tried to install Picasa for Linux on my Ubuntu 9.10/Gnome - system.
Everything seemed to be fine, but Picasa won't start when I click on the shortcut (something like /opt/bin/picasa). When I add the gksudo-command (like gksudo /opt/bin/picasa) Picasa starts. What can I do? Do I have to change permissions for directories or files? What groups need permissions?

Thank you for your help.

How did you install it? If you installed it as root then this could be the reason.

---

### Post by Memyselfandi2 on 2009-10-26
> How did you install it? If you installed it as root then this could be the reason.

I'm new to Ubuntu/Linux, but don't you have to be root to install programs? I did it using the GUI synaptics "Paketverwaltung" (I don't know how you call this in English, sorry). Later I tried it using the console (sudo install).

Sorry for my English :oops:

---

### Post by Memyselfandi2 on 2009-10-26
@revanb

> Hello,

I tried to install Picasa for Linux on my Ubuntu 9.10/Gnome - system.
Everything seemed to be fine, but Picasa won't start when I click on the shortcut (something like /opt/bin/picasa). When I add the gksudo-command (like gksudo /opt/bin/picasa) Picasa starts. What can I do? Do I have to change permissions for directories or files? What groups need permissions?

Thank you for your help.

Sorry, forgot to answer this posting:
I'll try when I'm back home. Right now I'm at work. Thank you so far...

---

### Post by aasche on 2009-10-28
Problem solved - user installed AND started Picasa 2.7 with "sudo" - so properties of *~/.picasa* were wrong. Quick fix: remove the folder with

```
sudo rm -rf ~/.picasa
```

and start Picasa 2.7 as user (Picasa creates the missing folder automatically).

---

