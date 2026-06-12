---
title: "Convert High Bitrate MP3 to Low Bitrate MP3"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by nick987654321 on 2009-07-24
I am looking for a package that will covert high bit rate mp3's to low bit rate mp3's.  For example I have a mp3 at 320 bit rate and I want to convert it to 128 bit rate.  Any suggestions?!?  -thx

---

### Post by braete on 2009-07-24
audacity

---

### Post by LookTJ on 2009-07-24
I recommend you take a look into ffmpeg, unless you're after a GUI progrom, that I cannot provide.

```
ffmpeg -i input.mp3 -ab 128k output.mp3
```I hope this works out well for you :)

It is also recommended that converting a lossy format into lossy format is not a good idea.

:)

---

### Post by nick987654321 on 2009-07-25
I found a great package in Synaptic that does exactly what I needed....SoundConverter.  You will also need to install 'gstreamer0.10-plugins-ugly-multiverse' for mp3 conversions.

---

### Post by mikechant on 2009-07-27
I came across both soundconverter and soundkonverter and tried them both, and decided soundkonverter was better (can't remember why now, but it might be worth trying both).

---

