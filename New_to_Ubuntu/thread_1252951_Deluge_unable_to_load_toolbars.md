---
title: "Deluge unable to load toolbars"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by neo.patrix on 2009-08-29
Deluge is failing to start properly on my system. When I start deluge, it loads without any toolbar and buttons, just plain gray/white window

This is the message , which I got in console

> 
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))



any clues?

---

### Post by NoaHall on 2009-08-29
try using "sudo ldconfig" and then attempt running it again.

---

### Post by neo.patrix on 2009-08-30
What does ldconfig do , in this particular case?

Edit : Tried it, no good same error

Edit : Building Deluge package from source did not help either.

Edit : D'oh, please pardon all those edits, it is just thought process.

line 62-63 from script file 'deluge/ui/gtkui/mainwindow.py'

> pkg_resources.resource_filename("deluge.ui.gtkui", "glade/main_window.glade"))

I do not see any 'assertion' statements in the code area of line 63 , so my programmer instincts tell me 'pkg_resources' is the culprit.

---

