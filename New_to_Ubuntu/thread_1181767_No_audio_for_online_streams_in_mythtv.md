---
title: "No audio for online streams in mythtv"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Brasil on 2009-06-08
Hi, I have a MB that outputs sound and video via HDMI. I configured my audio  correctly for TV, etc by putting ALSA:plughw:0,3 into the audio output device - audio in mythtv, mythdvd, etc works like a charm. I have also configured audio properly elsewhere so that streams from youtube, etc work properly. But I have no audio for any of the online streams in mythtv... This is true for both video streams and purely audio streams. Any advice as to what I should tweak?

Other audio settings are passthrough output device: default max channels: stereo upmix:passive enable ac3 to spdif pass checked, enable dts to spdif passthrough checked, aggressive sound card buffering unchecked, use internal volume controls unchecked

---

### Post by Brasil on 2009-06-11
Anybody?

---

### Post by pauna on 2009-06-11
> **Brasil said:**
> But I have no audio for any of the online streams in mythtv... This is true for both video streams and purely audio streams. Any advice as to what I should tweak?


Maybe you have configured online streams to use different playback application and the sound has not been set up correctly in that application? 

Mythtv can be configured to use different players for different content and that has caused me some problems like yours in the past (i.e. something works in video but not in audio and vice versa). I haven't used online streams, though, so this is a wild guess.

---

### Post by Brasil on 2009-06-13
> **pauna said:**
> Maybe you have configured online streams to use different playback application and the sound has not been set up correctly in that application? 

Mythtv can be configured to use different players for different content and that has caused me some problems like yours in the past (i.e. something works in video but not in audio and vice versa). I haven't used online streams, though, so this is a wild guess.

Hmmmn! Good suggestion, I'll have a look to see if I can work out where to change it! Thanks mate.

---

### Post by Brasil on 2009-06-17
Well, I've been fiddling around for DAYS with no luck. Based on some stuff I found I've tried editing mplayer.conf as well as /usr/share/mythtv/mythstream/player.xml to add plughw:0.3 to it but no luck. I think I am close but just can't seem to figure it out.:(

---

