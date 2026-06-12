---
title: "No option to use KDE from GDM after installing kubuntu-desktop"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by jazzgossen on 2010-07-30
I just installed kubuntu-desktop on my Ubuntu 10.04, because I'd like to be able to try out KDE while keeping my current installation.

According to the [documentation for 10.04]("https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html"), installing kubuntu-desktop should be enough, and there should be an option to select a KDE session from GDM afterwards.

However, I see no such option. 

If I quit GDM and start KDM, I can login with either Gnome or KDE.

How can I choose which session to run from GDM?

Edit: I realized I can change the session type using "gdmsetup", but that changes it for all users, which is not at all what I want.

---

### Post by jazzgossen on 2010-07-30
I see. The problem is that if GDM is set to not require a password for a user, the option to choose the session type is never displayed. 

IMHO, that's a design flaw. But at least I can now choose which session I want, even though the users that want to try both Gnome and KDE now have to enter their passwords at logon (unless I start using KDM instead of GDM).

---

