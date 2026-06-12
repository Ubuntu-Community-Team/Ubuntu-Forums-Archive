---
title: "Playing .avi files"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-03-13
Hi - how do I play a .avi file? I can't get it to play in any of the audio/media players I've tried. I've looked around and apparantly MPlayer is supposed to, but unfortunately that doesn't work for me :(

Can anyone help?

---

### Post by Xero Xenith on 2009-03-13
Run this command - 
```
sudo apt-get install ubuntu-restricted-extras
```

This will install a LOT of codecs and such that are very useful for audio/video playback, and more proprietary stuff as well. It's the first package I ever install on a new box.

EDIT: Actually, this might be better.

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg
```

---

### Post by stchman on 2009-03-13
> **Azhtabak said:**
> Hi - how do I play a .avi file? I can't get it to play in any of the audio/media players I've tried. I've looked around and apparantly MPlayer is supposed to, but unfortunately that doesn't work for me :(

Can anyone help?

You need all the gstreamer plugins.  

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

---

### Post by andrew.46 on 2009-03-13
Hi,

Can you have a shot at identifying the avi file? Grab a copy of FFmpeg from the repository and run the following:

```
ffmpeg -i my_problem_file.avi
```

This should give a clue as to why the file is not playing.

Andrew

---

