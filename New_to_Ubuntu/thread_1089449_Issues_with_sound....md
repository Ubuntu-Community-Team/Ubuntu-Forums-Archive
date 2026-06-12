---
title: "Issues with sound..."
date: 2009-03-07
forum: New to Ubuntu
---

### Post by deceptionpoint on 2009-03-07
Hello.  Anyway..

I'm having major issues with sound, I've been using Ubuntu for a month and now it's time to get help lol.

Anyawy.  I can't get sound out of flash or some music players/video players/alarms or any IM clients.  
I'm using OSS (ALSA doesn't work, or does anything else..)

So any ideas?

---

### Post by Xiong Chiamiov on 2009-03-07
[Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by deceptionpoint on 2009-03-07
I followed that tut and then I Went to change the sound to alsa and this is what I got (doing it via gnome-sound-properties in the terminal)

(gnome-sound-properties:5636): sound-properties-DEBUG: setting theme ubuntu
sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink': Could not open audio device for playback. [gstalsasink.c(692): gst_alsasink_open (): /GstBin:bin0/GstHalAudioSink:halaudiosink0/GstBin:bin1/GstAlsaSink:alsasink0:
Playback open error on device 'default:1': Invalid argument]

---

### Post by deceptionpoint on 2009-03-08
Bumping for help...

---

