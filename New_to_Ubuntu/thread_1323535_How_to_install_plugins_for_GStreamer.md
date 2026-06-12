---
title: "How to install plugins for GStreamer?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-11-11
Rhythmbox isn't playing (streaming) the radio stations it used to play.

This has something to do with GStreamer.

I opened a terminal and tried:

gstreamer config

but got nothing.

What needs to be done to bring ALL the codecs, etc. into Karmic to allow the OS to perform as expected?

I've installed the "ubuntu restricted extras" and codec32w and am having problem after problem, java isn't working (in Chrome). Picasa won't install or work ...

---

### Post by ohzopants on 2009-11-16
1) For gstreamer plugins: open up synaptic and search for "gstreamer".  There are 3 gstreamer-plugins packages; the good, the bad, and the ugly.  The bad and the ugly are the ones that are the most useful (e.g. divx, xvid, x264, etc.).

2) Java in chrome:  looks like this might be a bug. [http://code.google.com/p/chromium/issues/detail?id=25731](http://code.google.com/p/chromium/issues/detail?id=25731)

3) Picasa:  How is it not working?  Can you provide some more details?

---

### Post by Mark_in_Hollywood on 2009-11-17
> **ohzopants said:**
> 1) For gstreamer plugins: open up synaptic and search for "gstreamer".  There are 3 gstreamer-plugins packages; the good, the bad, and the ugly.  The bad and the ugly are the ones that are the most useful (e.g. divx, xvid, x264, etc.).

2) Java in chrome:  looks like this might be a bug. [http://code.google.com/p/chromium/issues/detail?id=25731](http://code.google.com/p/chromium/issues/detail?id=25731)

3) Picasa:  How is it not working?  Can you provide some more details?

Looking at the Syn. Pkg. Mgr. list of gstreamer packages, I see that good, bad and ugly are installed. Yet, when I go to this page:
[http://www.memritv.org/clip/en/2271.htm](http://www.memritv.org/clip/en/2271.htm)
the video opens, closes, and then doesn't play.

As for Java. I must have that bug, and can wait.

Picasa. I installed 2.7 and now have Picasa, but cannot find the icons to launch it with. So I must open a terminal and launch "by hand" so to speak.

thanks for your attention.

---

### Post by ohzopants on 2009-11-17
I checked that link (from a windows pc) and that's a wmv video.  Support for those is awful, at best.  Even for local files.  One thing that may help is trying to use the vlc-mozilla plugin instead of the totem one.  I've had slightly better results with that one but I haven't really used it much since most of the videos I watch online are flash based.

An easy way to get a launcher for picasa in your menus (which should have been created automatically, but that's another issue) is to locate any old .desktop file.  From a terminal:
```

locate firefox.desktop

```

Simply make a copy of that file in the same directory and rename it picasa.desktop.  Then modify it for your purposes; the files are pretty self-explanatory once you open them.

---

