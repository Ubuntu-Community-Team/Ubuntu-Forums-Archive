---
title: "What happened to Samba GUI config?"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by FeraTech on 2008-09-11
Is it me or is hardy missing the Samba configuration utility?

I remember you use to be able to change the workgroup and settings all from the little GUI samba app.

Why was this taken out in hardy?

---

### Post by bab1 on 2008-09-12
It's still there.  Try Alt-f2>>gksudo shares-admin

---

### Post by FeraTech on 2008-09-12
That is quite strange. I tried the command you said but it was all greyed out including the unlock function and it did not list any of my active shares.

Why is it no longer part of the gnome desktop? What happened? Was somebody from ubuntu development dating somebody in Samba development and they have a falling out?

---

### Post by FeraTech on 2008-09-12
Interesting it only works for me if I only type in shares-admin then unlock it through the gui.

---

### Post by bab1 on 2008-09-12
I'm really suprised.  Another reason to not update from Gutsy. The Gnome (gio/gvfs)interface seems to be in a transitional state and has broken many of the Samba tools.   Many others have complained about the lack of forewarning to users.

See:
[http://http://ubuntuforums.org/showthread.php?t=913498&highlight=gvfs]("http://http://ubuntuforums.org/showthread.php?t=913498&highlight=gvfs") [http://ubuntuforums.org/showthread.php?t=909453&highlight=gregphil]("http://ubuntuforums.org/showthread.php?t=909453&highlight=gregphil")

---

### Post by gregphil on 2008-09-12
Not only that, but they broke shared file browsing for authenticated Windows shares:

[https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

It may get fixed in a month or so.....

---

### Post by bab1 on 2008-09-12
@gregphil

> It may get fixed in a month or so.....

This is good news!  Are you thinking that Intrepid (8.10) will be when they get it right?  Do you have other info.  I'm hoping for an update to Hardy (8.04) as it is the LTS version.

---

