---
title: "Cheese does not work"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by ubuntu27 on 2008-12-23
Hello everyone. I am trying to take pictures using Cheese, but it does not show any images from my built-in webcam. It is just blank.
The take video function does not work as well.

_It has always worked until now_. I already tried to re-install.

What can I do?

Here is the input from terminal:

```
ubuntu27@debian:~$ cheese
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:11336): WARNING **: could not generate thumbnail for /home/ubuntu27/Videos/Webcam/2008-12-23-131704.ogv (video/ogg)


(cheese:11336): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:11336): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:11336): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small


```

Thank you guys!

---

### Post by nhasian on 2008-12-23
take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1007341](http://ubuntuforums.org/showthread.php?t=1007341)

---

