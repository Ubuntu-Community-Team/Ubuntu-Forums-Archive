---
title: "missing plugins"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by manny43 on 2010-01-29
Hello friends 
gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon
My webcam will not work with Cheese version 2.28.1 in Ubuntu 9.10.
Multimedia System Selector ran pipeline test and webcam works.
Does unavailable plugin mean that i have to download and install it?

---

### Post by Shpongle on 2010-01-29
"Most, if not all, Linux distributions provide packages of GStreamer. You should find these in your distribution's package repository.
Note that some distributions split the GStreamer plugins up further than the upstream sources. Additionally, some distributions do not include the gst-plugins-bad, gst-plugins-ugly, and gst-ffmpeg packages in their main repository, for legal reasons. "

[http://gstreamer.freedesktop.org/download/](http://gstreamer.freedesktop.org/download/)

hope this helps

---

