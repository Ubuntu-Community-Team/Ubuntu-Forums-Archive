---
title: "Reinstall ALL media codecs"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by eagle416 on 2009-03-09
Well, when I first got started with kubuntu, I didn't know about ubuntu-restricted-extras, and I just had Amarok and Kaffeine figure themselves out as to how to play media files. Later, I tried installing ubuntu-restricted-extras to add compatibility with more media formats, but it ended up making Kaffeine go into irrecoverable errors and Amarok won't play MP3's. I want to wipe out all codecs for media, and just start fresh, without doing a reinstall.

Kubuntu 8.04 Hardy Heron

Any suggestions?

---

### Post by Diabolis on 2009-03-11
It would be easier to troobleshout your problem if you had posted the error messages that you get, if any are shown.

The libraries that I usually install for media are:

gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad w32codecs

You can reinstall packages with this command:
```
 sudo apt-get --reinstall --install *package name*
```

---

### Post by eagle416 on 2009-03-11
When I try to play certain videos in Kaffeine, This little installation bar advances twice, then it gives an error message that says "Codec Package is Already Installed". It doesn't say WHICH codec package.

As for Amarok, it just says "Amarok cannot play MP3 files" and there's a button that says "install MP3 support" I click that, and nothing happens.

---

### Post by teamcoltra on 2009-03-11
Have you taken a gander over at [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3) ?

---

