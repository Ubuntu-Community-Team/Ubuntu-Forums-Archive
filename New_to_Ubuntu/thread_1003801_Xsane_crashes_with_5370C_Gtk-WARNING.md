---
title: "Xsane crashes with 5370C Gtk-WARNING"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-12-06
I am trying to scan some pages with my 5370C HP scanner using Xsane. It detects it and seems to work and all but when I click scan the scanner scans the image but about 1/2 way xsane crashes. When I start it from the terminal I get.
```
:~$ xsane

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7860): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
```
All I get when it crashes is
```
Segmentation fault
```

Any help would be great!

Thanks a lot,
Justin

---

### Post by grendel_khan on 2009-01-10
Please enable Apport and file a bug report with crash details, if you can reproduce the bug.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Also, I can't get the Gtk-WARNING messages to appear (they're not related to any crash; they're just a notice to change some obsolete layout code) on my copy of xsane ("dpkg -l xsane" reports that I'm running xsane 0.995-3ubuntu2).

---

