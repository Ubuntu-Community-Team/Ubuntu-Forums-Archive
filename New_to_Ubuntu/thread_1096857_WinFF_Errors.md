---
title: "WinFF Errors"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-03-15
I have been trying to use winff to convert a batch of AVI files into an iPod compatible format.

I used the following repo to download the program from:
[https://launchpad.net/~paul-climbing/+archive/ppa](https://launchpad.net/~paul-climbing/+archive/ppa)

I used the following preset files (to utilse the "iPod preset"):
[http://winff.org/winffwiki/Presets](http://winff.org/winffwiki/Presets)

When I try and convert a mp4 video using an iPod preset I get the following error:

```

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/john/MyDownloads/TED/videos/AdamGrosser_2007.mp4':
  Duration: 00:03:31.1, start: 0.000000, bitrate: 455 kb/s
    Stream #0.0(eng): Audio: mpeg4aac, 44100 Hz, stereo
    Stream #0.1(eng): Video: h264, yuv420p, 432x240 [PAR 0:1 DAR 0:1], 24.00 tb(r)
Unknown encoder 'h264'
Press Enter to Continue

```

When I try and convert an mp4 file into an AVI:
```

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/john/MyDownloads/TED/videos/AimeeMullins_1998.mp4':
  Duration: 00:20:43.5, start: 0.000000, bitrate: 460 kb/s
    Stream #0.0(eng): Audio: mpeg4aac, 44100 Hz, stereo
    Stream #0.1(eng): Video: h264, yuv420p, 320x240 [PAR 0:1 DAR 0:1], 29.97 tb(r)
Unknown encoder 'xvid'
Press Enter to Continue

```

So, basically I am unable to use WinFF at all!

Any thoughts on this?

Thanks in advance!

---

### Post by oldos2er on 2009-03-15
Do you have libmpeg4ip-0 installed?

---

### Post by abhiroopb on 2009-03-15
Thanks but got it to work...i used the default presets installed of installing the ones on the website!

---

### Post by paul.gevers on 2009-03-16
Which version of Ubuntu do you have and which version did you install from the ppa? It should work if you choose the same version. If not, I really want to know.

In the mean time, the package has the proper preset file included in /usr/share/winff/ but you need to move that over the standard preset file. It is described in the /usr/share/doc/winff/README.Debian file and [here.]("http://code.google.com/p/winff/wiki/InstallPresetsxml")

---

### Post by abhiroopb on 2009-03-16
I have intrepid, and I am using the intrepid repo from your ppa. 

The first time round I did a clean install and used the preset file I found on your website (this didn't work and kept throwing up those errors).

The next time I did a clean install and just used the presets that were already available in the program and that seemed to work fine. I didn't have to move it from /usr/share/winff.

Thanks for the software!

---

### Post by paul.gevers on 2009-03-16
> **abhiroopb said:**
> I have intrepid, and I am using the intrepid repo from your ppa. 

The first time round I did a clean install and used the preset file I found on your website (this didn't work and kept throwing up those errors).

Do I understand correctly that you installed the preset file before running the program? Why?

> **abhiroopb said:**
> 
The next time I did a clean install and just used the presets that were already available in the program and that seemed to work fine. I didn't have to move it from /usr/share/winff.

This just uses the last file you installed in the previous session, because if there is no file in ~/.winff/presets.xml than the one from /usr/share/winff is copied before any other execution. However, when it's there already, it's used. When you remove the program this file is NOT removed (not allowed by policy).

> **abhiroopb said:**
> Thanks for the software!

No thanks. But BiggMatt is to thank (see [winff.org ]("http://winff.org") website ;) )

---

### Post by abhiroopb on 2009-03-16
No, sorry I ran the program, and then copied the file over.

Fair enough...well the programme works great now :)

---

### Post by froggontherocks on 2009-06-23
I installed WinFF from the normal ubuntu repositories and got this error so i updated it from the repository listed on the programs website and this is the output I'm getting I've checked and all dependencies should be installed how can i get this to work? 

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
[mpeg @ 0x71ca60]invalid dts/pts combination
    Last message repeated 10 times
Input #0, mpeg, from '/home/froggontherocks/Videos/Family Videos/012.MPG':
  Duration: 00:00:01.32, start: 0.177778, bitrate: 760 kb/s
    Stream #0.0[0x1c0]: Audio: mp2, 32000 Hz, mono, s16, 32 kb/s
    Stream #0.1[0x1e0]: Video: mpeg1video, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 104857 kb/s, 25 tbr, 90k tbn, 25 tbc
Unknown encoder 'libx264'
Press Enter to Continue

---

### Post by paul.gevers on 2009-06-23
> **froggontherocks said:**
> I've checked and all dependencies should be installed how can i get this to work? 

Unknown encoder 'libx264'

Do you have libavcodec-unstripped-52 installed?

---

