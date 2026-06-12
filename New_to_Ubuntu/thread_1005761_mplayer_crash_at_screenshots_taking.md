---
title: "mplayer crash at screenshots taking"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by netimen on 2008-12-08
After to-days updating mplayer started to crash at taking screenshots with following error log:
```
sending VFCTRL_SCREENSHOT!
*** screenshot 'shot0001.png' ***
libpng error: Write Error


MPlayer interrupted by signal 11 in module: filter_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by andrew.46 on 2008-12-09
Hi,

Well the newest version runs -vf screenshot perfectly:

```
andrew@skamandros:~/Desktop$ mplayer -vf screenshot 100_0057.MOV 
**[COLOR="Red"]MPlayer dev-SVN-r28053-4.3.2 (C) 2000-2008 MPlayer Team[/COLOR]**
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing 100_0057.MOV.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [jpeg]  640x480  24bpp  14.991 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 comments: EASTMAN KODAK COMPANY  KODAK M853 ZOOM DIGITAL CAMERA
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, u8, 0.0 kbit/0.00% (ratio: 0->11025)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [oss] 11025Hz 1ch u8 (1 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x89fff20]No accelerated colorspace conversion found.
[swscaler @ 0x89fff20]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 640x480 => 640x480 Planar YV12 
[B][COLOR="Red"]sending VFCTRL_SCREENSHOT!003 ct: -0.039   0/  0 12%  1%  0.3% 2 0 
*** screenshot 'shot0001.png' ***[/COLOR][/B]
A: 149.8 V: 149.8 A-V: -0.000 ct: -0.014   0/  0  8%  0%  0.3% 2 0 

Exiting... (End of file)
```

I have written a guide to using the latest svn MPlayer:

[[Howto] Successfully install the svn mplayer + gmplayer + all the codecs.]("http://ubuntuforums.org/showthread.php?t=558538")

It is a bit of work to get going but well worthwhile.

  Andrew

---

