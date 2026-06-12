---
title: "Scanner/Xsane Issues HP Scanjet 8250"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-24
Still not able to scan. Typically, the 1st attempt to scan with xsane restarts my computer, then post attempts shuts down xsane app. This is the output from running xsane in a terminal
(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

Also, someone suggested running hplip-3.9.2.run. I saved it to my desktop, but can't run it. Can't open file.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Any help is appreciated. 
JS

---

### Post by Bachstelze on 2009-03-24
As its extension imples, a .RUN file is supposed to be run (executed), not opened in a text editor. Open a terminal, browse to the directory you saved it to, and do

```
./hplip-3.9.2.run
```

---

