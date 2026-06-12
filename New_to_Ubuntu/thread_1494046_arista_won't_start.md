---
title: "arista won't start"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by jodonald on 2010-05-26
I've been using arista transcoder to convert media files.  Recently, however, it hasn't been able to start up.  When i attempt to open the program, it looks like it will load but nothing happens.  I've tried removing and reinstalling arista but no luck.  Any suggestions?

---

### Post by Skorzen on 2010-05-26
Have you tried running it from the command-line? Any error messages?
Have you checked the log files? Under /var.

---

### Post by jodonald on 2010-05-27
Thanks for your help.  I can't figure out how to run arista-transcode from terminal but I downloaded some updates and it started running again.  I have much to learn.

---

### Post by XsheepX on 2011-03-23
> **jodonald said:**
> Thanks for your help.**  I can't figure out how to run arista-transcode from terminal** but I downloaded some updates and it started running again.  I have much to learn.
To run it from terminal, it would be arista-gtk :)

---

### Post by Zanven on 2011-08-18
I'm having the same trouble. I click Arista and it shows the thinking cursor for a half of a second then nothing happens. Terminal reads as follows:
> ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Traceback (most recent call last):
  File "/usr/bin/arista-gtk", line 1685, in <module>
    main = MainWindow(options)
  File "/usr/bin/arista-gtk", line 398, in __init__
    self.setup_devices()
  File "/usr/bin/arista-gtk", line 624, in setup_devices
    image = _get_icon_pixbuf(device.icon, width, height)
  File "/usr/bin/arista-gtk", line 122, in _get_icon_pixbuf
    image = gtk.gdk.pixbuf_new_from_file_at_size(path, width, height)
glib.GError: Unrecognized image file format

---

