---
title: "Missing Python dependency. Fixes?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-04-26
I'm trying to use the usb-creator program to put Ubuntu Studio on a flash drive. However, I can't run usb-creator. Note that I'm using Kubuntu 9.04 (KDE 4.2.2), which I think is the source of the problem.

I installed it with ```
sudo apt-get install usb-creator
``` It finished successfully. 
When I launch it from the K-menu thing, there is a listing for it in the taskbar, but no window opens; it eventually disappears. From the command line I get the following error. 

> ~$ sudo usb-creator
Traceback (most recent call last):
  File "/usr/bin/usb-creator", line 21, in <module>
    from usbcreator.gtk_frontend import GtkFrontend
  File "/usr/lib/python2.6/dist-packages/usbcreator/gtk_frontend.py", line 25, in <module>
    import gnomevfs
ImportError: No module named gnomevfs


I think that the python dependencies weren't upgraded properly with 9.04, so some gtk library is not installed. Does anyone know which package I should install? I already have python-gtk2 (2.14.1) and didn't see anything else that seemed relevant.

Thanks for the help

---

### Post by jbrown96 on 2009-04-26
Fixed with ```
sudo apt-get install python-gnome2
```

---

