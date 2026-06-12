---
title: "&quot;this bitstream does not contain Vorbis audio data&quot;"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by pranayama on 2009-10-14
I have converted some mp3s to oggs with Sound Converter. I have done this many times before and always been able to play the oggs back with VLC.

Now VLC is silent when playing back the oggs I have generated tonight. But Totem and Exaile play them fine. The only difference I can think of is that they're podcasts and mono instead of stereo.

When starting VLC in a terminal the following error message streams past repeatedly:

```
[00000440] vorbis decoder error: this bitstream does not contain Vorbis audio data
```

I have changed VLC audio output to Pulseaudio and installed vlc-plugin-pulse which make no difference.

---

### Post by Book 'em Dano on 2009-11-24
I am getting the same error message when trying to play ogg audio files encoded by rhythmbox (I think), but another ogg audio file of an audio stream encoded by vlc will play.  I seem to remember that while Totem would not play any of the ogg audio files vlc used to, but currently is not.

I reinstalled the various libraries pertaining to Vorbis but the result is the same.

---

### Post by pranayama on 2009-12-19
In my case, it turned out to be the album art jpeg. VLC could open the ogg file again when that was removed. Totem and Exaile could cope with the album art.

---

