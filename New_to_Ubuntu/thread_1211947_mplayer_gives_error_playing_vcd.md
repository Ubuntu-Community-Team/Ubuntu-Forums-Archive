---
title: "mplayer gives error playing vcd"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by pratiks19 on 2009-07-13
mplayer shows the following error message when I try to play a VCD:

> ioctl dif1: Input/output error

I use the following codecs:
Video: RealVideo Decoder
Audio: AAC (also tried FFmpeg)

The terminal output:

> 
pratik@pratik-laptop:~$ mplayer vcd://1
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://1.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 1
track 02:  adr=1  ctrl=4  format=2  00:21:26  mode: 1
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1100.0 kbps (137.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x288 => 376x288 Planar YV12 
V:   0.0   1/  1 ??% ??% ??,?% 0 0 
GNOME screensaver enabled

Exiting... (End of file)


Kindly help me with this.

---

### Post by carml on 2009-07-13
Did you install the Gstreamer packages or the package named ubuntu-restricted-extras?
If you didn't just go to Applications->Add/remove look for them and install,then retry to play the file and post here the result. :)

---

### Post by pratiks19 on 2009-07-14
i installed w32codecs from the medibuntu repository. 
Now the VCD plays fine, but the error message is displayed once before the video starts playing.

Will install ubuntu-restricted-extras and post the result soon.

---

