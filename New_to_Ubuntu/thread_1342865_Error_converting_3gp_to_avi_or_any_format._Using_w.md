---
title: "Error converting 3gp to avi or any format. Using winff,  Unknown encoder 'libxvid'"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by philinux on 2009-12-01
Any help appreciated. The 3gp plays with movie player but with no sound hence trying to convert. Vid plays fine on mobile phone.

```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/philcb/Desktop/MOV00215.3GP':
  Duration: 00:00:37.20, start: 0.000000, bitrate: 145 kb/s
    Stream #0.0(jpn): Video: h263, yuv420p, 176x144 [PAR 12:11 DAR 4:3], 29.97 tbr, 250 tbn, 29.97 tbc
    Stream #0.1(jpn): Audio: samr / 0x726D6173, 8000 Hz, mono, s16
Unknown encoder 'libxvid'
```

---

### Post by paul.gevers on 2009-12-01
> **philinux said:**
> 
Unknown encoder 'libxvid'[/CODE]

Do you have libavcodec-extra-52 or libavcodec-unstripped-52 installed?

---

### Post by philinux on 2009-12-01
> **paul.gevers said:**
> Do you have libavcodec-extra-52 or libavcodec-unstripped-52 installed?

Neither.

```
philcb@philcb-desktop:~$ sudo apt-get install libavcodec-unstripped-52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libavcodec-extra-52 libopenjpeg2
The following packages will be REMOVED
  libavcodec52
The following NEW packages will be installed
  libavcodec-extra-52 libavcodec-unstripped-52 libopenjpeg2
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/2,322kB of archives.
After this operation, 324kB of additional disk space will be used
Do you want to continue [Y/n]? y
dpkg: libavcodec52: dependency problems, but removing anyway as you requested:
 mplayer depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 mencoder depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 vlc-nox depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 mplayer-nogui depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libquicktime1 depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
(Reading database ... 145998 files and directories currently installed.)
Removing libavcodec52 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libopenjpeg2.
(Reading database ... 145987 files and directories currently installed.)
Unpacking libopenjpeg2 (from .../libopenjpeg2_1.3+dfsg-4_amd64.deb) ...
Selecting previously deselected package libavcodec-extra-52.
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_amd64.deb) ...
Selecting previously deselected package libavcodec-unstripped-52.
Unpacking libavcodec-unstripped-52 (from .../libavcodec-unstripped-52_4%3a0.5+svn20090706-2ubuntu3_amd64.deb) ...
Setting up libopenjpeg2 (1.3+dfsg-4) ...

Setting up libavcodec-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libavcodec-unstripped-52 (4:0.5+svn20090706-2ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Now I get.

```
Unsupported codec (id=73728) for input stream #0.1
```

---

### Post by FakeOutdoorsman on 2009-12-01
FFmpeg from the repository does not support decoding of AMR audio.  If you want to use FFmpeg or WinFF to convert this file, you will have to compile FFmpeg yourself:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

...and for other users who get the same "unknown encoder" problem and want to know why that error comes up:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in WinFF](http://ubuntuforums.org/showpost.php?p=8298012&postcount=20)

---

### Post by philinux on 2009-12-01
> **FakeOutdoorsman said:**
> FFmpeg from the repository does not support decoding of AMR audio.  If you want to use FFmpeg or WinFF to convert this file, you will have to compile FFmpeg yourself:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

...and for other users who get the same "unknown encoder" problem and want to know why that error comes up:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in WinFF](http://ubuntuforums.org/showpost.php?p=8298012&postcount=20)

Ah gotcha. I think I used mobile media converter last time but I'm using 64 bit now and their deb is for 32 bit.

---

