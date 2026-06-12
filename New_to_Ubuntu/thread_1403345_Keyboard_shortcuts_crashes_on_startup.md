---
title: "Keyboard shortcuts crashes on startup"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Ajay Ramaseshan on 2010-02-10
Hello 
I am using Ubuntu 9.04 and was trying to run the keyboard shortcut application . But it crashed on startup.
I also tried another thing - trying to launch it from terminal. ie. I pulled the application to the panel and right clicked on it and went to properties to find the command for it. When I ran command gnome-keybinding-properties  I got a segmentation fault( core dumped). 
This is the exact error that is dumped on the terminal screen:

(gnome-keybinding-properties:8311): Gtk-CRITICAL **: gtk_tree_store_get_value: assertion `VALID_ITER (iter, tree_store)' failed

(gnome-keybinding-properties:8311): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.22.3/gobject/gtype.c:3942: type id `0' is invalid

(gnome-keybinding-properties:8311): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault


Could someone please help me out? I wanted to edit some keyboard shortcuts but am not able to do anything now.

---

