---
title: "Transmission-GTK stopped working-Theme parsing error"
date: 2016-10-22
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2016-10-22
I am having an issue using transmission-gtk. It was working fine and I don't really know why it stopped, I didn't do any updating or anything. I am running xubuntu 14.04. Anyway, when I try to run transmission from the app menu nothing happens, so then I try to run it from the command line and this is the error returned.
```
(transmission-gtk:5445): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:62:17: Theming engine 'unico' not found
Failed to register: Timeout was reached

```
Can anyone help me with this, i've googled trying to find a solution but I can't find any solutions.

---

### Post by vasa1 on 2016-10-23
Which gtk theme are you using? Have you tried another? Xubuntu 14.04 should default to Greybird which, AFAICT, doesn't use the unico engine and I don't see why transmission-gtk should need it.

---

### Post by dannyboy79 on 2016-10-26
looking under the Appearance tab within my settings i see it's using Greybird. I switched it to Ambience-Graphite-Pro and transmission still shows this when starting from the terminal
```
(transmission-gtk:2194): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:63:17: Theming engine 'unico' not found
Failed to register: Timeout was reached
```

---

