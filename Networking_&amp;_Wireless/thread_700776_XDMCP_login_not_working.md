---
title: "XDMCP login not working"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2008-02-18
After i attempt to click connect on the desired PC it simply returns me to the main login, not a remote one.

Why is this?

---

### Post by Aearenda on 2008-02-18
XDMCP was broken in Gutsy's GDM. See [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193).

---

### Post by dgrafix on 2008-02-19
After reading a bit it appears this bug has been around for months with low importance!!

What are they thinking? Surely this is [COLOR="Black"]**critical**[/COLOR] for anyone running distributed servers.

What are the alterrnitives as the PicoATX mini-server i am building will be in sore need of that as there will be no peripherals attached, except for initial setup of course.

---

### Post by Aearenda on 2008-02-19
All is not lost - there are ways around it. One is to use KDM instead of GDM as your login manager. Another is to use Xephyr (similar to Xnest, but better) as your client inside a local session - this is what I do, with Xephyr full-screen on one desktop - it makes for very quick switching between systems.

As far as the release testing in concerned, it's a trade-off that has to be made - a free operating system cannot possibly be tested in the same way as a commercial one, since it relies on volunteers. The release cycle is very short, so you can flip back to Feisty and still be almost up to date until the problem is fixed. The best way to make sure it doesn't happen again is to take part in the testing of the next version.

Good luck!

---

### Post by dgrafix on 2008-02-21
One option is to use Xubuntu instead, do you happen to know if this supports XDMCP?

---

### Post by Aearenda on 2008-02-21
Xubuntu still uses GDM as login manager, so it would make no difference! The fault is in GDM, installing and using KDM instead of GDM still allows you to use GNOME as your desktop environment.

---

