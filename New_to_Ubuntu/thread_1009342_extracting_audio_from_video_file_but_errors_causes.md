---
title: "extracting audio from video file but errors causes it to stop 10mins into the file"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by simtaalo on 2008-12-12
i've used the ffmpeg -i command to extract audio from a video file. it works fine til something causes it to stop 10minutes into the video file (file is 40minutes long). below is the output when the command is run

```
ffmpeg -i filename.rmvb file.mp3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:28:49, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[NULL @ 0x7f36039dd8d0]Unsupported video codec
Input #0, rm, from '**filename**':
  Duration: 00:42:10.0, start: 0.000000, bitrate: 582 kb/s
  Stream #0.0: Video: RV40 / 0x30345652, 512x384, 512 kb/s, 12.00 fps(r)
  Stream #0.1: Audio: cook, 44100 Hz, mono, 64 kb/s
  Stream #0.2: Data: 0x0000
Output #0, mp3, to 'file.mp3':
  Stream #0.0: Audio: mp3, 44100 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
*** glibc detected *** ffmpeg: double free or corruption (fasttop): 0x000000000063fac0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f36029f308a]
/lib/libc.so.6(cfree+0x8c)[0x7f36029f6c1c]
/usr/lib/libavformat.so.1d(av_destruct_packet+0xd)[0x7f3603a6667d]
ffmpeg(main+0x1bc2)[0x40c5f2]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f360299d1c4]
ffmpeg[0x4038e9]
======= Memory map: ========
00400000-00412000 r-xp 00000000 08:01 978398                             /usr/bin/ffmpeg
00611000-00612000 rw-p 00011000 08:01 978398                             /usr/bin/ffmpeg
00612000-00660000 rw-p 00612000 00:00 0                                  [heap]
7f35f8000000-7f35f8021000 rw-p 7f35f8000000 00:00 0 
7f35f8021000-7f35fc000000 ---p 7f35f8021000 00:00 0 
7f35ffb9c000-7f35ffba9000 r-xp 00000000 08:01 729108                     /lib/libgcc_s.so.1
7f35ffba9000-7f35ffda9000 ---p 0000d000 08:01 729108                     /lib/libgcc_s.so.1
7f35ffda9000-7f35ffdaa000 rw-p 0000d000 08:01 729108                     /lib/libgcc_s.so.1
7f35ffdaa000-7f35ffdaf000 r-xp 00000000 08:01 976225                     /usr/lib/libXdmcp.so.6.0.0
7f35ffdaf000-7f35fffae000 ---p 00005000 08:01 976225                     /usr/lib/libXdmcp.so.6.0.0
7f35fffae000-7f35fffaf000 rw-p 00004000 08:01 976225                     /usr/lib/libXdmcp.so.6.0.0
7f35fffaf000-7f35fffb1000 r-xp 00000000 08:01 976214                     /usr/lib/libXau.so.6.0.0
7f35fffb1000-7f36001b0000 ---p 00002000 08:01 976214                     /usr/lib/libXau.so.6.0.0
7f36001b0000-7f36001b1000 rw-p 00001000 08:01 976214                     /usr/lib/libXau.so.6.0.0
7f36001b1000-7f36001b3000 r-xp 00000000 08:01 729691                     /lib/libdl-2.7.so
7f36001b3000-7f36003b3000 ---p 00002000 08:01 729691                     /lib/libdl-2.7.so
7f36003b3000-7f36003b5000 rw-p 00002000 08:01 729691                     /lib/libdl-2.7.so
7f36003b5000-7f36003d0000 r-xp 00000000 08:01 977147                     /usr/lib/libxcb.so.1.0.0
7f36003d0000-7f36005cf000 ---p 0001b000 08:01 977147                     /usr/lib/libxcb.so.1.0.0
7f36005cf000-7f36005d0000 rw-p 0001a000 08:01 977147                     /usr/lib/libxcb.so.1.0.0
7f36005d0000-7f36005d1000 r-xp 00000000 08:01 977143                     /usr/lib/libxcb-xlib.so.0.0.0
7f36005d1000-7f36007d0000 ---p 00001000 08:01 977143                     /usr/lib/libxcb-xlib.so.0.0.0
7f36007d0000-7f36007d1000 rw-p 00000000 08:01 977143                     /usr/lib/libxcb-xlib.so.0.0.0
7f36007d1000-7f36008d0000 r-xp 00000000 08:01 976208                     /usr/lib/libX11.so.6.2.0
7f36008d0000-7f3600acf000 ---p 000ff000 08:01 976208                     /usr/lib/libX11.so.6.2.0
7f3600acf000-7f3600ad4000 rw-p 000fe000 08:01 976208                     /usr/lib/libX11.so.6.2.0
7f3600ad4000-7f3600ada000 r-xp 00000000 08:01 977003                     /usr/lib/libraw1394.so.8.2.0
7f3600ada000-7f3600cd9000 ---p 00006000 08:01 977003                     /usr/lib/libraw1394.so.8.2.0
7f3600cd9000-7f3600cda000 rw-p 00005000 08:01 977003                     /usr/lib/libraw1394.so.8.2.0
7f3600cda000-7f3600ce9000 r-xp 00000000 08:01 976482                     /usr/lib/libfaac.so.0.0.0
7f3600ce9000-7f3600ee8000 ---p 0000f000 08:01 976482                     /usr/lib/libfaac.so.0.0.0
7f3600ee8000-7f3600eeb000 rw-p 0000e000 08:01 976482                     /usr/lib/libfaac.so.0.0.0
7f3600eeb000-7f3600f66000 r-xp 00000000 08:01 977137                     /usr/lib/libx264.so.57
7f3600f66000-7f3601165000 ---p 0007b000 08:01 977137                     /usr/lib/libx264.so.57
7f3601165000-7f3601167000 rw-p 0007a000 08:01 977137                     /usr/lib/libx264.so.57
7f3601167000-7f360116b000 rw-p 7f3601167000 00:00 0 
7f360116b000-7f36011e8000 r-xp 00000000 08:01 977161                     /usr/lib/libxvidcore.so.4.1
7f36011e8000-7f36013e7000 ---p 0007d000 08:01 977161                     /usr/lib/libxvidcore.so.4.1
7f36013e7000-7f36013f2000 rw-p 0007c000 08:01 977161                     /usr/lib/libxvidcore.so.4.1
7f36013f2000-7f360145c000 rw-p 7f36013f2000 00:00 0 
7f360145c000-7f3601476000 r-xp 00000000 08:01 977049                     /usr/lib/libvorbisenc.so.2.0.3
7f3601476000-7f3601675000 ---p 0001a000 08:01 977049                     /usr/lib/libvorbisenc.so.2.0.3
7f3601675000-7f3601834000 rw-p 00019000 08:01 977049                     /usr/lib/libvorbisenc.so.2.0.3
7f3601834000-7f3601852000 r-xp 00000000 08:01 976995                     /usr/lib/libvorbis.so.0.4.0
7f3601852000-7f3601a51000 ---p 0001e000 08:01 976995                     /usr/lib/libvorbis.so.0.4.0
7f3601a51000-7f3601a5f000 rw-p 0001d000 08:01 976995                     /usr/lib/libvorbis.so.0.4.0
7f3601a5f000-7f3601aa2000 r-xp 00000000 08:01 977077                     /usr/lib/libtheora.so.0.3.2
7f3601aa2000-7f3601ca1000 ---p 00043000 08:01 977077                     /usr/lib/libtheora.so.0.3.2
7f3601ca1000-7f3601ca3000 rw-p 00042000 08:01 977077                     /usr/lib/libtheora.so.0.3.2
7f3601ca3000-7f3601d09000 r-xp 00000000 08:01 976855                     /usr/lib/libmp3lame.so.0.0.0
7f3601d09000-7f3601f08000 ---p 00066000 08:01 976855                     /usr/lib/libmp3lame.so.0.0.0
7f3601f08000-7f3601f0a000 rw-p 00065000 08:01 976855                     /usr/lib/libmp3lame.so.0.0.0
7f3601f0a000-7f3601f3b000 rw-p 7f3601f0a000 00:00 0 
7f3601f3b000-7f3601f48000 r-xp 00000000 08:01 976667                     /usr/lib/libgsm.so.1.0.12
7f3601f48000-7f3602147000 ---p 0000d000 08:01 976667                     /usr/lib/libgsm.so.1.0.12
7f3602147000-7f3602148000 rw-p 0000c000 08:01 976667                     /usr/lib/libgsm.so.1.0.12
7f3602148000-7f3602152000 r-xp 00000000 08:01 976270                     /usr/lib/liba52-0.7.4.so
7f3602152000-7f3602351000 ---p 0000a000 08:01 976270                     /usr/lib/liba52-0.7.4.so
7f3602351000-7f3602352000 rw-p 00009000 08:01 976270                     /usr/lib/liba52-0.7.4.so
7f3602352000-7f3602353000 rw-p 7f3602352000 00:00 0 
7f3602353000-7f3602362000 r-xp 00000000 08:01 976410                     /usr/lib/libdc1394_control.so.13.0.0
7f3602362000-7f3602562000 ---p 0000f000 08:01 976410                     /usr/lib/libdc1394_control.so.13.0.0
7f3602562000-7f3602563000 rw-p 0000f000 08:01 976410                     /usr/lib/libdc1394_control.so.13.0.0
7f3602563000-7f3602568000 r-xp 00000000 08:01 976906                     /usr/lib/libogg.so.0.5.3
7f3602568000-7f3602767000 ---p 00005000 08:01 976906                     /usr/lib/libogg.so.0.5.3
7f3602767000-7f3602768000 rw-p 00004000 08:01 976906                     /usr/lib/libogg.so.0.5.3
7f3602768000-7f360277e000 r-xp 00000000 08:01 977163                     /usr/lib/libz.so.1.2.3.3
7f360277e000-7f360297e000 ---p 00016000 08:01 977163                     /usr/lib/libz.so.1.2.3.3
7f360297e000-7f360297f000 rw-p 00016000 08:01 977163                     /usr/lib/libz.so.1.2.3.3
7f360297f000-7f3602ad7000 r-xp 00000000 08:01 729688                     /lib/libc-2.7.so
7f3602ad7000-7f3602cd7000 ---p 00158000 08:01 729688                     /lib/libc-2.7.so
7f3602cd7000-7f3602cda000 r--p 00158000 08:01 729688                     /lib/libc-2.7.so
7f3602cda000-7f3602cdc000 rw-p 0015b000 08:01 729688                     /lib/libc-2.7.so
7f3602cdc000-7f3602ce1000 rw-p 7f3602cdc000 00:00 0 
7f3602ce1000-7f3602cf7000 r-xp 00000000 08:01 729702                     /lib/libpthread-2.7.so
7f3602cf7000-7f3602ef7000 ---p 00016000 08:01 729702                     /lib/libpthread-2.7.so
7f3602ef7000-7f3602ef9000 rw-p 00016000 08:01 729702                     /lib/libpthread-2.7.so
7f3602ef9000-7f3602efd000 rw-p 7f3602ef9000 00:00 0 
7f3602efd000-7f3602f7d000 r-xp 00000000 08:01 729692                     /lib/libm-2.7.so
7f3602f7d000-7f360317c000 ---p 00080000 08:01 729692                     /lib/libm-2.7.so
7f360317c000-7f360317e000 rw-p 0007f000 08:01 729692                     /lib/libm-2.7.so
7f360317e000-7f3603184000 r-xp 00000000 08:01 976325                     /usr/lib/libavutil.so.1d.49.3.0
7f3603184000-7f3603384000 ---p 00006000 08:01 976325                     /usr/lib/libavutil.so.1d.49.3.0
7f3603384000-7f3603385000 rw-p 00006000 08:01 976325                     /usr/lib/libavutil.so.1d.49.3.0
7f3603385000-7f3603387000 rw-p 7f3603385000 00:00 0 
7f3603387000-7f36037d3000 r-xp 00000000 08:01 976321                     /usr/lib/libavcodec.so.1d.51.38.0
7f36037d3000-7f36039d3000 ---p 0044c000 08:01 976321                     /usr/lib/libavcodec.so.1d.51.38.0Aborted

```

it looks like "libavcodec.so.1d.53.38" is going wrong? anyway of sorting this out?

N.B - i tried using the mplayer -dumpaudio way of doing it and this doesn't work at all.

---

### Post by Dedoimedo on 2008-12-12
Have you tried other files? Could this file be corrupted?
Dedoimedo

---

### Post by tomtom1982 on 2008-12-12
You also can try to use vlc media player to extract the audio file (via streaming-assistent) to wav, mp3, ogg, flac etc.

---

### Post by simtaalo on 2008-12-12
right, i tried another file in the same rmvb format and the same thing occured, but with an avi file it ran the whole length error free.

so obviously there is a problem with the rmvb format, but it *should* be able to do it all the way if it can do 10mins of it.

so for short term what is the best way to convert an rmvb file to avi?

if anyone does know how to fix it so it can do it from the rmvb file i would be interested to know that too.

thanks

---

### Post by Bachstelze on 2008-12-12
Do this instead:

```
ffmpeg -i file.rmvb -vn -acodec mp3 -ab 128k file.mp3
```

---

### Post by simtaalo on 2008-12-13
> **HymnToLife said:**
> Do this instead:

```
ffmpeg -i file.rmvb -vn -acodec mp3 -ab 128k file.mp3
```

threw up exactly the same error

---

