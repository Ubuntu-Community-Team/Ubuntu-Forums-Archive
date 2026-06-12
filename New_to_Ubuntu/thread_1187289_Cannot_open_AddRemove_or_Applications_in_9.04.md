---
title: "Cannot open Add/Remove or Applications in 9.04"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Tristan Carlson on 2009-06-14
First of all, let me start off with this: I am rather inexperienced at varied operating systems and at Ubuntu in particular, so this may very well be some stupid mistake of my own. I just installed Ubuntu 9.04 as my first non-Windows operating system yesterday, and now it will not open some applications such as Banshee (opens but then freezes) wine (refuses to open) or Add/Remove (says it's starting but then nothing happens). I tried most of the suggestions in here: [http://ubuntuforums.org/showthread.php?t=1154685](http://ubuntuforums.org/showthread.php?t=1154685), the only one of which that actually did anything was ```
sudo gnome-app-install
```which opened Add/Remove and produced this: ```
 ** (gnome-app-install:9726): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1295: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_sort_column_id(-1, sort_type)
``` but failed to actually fix anything. I did allow it to update yesterday, so that might have caused something, or it might have simply been my own incompetence. Does anyone know what might be the problem? Thank you very much for any assistance.

---

### Post by gettinoriginal on 2009-07-13
Try rebooting and at the sign in page, > options > session > gnome > change session then sign in as usual.  Hopefully that will help :p  Welcome to ubuntu and the forums.

---

