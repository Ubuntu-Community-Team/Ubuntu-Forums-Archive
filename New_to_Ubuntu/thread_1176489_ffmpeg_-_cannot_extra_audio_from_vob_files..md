---
title: "ffmpeg - cannot extra audio from vob files."
date: 2009-06-02
forum: New to Ubuntu
---

### Post by olddavd on 2009-06-02
Last night I installed ffmpeg following the instructions on:

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

FFmpeg installed and works except when trancoding a vob file to any other format it will not have audio or usually will not transcode. I enabled libmp3lame, gpl, and most of the other codecs.
Some of the commands used are:

ffmpeg -i file.vob -f avi -vcodec mpeg4 -b 800k -g 300 -bf2 -acodec libmp3lame -ab 128000 output.avi

ffmpeg -i file.vob -vcodec wmv2 -b 500 -g 300 output.wmv

ffmpeg -i file.vob -vcodec wmv2 -b 800k -g 300 -acodec wmav2 output.wmv

What I really need is to convert a vob file to a wmv. My mp3 requires smv format video and comes with a converter that will only convert wmv to smv.

Any help would be greatly appreciated.

---

### Post by FakeOutdoorsman on 2009-06-02
> **olddavd said:**
> 
FFmpeg installed and works except when trancoding a vob file to any other format it will not have audio or usually will not transcode.
What version of Ubuntu are you using?  What errors is FFmpeg giving you?

If you want to compile FFmpeg, I recommend getting the most recent source from ffmpeg.org.  Development is active and the source from the Ubuntu repositories is ancient (Jaunty is fairly recent though):

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You can also easily enable the repository FFmpeg to encode to restricted formats such as MP3 and MPEG4:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

