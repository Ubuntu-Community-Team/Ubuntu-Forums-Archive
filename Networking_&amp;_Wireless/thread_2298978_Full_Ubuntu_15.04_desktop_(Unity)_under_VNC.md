---
title: "Full Ubuntu 15.04 desktop (Unity) under VNC"
date: 2015-10-15
forum: Networking &amp; Wireless
---

### Post by tonymobily on 2015-10-15
Hi,

I have tigervnc working 100% well.
What do I have to write in my .vnc/xstartup file so that a FULL Ubuntu desktop comes on? I want to include:

* The proper application-dependent menu bar at the top
* The proper Unity menu on the left
* All shortcuts working

I am after the _full_ thing. I managed to run XFCE 100% OK, but I simply hate it. I managed to get Unity to come up, but not without errors relating to dbus etc.

So, what's "the" magic formula to get a FULL Ubuntu/Unity desktop really?

Merc.

---

### Post by tonymobily on 2015-10-15
Hi,

For the record, I read this:

[http://askubuntu.com/questions/150487/what-happens-under-the-covers-to-log-me-in-and-start-up-unity-or-another-graphic](http://askubuntu.com/questions/150487/what-happens-under-the-covers-to-log-me-in-and-start-up-unity-or-another-graphic)

If I run lightdm-session, I end up with a Gnome (not Unity) desktop...

Merc.

---

### Post by ajgreeny on 2015-10-15
I think I read somewhere that you need to have **ubuntu-session** in the startup configuration.  I don't use unity so I might be wrong but it's worth a try.

What OS did you install in the first place; Ubuntu (using unity), Ubuntu-gnome, or Xubuntu (XFCE desktop)?

---

### Post by slickymaster on 2015-10-15
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by leetom on 2015-11-28
I have the same problem, have you solved it?

---

