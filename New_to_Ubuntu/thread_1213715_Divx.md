---
title: "Divx"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by mdmorash on 2009-07-15
Is there a good and easy to use Divx-like converter for use in Ubuntu? I've tried to use Wine with Divx but it does not work very well.

---

### Post by stinger30au on 2009-07-15
yep, xvid

xvid is an opens source version of divx, infact xvid is divx spelt backwards

grab a copy of handbrake from getdeb.net and install it and oyur in business

---

### Post by lovinglinux on 2009-07-15
Avidemux can also convert using xvid codec.

---

### Post by 3rdalbum on 2009-07-15
Try and use native programs before turning to Wine, because as you said, things don't always work well in Wine.

You could try one of the above suggestions, or WinFF (which is popular on Windows as well as available on Linux).

If you will be continuously converting video files to Divx/Xvid/(Some other format) you should learn to use ffmpeg on the command-line. It's actually not difficult, and it gives you a phenominal amount of control. Plus, you can set up a script to work through your entire list of pending video conversions overnight. This is what I do.

FFmpeg is pretty easy, here's one command:

```
ffmpeg -i "h2o episode 1.vob" -b 1500k -vcodec libx264 -deinterlace -ab 128k -acodec libmp3lame -threads 2 "h2o_s2d2e1.avi"
```

**Explanation:**

-i "h2o episode 1.vob": The input file
-b 1500k: Use 1500 kilobits per second for the output video (1.5 megabits per second)
-vcodec libx264: Use the "x264" codec for the output video (you can find out the codec names by typing "ffmpeg -formats"
-ab 128k: Use 128 kilobits per second for the output audio - basically standard MP3 quality
-acodec libmp3lame: Use the MP3 codec for the output audio
-threads 2: Use both cores of my computer
"h2o_s2d2e1.avi": Save the output file with this filename (and wrap it in the AVI container format).

I usually use more options to guarantee that I get the exact settings I want, rather than the same settings as the input file. And I put multiple commands in the one text file and then run it, so my CPU works on it all night.

---

### Post by mdmorash on 2009-07-15
This forums great. Thanks for all the ideas everyone.

---

### Post by FakeOutdoorsman on 2009-07-15
> **3rdalbum said:**
> ...
FFmpeg is pretty easy, here's one command:

```
ffmpeg -i "h2o episode 1.vob" -b 1500k -vcodec libx264 -deinterlace -ab 128k -acodec libmp3lame -threads 2 "h2o_s2d2e1.avi"
```

I usually use more options to guarantee that I get the exact settings I want, rather than the same settings as the input file. And I put multiple commands in the one text file and then run it, so my CPU works on it all night.

You'll generally get better results when using the libx264 presets when encoding to H.264 video.  These are available in Intrepid's FFmpeg from the Ubuntu repository but you will need to enable restricted encoders.  Older Ubuntu releases will need to compile FFmpeg to have access to the presets.  Both procedures are outlined here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

**Example One-Pass CRF:**
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 22 -threads 0 output.mp4
```

For more info, I recommend reading the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) [rob.opendot.cl].

---

