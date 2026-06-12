---
title: "Sound Error"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by borboleta on 2009-03-26
"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

It is a new netbook so I don't understand what would be wrong with it?
I don't have any sound at all.[ubuntu netbook remix]

By the way I dont have access to that synaptic programme since the apply button is greyed out, i just have something called add/remove

Thanks in advance for any help!

---

### Post by borboleta on 2009-03-26
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

When I go into Sound and click on test for Sound Playback I get the above message

There is one option which has ALSA selected, all the rest are autodetect or something like that, but even when i text the one with ALSA i get an error message

---

### Post by borboleta on 2009-03-26
I have these programme things lready instlled on this computer:
Volume Control
GNOME media utilities  
This package contains a few media utilities for the GNOME desktop:
* the GNOME GStreamer-based audio mixer;
* a volume level meter for ESD;
* the GNOME Sound Recorder;
* the GStreamer properties capplet.

 Volume Monitor
GNOME media utilities  
This package contains a few media utilities for the GNOME desktop:
* the GNOME GStreamer-based audio mixer;
* a volume level meter for ESD;
* the GNOME Sound Recorder;
* the GStreamer properties capplet.

and 2 things for recording

---

### Post by borboleta on 2009-03-28
:) sorry i'd just like to bump this so maybe someone who knows what to do reads this

---

### Post by halitech on 2009-03-28
open up a terminal and post the results of
```
aplay -l
```
also
```
lshw -C sound
```

---

