---
title: "GVIM gives error screen"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by duckfeet on 2010-03-03
I just loaded Ubuntu 9.10, and everything seems to be working right, with this one minor glitch: I use gvim as my text editor.  (I'm learning Java, and I use it regularly), and I was used to vi in old days on Unix...problem is, every time I load gvim, from terminal, it always brings up this whole page of errors...anything I need to do to make it quit...this only does this in gvim, not vim, and the gvim screen is all right, it's just all the errors on the command line terminal...thanks in advance...

Here is error page:

(gvim:5900): GLib-WARNING **: g_set_prgname() called multiple times

** (gvim:5900): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:5900): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:5900): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:5900): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

** (gvim:5900): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed
geff@geff-desktop:~$

---

### Post by diesch on 2010-03-03
That's a known bug, see [https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188)

---

### Post by duckfeet on 2010-03-03
I had done a search, and hadn't really found a fix, thought maybe someone on here knew of one, but after reading your link, I just went back to vim, and I'm used to it anyway, so no worries...thankyou for quick comeback...

---

