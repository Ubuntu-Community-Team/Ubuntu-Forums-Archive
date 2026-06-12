---
title: "looking for a reliable program to convert files to mp3"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by Falc7 on 2010-01-04
Hi
I am looking for a good program to convert flv and other file types to mp3. I've tried sound converter, but it is unreliable, sometimes it works, others it dosen't, and sometimes it just mucks up the output. I've also tried winff, but that crashes immediately. Can someone suggest an easy to use and reliable one please

---

### Post by J V on 2010-01-04
you should try _[handbrake]("apt://handbrake-gtk")_

---

### Post by Jonwenger on 2010-01-04
I think the answer to your question is in this thread: [http://ubuntuforums.org/showthread.php?t=852027]("http://ubuntuforums.org/showthread.php?t=852027")

---

### Post by Falc7 on 2010-01-05
thanks guys i'll check these out

---

### Post by paul.gevers on 2010-01-07
> **Falc7 said:**
> I've also tried winff, but that crashes immediately. 

Could you please help me fix this problem. Winff should not crash. So, as a starter, what is the output if you start winff from a terminal? And crashes immediately, does that mean you don't see anything at all?

And, where did you get winff and what version of Ubuntu are you running?

---

### Post by ankspo71 on 2010-01-07
Hi Paul,
I have always had a problem getting WinFF to work for me. I keep getting the " Unknown encoder 'libmp3lame' " error when I try to convert any video to mp3 (and I think ogg too). I was wondering if you knew a work around for this. Do you recommend I uninstall libmp3lame? I don't think I actually need it for anything else, but I thought winff depended on it to create mp3s, so I'm not sure what I should try to do. :D
Thanks

Package details:
winff_1.0.4-2ubuntu2_i386.deb
ubuntu-restricted-extras_36_i386.deb
libmp3lame0_3.98.2+debian-0ubuntu2_i386.deb  
I also have medibuntu installed with win32codecs: w32codecs_20071007-0medibuntu5_i386.deb
Ubuntu 9.10

Output of starting WinFF by command line.
> james@Karmic:~$ winff
[WARNING] Out of OEM specific ** codes, changing to unassigned
[WARNING] Out of unassigned ** codes, assigning $FF

(winff:11718): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:2270: signal `enter' is invalid for instance `0x9b52a60'

(winff:11718): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:2270: signal `leave' is invalid for instance `0x9b52a60'

(winff:11718): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:2270: signal `enter' is invalid for instance `0x9bb74c0'

(winff:11718): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:2270: signal `leave' is invalid for instance `0x9bb74c0'
The output of the conversion:
> FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 24.00 (24/1)
Input #0, flv, from '/home/james/Desktop/test.flv':
  Duration: 00:01:07.08, start: 0.000000, bitrate: 413 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 349 kb/s, 24 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
Unknown encoder 'libmp3lame'
Press Enter to Continue


---

### Post by nothingspecial on 2010-01-07
Winff (or ffmpeg for that matter) will not work with certain media formats unless you do [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

It all looks awfully complicated, but it`s just a matter of copy and paste.

---

### Post by Tahakki on 2010-01-07
Why not just use Sound Converter? It's simple, reliable and in the software store.

---

