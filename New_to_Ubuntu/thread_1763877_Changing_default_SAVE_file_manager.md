---
title: "Changing default SAVE file manager"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by BobJam on 2011-05-21
I like gnome-commander better than nautilus.  So it's no problem opening gnome-commander and manipulating from there.

I've tried to use gconf to set gnome-commander as my default file manger, but it doesn't seem to work ( desktop>gnome>applications>component_viewer and set it to "exec gnome-commender".)

When I say "it doesn't seem to work" what I'm talking about is the SAVE and SAVE AS dialogue in gedit.  THIS is where I want gnome-commander to show up instead of nautilus.  Nautilus shows up no matter what I do.

It may not be an issue of a default file manager but rather nautilus showing up as the SAVE default.  That's what I want to do.

Can it be done, and if so how?

---

### Post by jtarin on 2011-05-21
[Maybe some ideas here.]("https://help.ubuntu.com/community/DefaultFileManager")

---

### Post by mcduck on 2011-05-21
Sorry, but probably not. It's not Nautilus that shows up, the Save dialog is just a standard GTK2 dialog (GtkFileChooserDialog). So it comes directly from the toolkit itself, not from any program.

---

