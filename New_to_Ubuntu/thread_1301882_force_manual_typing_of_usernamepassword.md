---
title: "force manual typing of username/password"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-10-26
Greetings,

I would like to force the login screen to make me type in the username at startup instead of selecting it.  Any way to do this?

Running Xubuntu 9.10 on a Dell Mini 9.

---

### Post by jrev on 2009-10-26
system/admin/connection windows

---

### Post by Redmage913 on 2009-10-26
> **jrev said:**
> system/admin/connection windows


Forgive me, but I don't think that applies in XFCE. There is no admin tab under system, neither is there a connection windows button.

---

### Post by earthpigg on 2009-10-26
according to [this]("http://packages.ubuntu.com/karmic/xubuntu-desktop"), i take it xubuntu uses the latest version of gdm?

the latest version of gdm does not have a GUI to manage it's settings, for some ungodly reason.

here is the arch wiki documentation on what you are asking, though i myself cannot verify if it works or not (but the arch wiki has never led me astray before, and bleeding edge distro = documentation on bleeding edge problems...):

[http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Removing_list_of_user_names](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Removing_list_of_user_names)

---

### Post by Redmage913 on 2009-10-26
Thank you very much. I'm listening to streaming audio at the moment, when I'm done that I'll restart and see if it worked.

---

### Post by earthpigg on 2009-10-26
since gdm is a daemon, you will probably need to reboot for changes to take affect, not just log out :D

---

