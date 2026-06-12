---
title: "Banshee help?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by scathmandra on 2009-11-03
I somehow can't play the internet radio station I'd added two days ago and which worked fine until my upgrade to Karmic Koala. If I run Banshee in terminal, I get
```

[Info  13:15:09.001] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, x86_64) @ 2009-10-19 15:42:39 UTC]

(Banshee:3699): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libx264.so.67: cannot open shared object file: No such file or directory

(Banshee:3699): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': libx264.so.67: cannot open shared object file: No such file or directory
[Info  13:15:34.256] All services are started 23.719725s
[Info  13:15:50.943] nereid Client Started
** Message: don't know how to handle audio/x-wma, wmaversion=(int)2, bitrate=(int)64024, depth=(int)16, rate=(int)44100, channels=(int)2, block_align=(int)2973, codec_data=(buffer)008800000f00752e0000
[Error 13:16:42.689] GStreamer stream error: CodecNotFound

(gstreamer-codec-install:4043): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libx264.so.67: cannot open shared object file: No such file or directory

(gstreamer-codec-install:4043): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': libx264.so.67: cannot open shared object file: No such file or directory
** Message: don't know how to handle audio/x-wma, wmaversion=(int)2, bitrate=(int)64024, depth=(int)16, rate=(int)44100, channels=(int)2, block_align=(int)2973, codec_data=(buffer)008800000f00752e0000
[Error 13:16:45.185] GStreamer stream error: CodecNotFound
^C

```
I honestly can't extract much from this, as I'm a complete beginner... help? What am I missing? How can I install a plugin?

---

### Post by Darce on 2009-11-03
Check to see if you have gstreamer installed

Go to System -> Administration -> Synaptic Package Manager

    and type gst into the  'quick search' box

There should be a green box next to 'gstreamer0.10-ffmpeg'

Cheers,

Tim

---

### Post by Technoviking on 2009-11-03
Installing ubuntu-restricted-extras should install all the codecs you need.

```
sudo apt-get install ubuntu-restricted-extras
```

T-V

---

### Post by scathmandra on 2009-11-03
I did both of those. gstreamer is already installed, and so are the restricted extras.

Any other ideas?

---

### Post by Technoviking on 2009-11-03
Maybe related to this bug.

[https://bugs.edge.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/467193](https://bugs.edge.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/467193). Is gstreamer0.10-pitfdll installled?

T-V

---

### Post by scathmandra on 2009-11-03
I checked and got > gst-inspect-0.10 pitfdll

(gst-inspect-0.10:4850): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libx264.so.67: cannot open shared object file: No such file or directory

(gst-inspect-0.10:4850): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': libx264.so.67: cannot open shared object file: No such file or directory
No such element or plugin 'pitfdll'


So how would I install it?

---

### Post by Darce on 2009-11-04
> **scathmandra said:**
> I checked and got 

So how would I install it?

You can install it through the Synaptic Package Manager which is found under 
Sysem -> Administration.

Just punch it into the 'quick search' box.

---

### Post by RayleenCourtney on 2010-08-05
I am having a similar problem-- except Banshee won't read any of my music files AT ALL. When I try to import them, they get listed as errors and each read "No such file or directory". I've got Gstreamer, 0.10 pitfdll, and all of the restricted extras installed. I am ready to tear my hair out....

Any thoughts? Thanks ahead of time. :)

---

