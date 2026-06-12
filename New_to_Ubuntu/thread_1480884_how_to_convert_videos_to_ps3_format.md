---
title: "how to convert videos to ps3 format?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by ashora on 2010-05-12
i want to convert some videos to play on my ps3..i tryed winFF but i got this error message..what does that mean? any other way to convert them or to fixed the winFF?

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/cindy/LimeWire/Saved/Hollywood Undead No. 5 Music Video.mp4':
  Duration: 00:03:27.53, start: 0.000000, bitrate: 313 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1(und): Audio: aac, 24000 Hz, stereo, s16
Unknown encoder 'libx264'
Press Enter to Continue

---

### Post by adam22 on 2010-05-12
There's no such thing as PS3 format. Your PS3 will play pretty much any video file, including .avi, .mp4, .flv, etc. Simply put the movie on a flash drive and stick it in the ps3, and then go to videos and push triangle on the flash drive and select show all.

Even better, if you can, make a media server and you can just play the files without using discs or a flash drive.

---

### Post by ashora on 2010-05-12
then how do i convert them..i need Mpeg-4 i think..oh and flv wont play on the ps3 thats a flash video not supported by the ps3

---

### Post by adam22 on 2010-05-12
What format is the file in that is requiring you to convert it? Avidemux will do the trick...see [this](http://justanotherwebblog.wordpress.com/2008/06/07/how-to-convert-movies-to-mp4/).

---

### Post by paul.gevers on 2010-05-12
Please install libavcodec-extra-52 and you will have libx264 available in ffmpeg.

---

### Post by ashora on 2010-05-12
alright i will try

i end up getting this 

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/cindy/LimeWire/Saved/Hollywood Undead No. 5 Music Video.mp4':
  Duration: 00:03:27.53, start: 0.000000, bitrate: 313 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1(und): Audio: aac, 24000 Hz, stereo, s16
Unknown encoder 'libfaac'
Press Enter to Continue

---

### Post by bacardiandwatermelon on 2010-05-12
If you feel like having the latest and greatest you could follow this..

[http://ubuntuforums.org/showthread.php?t=786095&highlight=x264+ffmpeg](http://ubuntuforums.org/showthread.php?t=786095&highlight=x264+ffmpeg)

---

### Post by ashora on 2010-05-12
i tryed Avidemux (GTK+) i put the video in and select my settings and then i hit save..but then nothing happens it save a thumb nail but no video...did i do it wrong? alright _[bacardiandwatermelon]("http://ubuntuforums.org/member.php?u=84356")_ i will try

---

### Post by ashora on 2010-05-12
it says ** "Get the most current source files from the official x264 git repository, compile, and install" **where do i get that and how do i compile and install?...never mind i think i got it

---

### Post by ashora on 2010-05-12
i cant get number 4 in the direction for 9.10 to work help please?

---

### Post by ashora on 2010-05-12
> **adam22 said:**
> What format is the file in that is requiring you to convert it? Avidemux will do the trick...see [this]("http://justanotherwebblog.wordpress.com/2008/06/07/how-to-convert-movies-to-mp4/").

oops so sorry didnt see the link!! thanks so much that should work i will go try it!! again sorry

---

### Post by ashora on 2010-05-12
> **adam22 said:**
> What format is the file in that is requiring you to convert it? Avidemux will do the trick...see [this]("http://justanotherwebblog.wordpress.com/2008/06/07/how-to-convert-movies-to-mp4/").

it worked thanks so much!!!! :popcorn::guitar:

---

### Post by ashora on 2010-05-13
i found out how to fixed my ffmpeg problem silly me should of used the search lol

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Dex73 on 2010-11-10
> **ashora said:**
> i found out how to fixed my ffmpeg problem silly me should of used the search lol

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I can't get my flv files to work on my PS3. I have files that just won't play. Can you tell me what you used and exactly how you set them up? I'm still basically a noob. Please be sure not to skip anything you consider obvious. Sometimes I get great help, but have trouble following it.

---

