---
title: "Gloobus Preview..."
date: 2010-07-13
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-07-13
For some reason gloobus preview will only play audio from any video file...

I'm running ubuntu 10.04

Thanks

---

### Post by kamitsukai on 2010-07-15
<Bump>

---

### Post by kamitsukai on 2010-07-20
Output from terminal whilst trying to play an divx/xvid avi file:

> [WARNING] Warning message: warning message from element 'uridecodebin0': GstMessageWarning, gerror=(GstGError)NULL, debug=(string)"gsturidecodebin.c\(686\):\ unknown_type_cb\ \(\):\ /GstPlayBin2:playbin/GstURIDecodeBin:uridecodebin0";

---

### Post by kamitsukai on 2010-07-20
Seems to play MPG files without fault...

So what would cause gloobus-preciew to play avi, flv files with sound only? and not mkv files at all?

---

### Post by kamitsukai on 2010-07-20
okay 2 hours of googling turned up this:

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/573607](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/573607)

which led me to a comment by someone called "Bright Lightning" who incidentally is now my new all time favorite person.

> Bright Lightning wrote on 2010-06-19:	 #10

I also had this bug - when I open a video file (like an avi or flv or mp4). However I found a solution on the ubuntu forums - I ran the following commands:

rm ~/.gstreamer-0.10/*
This removed the Gstreamer settings for the current user.

I then installed Gstreamer-Tools (check in synaptic to see if you already have it, if not install it - or run "sudo apt-get install gstreamer-tools" without quote marks).

and then ran the gstreamer-tools command:
gst-inspect
to rebuild the gstreamer settings.

This fixed playing the video layer for all these formats!

I hope you find this useful.

Matt

---

