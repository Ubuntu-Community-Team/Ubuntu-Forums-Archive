---
title: "Videoporama"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by bigal1932flying on 2010-03-14
When I open the program Videoporama I receive the following message:
The ffmpeg package installed don't include libxvid and isn't able to encode in Xvid (avi). This format will be disable in the user interface.
The ffmpeg package installed don't include libx264 and isn't able to encode in H264 (avi). This format will be disable in the user interface.


Mp3 Format is not supported by your version of Sox. Add required package from your distribution unless you won't be able to use mp3 sound file.
How do I fix this problem?

---

### Post by Revolutionary101 on 2010-03-14
Just install the lib files you need and it looks like you need libx264 and libxvid.

To install them type this into terminal:

```
sudo apt-get install libx264-67 libxvidcore4
```

After you install those it should work.

---

### Post by bigal1932flying on 2010-03-16
Tried that command line and it said that both were already the latest version. Thanks.

---

### Post by no2498 on 2010-03-18
is not the mp3 in 263
264 is for the mp4
just asking

---

### Post by Revolutionary101 on 2010-03-20
> **no2498 said:**
> is not the mp3 in 263
264 is for the mp4
just asking

No H.263 and H.264 are both video formats for the MP4 container.

---

### Post by nPoc on 2010-03-24
I'm having this same issue.  Has anyone discovered a solution?  

As a workaround, I'm planning on outputting the video to raw dv, and then re-encoding it with handbrake into h.264.

---

### Post by FakeOutdoorsman on 2010-03-24
Related bug report:

[Bug #546297 videoporama h264 error on startup](https://bugs.launchpad.net/ubuntu/+source/videoporama/+bug/546297)

I'm surprised that videoporama, according to its warning message, wants to place H.264 in an AVI container.  This is generally a bad idea and MP4 or MKV would be much better choices.

---

