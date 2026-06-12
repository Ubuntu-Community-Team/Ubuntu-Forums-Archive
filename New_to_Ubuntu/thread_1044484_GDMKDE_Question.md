---
title: "GDM/KDE Question"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by rdmike on 2009-01-19
Hi all,

I'm a new Ubuntu user but am quickly getting accustomed to and enjoying the experience. That said, I've been thinking about taking a look at KDE in an effort to see which environment I like best. I understand how to make the change via the terminal but what I am wondering is if making such a change will impact what I already have going in Ubuntu? Specifically what I mean is will switching the environment cause me to lose data such as e-mails within the Evolution mail client?

Thanks!

---

### Post by txcrackers on 2009-01-19
Not at all - in fact, you can run Evolution within KDE. Gnome and KDE can exist quite well side-by-side and no application will be harmed.

The problem you're having is trying to separate the programs from the environment settings. In Windows, this is all controlled by the registry and programs/OS will muck with each other's settings. In Linux-land, each program (which *includes* Gnome and KDE) has their own settings, typically stored in separate files (usually called "dot files" or "hidden" because the filename starts with a "." and is normally hidden from view).

That said, Gnome and KDE do share some settings (notably menus) because they're participating in Freedesktop.org - but that's a good thing.

---

### Post by rdmike on 2009-01-19
Thanks for the reply, great info! Is there any suggested prep prior to getting the KDE?

---

### Post by Ben Page on 2009-01-19
Just install KDE like a normal package via apt-get. You can choose what DE you want in login screen (sessions). I had this setup for the same reason as you (and was disappointed by KDE-but thats another story). Only trouble is that your open office 3.0 (if you have it installed) will be over written by KDEs edition witch is 2.4, and there is no 3.0 stable version for KDE yet. Other than that, there is no incompatibility, and a great plus is that you can use KDE apps in Gnome (like Konqueror witch is a great web browser only available in KDE). Note, you'll need ~450 MB of disk space and will need to download 100MB of archives.
No prep, just install, but watch out for that Open office glitch.

---

### Post by rdmike on 2009-01-19
Excellent info y'all, thank you very much!

---

