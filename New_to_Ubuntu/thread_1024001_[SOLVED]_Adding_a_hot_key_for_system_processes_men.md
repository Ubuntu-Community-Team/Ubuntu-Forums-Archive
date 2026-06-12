---
title: "[SOLVED] Adding a hot key for system processes menu?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-28
So I just recently started using Gnome, previously I had been using KDE and one feature I really miss from KDE is that when hitting ctrl+esc it would bring up a system processes menu. Is there a way to link the system processes menu in Gnome to these (or similar) hotkeys so when pressed it will popup? (I am really kinda lazy and don't like going through the menus to close a frozen app.)

~Jeff

---

### Post by Michael.Godawski on 2008-12-28
hi, 

have a look at this application:
[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)

I guess with a little tweaking it should work.

---

### Post by beastrace91 on 2008-12-28
That program worked like a charm! Thank you very much :)

~Jeff

---

### Post by Michael.Godawski on 2008-12-28
I am rather curious...

can you please post what entry did you add so that 
ctrl+esc would be associated with the system processes?

---

### Post by beastrace91 on 2008-12-28
I just opened the .xbindkeysrc in gedit and added the following lines: ```
#Display System Monitor
"gnome-system-monitor"
  Control + Escape
```

It is a pretty nifty little tool, you can bind any combination of keys to run any terminal command :D

~Jeff

---

