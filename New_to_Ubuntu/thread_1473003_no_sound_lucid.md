---
title: "no sound lucid"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-05-04
I am having no luck getting sound since  upgrade here is some code hoping it will help

```
cmcanulty@Gateway:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'OSS - Open Sound System': Could not open audio device for playback. Device is being used by another application. [gstosssink.c(403): gst_oss_sink_open (): /GstPipeline:pipeline2/GstOssSink:osssink1]
cmcanulty@Gateway:~$ 
```

---

### Post by mpennell on 2010-05-04
Hi! 
1. I am actually VERY Absolute Beginner (that's my caveat).
2. I had the "no sound" problem (I gather it's been common with Lucid Lynx... cats DO tend to be quiet, after all...).
3. Someone somewhere here suggested entering into the terminal this: 
  alsactl init

I do not know what this means and what it does and why it worked, but it did work to give me back sound. Maybe it will work for you?

---

### Post by agnes on 2010-05-04
Perhaps more details would help more

1. Do you have no sound in *all *applications? Also if you close everything and only open 1 music-playing app?
2. You mention a gstreamer error but what happens if you install Gnome-Mplayer and play a sound file with it? (mplayer != gstreamer)

---

