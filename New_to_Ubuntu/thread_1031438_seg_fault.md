---
title: "seg fault"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by lapubell on 2009-01-05
I'm not sure where to put this, but I think I found a bug in the gftp-gtk package.

I have several bookmarks set up with shortcuts to different ftp servers and after the hosting on one changed I went in and updated the bookmark.  Now when I try to access the bookmarks menu the program seg faults.

Here is the output from the console when I run it from there:

> 

lapubell@lapubell-desktop:~$ gftp

(gftp-gtk:7116): Gtk-CRITICAL **: gtk_widget_get_pango_context: assertion `GTK_IS_WIDGET (widget)' failed

(gftp-gtk:7116): Pango-CRITICAL **: pango_context_get_language: assertion `context != NULL' failed
Segmentation fault



does anyone know what I should do to get my bookmarks fixed so that this will work again?
where do i submit the bug report?

---

