---
title: "How can I play or convert .oma files?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by al.adab on 2009-09-21
hi, I'm wondering if anyone knows how to play or convert .oma files (previously transferred on Vista through Sonicstage) to mp3 on Ubuntu? The only "solution" I came across is to use HiMDRenderer but this seems to require Vista + Sonicstage (that's at least the message I got when I tried to use this software through Wine).

---

### Post by sandyd on 2009-09-21
so..... install sonicstage and set the windows version to vista.

---

### Post by al.adab on 2009-09-22
er...I'm on Ubuntu...no Vista in da house.

---

### Post by mike555 on 2009-09-22
check this site ...   it says VLC will play ...
[http://www.file-extensions.org/oma-file-extension](http://www.file-extensions.org/oma-file-extension)

---

### Post by al.adab on 2009-10-07
thanks mike555 I've just tried VLC. Doesn't seem to play or convert .oma files (although .oma is in the list of files it should handle).

---

### Post by howefield on 2009-10-07
Try the answer in this thread...

[http://ubuntuforums.org/showthread.php?p=8065838](http://ubuntuforums.org/showthread.php?p=8065838)

---

### Post by al.adab on 2009-10-12
No success. Tried for hours, to no avail. VLC won't convert .oaa files. Nor will any ffmpeg trick I tried on terminal - following the post. There must be a solution.

---

### Post by MelDJ on 2009-10-12
maybe soundconverter can convert it. sudo apt-get install soundconverter.
or try this nautilus-script which can convert many things: [http://www.gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533](http://www.gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533)

---

### Post by FakeOutdoorsman on 2009-10-12
I am able to convert non-DRM OMA files with FFmpeg:
```
$ wget http://samples.mplayerhq.hu/oma/01-Untitled\(1\).oma
$ ffmpeg -i 01-Untitled\(1\).oma output.wav
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, oma, from '01-Untitled(1).oma':
  Duration: 00:04:24.38, start: 0.000000, bitrate: 132 kb/s
    Stream #0.0: Audio: atrac3, 44100 Hz, stereo, s16, 132 kb/s
Output #0, wav, to 'output.wav':
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   45512kB time=264.20 bitrate=1411.2kbits/s    
video:0kB audio:45512kB global headers:0kB muxing overhead 0.000094%
```

With an OMA with encryption/DRM I get:
```
[oma @ 0x905c420]Encrypted file! Eid: 1
03-Exdous.oma: Error while opening file
```

---

