---
title: "Internal Gstreamer error: file bug"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by RayleenCourtney on 2010-07-21
I've been using Rhythmbox (on Ubuntu 10.04) as my media player for a few months now with little problem. But suddenly, I keep getting an error message when I try to import new audio files into the program. It tells me "Internal gstreamer error: file bug"

I've tried poking around on these forums to find an answer before I made a new thread, but found nothing that worked. Anybody have any thoughts?

Thank you in advance!

---

### Post by jtarin on 2010-07-21
Have you done a recent update to any related apps....like gstreamer,any codecs, audio changes? Are you using pulse audio or alsa? Have you tried running from command line?

---

### Post by RayleenCourtney on 2010-07-21
I don't know the update command for any of these apps, but I would certainly try them if I knew! 

I'm not sure whether I'm using pulse audio or alsa..... how do I find out?

---

### Post by jtarin on 2010-07-21
> **RayleenCourtney said:**
> I don't know the update command for any of these apps, but I would certainly try them if I knew! 

I'm not sure whether I'm using pulse audio or alsa..... how do I find out?

Simply put....have you done **_ANY_** updates just before this problem arose? Do you have any sound from any application? When you say new audio files what type are they?

---

### Post by RayleenCourtney on 2010-07-21
I had done the standard updates that my Package Manager periodically prompts me to do.

Yes, there is sound from Rhythmbox. It works just like it's supposed to, EXCEPT for adding new songs. When I try to add any audio file (mp3, m4a, etc) it freezes, goes onto a grey screen, and gives me the error message.

---

### Post by jtarin on 2010-07-21
What file extension are they.....mp3....etc?

---

### Post by RayleenCourtney on 2010-07-21
See my above post for the answer I already gave to this question.

---

### Post by jtarin on 2010-07-21
Are you using the Synaptic package manager for your updates?

Issue this command in a terminal and post the output.
```
dpkg -l |grep gstreamer
```

and this one
```
dpkg -l |grep Rhythmbox
```

---

### Post by phatqao on 2010-07-24
i'm having a similar problem. same error message, but rhythmbox remains unable to import new music as soon as it's opened. this started this morning when attempting to import new music by way of the 'home/~/Music' directory. i saw on the [ubuntu development page]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/367623") that this may be a bug, are there any temporary fixes that can be used without waiting until october for the next release?

grep output for gstreamer:

ii  bluez-gstreamer                           4.60-0ubuntu8                                   Bluetooth GStreamer support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
ii  gstreamer0.10-fluendo-plugins-mp3-partner 7.0.20100316-3                                  MP3 codec support for GStreamer
ii  gstreamer0.10-gnonlin                     0.10.15-1                                       non-linear editing module for GStreamer
ii  gstreamer0.10-nice                        0.0.10-2build1                                  ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad                 0.10.18-1ubuntu1                                GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-base                0.10.28-1                                       GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps           0.10.28-1                                       GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                0.10.21-1ubuntu3                                GStreamer plugins from the "good" set
ii  gstreamer0.10-pulseaudio                  0.10.21-1ubuntu3                                GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                       0.10.28-1                                       Tools for use with GStreamer
ii  gstreamer0.10-x                           0.10.28-1                                       GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0           0.10.28-1                                       GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                        0.10.28-1                                       Core GStreamer libraries and elements


grep output for Rhythmbox:

ii  rhythmbox-ubuntuone-music-store           0.0.9-0ubuntu1                                  Ubuntu One Music Store Rhythmbox plugin

---

### Post by RayleenCourtney on 2010-07-24
I just ended up uninstalling and reinstalling Rhythmbox. It seems to be working fine now.

I didn't know there was a new release coming in October-- excellent!!

---

### Post by impresionist on 2010-11-14
Well, we're in Nov. 2010, and this bug it seem to be alive, unsolved yet....

---

