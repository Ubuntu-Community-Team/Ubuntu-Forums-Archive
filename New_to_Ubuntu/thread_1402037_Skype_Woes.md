---
title: "Skype Woes"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by JoeGoe on 2010-02-08
Hi,

This keeps happening.  When ever I receive a video from someone in Skype, I can only see a slightly transparent white background.  If it matters, this happens when watching dvds in vlc

---

### Post by usererror on 2010-02-08
something is not set up right with your video.  My skype works great as does dvd playing in vlc.

if you run vlc from a terminal and then play a dvd can you copy paste the output?  How about via mplayer?

---

### Post by JoeGoe on 2010-02-08
> **usererror said:**
> something is not set up right with your video.  My skype works great as does dvd playing in vlc.

if you run vlc from a terminal and then play a dvd can you copy paste the output?  How about via mplayer?

Okay, If I play a DVD in mplayer media player it says seek error.  Movie player I can only see the video with no sound Gnome mPlayer works fine, but still no Skype.  If I run DVD in terminal with vlc, it player perfectly.  It doesn't show controls for seeking through the movie.  I have no idea what that output thingie is.

---

### Post by usererror on 2010-02-08
what steps did you follow to install dvd playback?  it is really odd that one player works, but another does not.  

Skype apparently does not return any useful information when run via terminal.  vlc should, as would mplayer...

Open mplayer up via Applications > Accessories > Terminal then type 

```
mplayer dvd://
```

then it should open and play your dvd, post the output from terminal.

you should get a bunch of stuff that looks like this (but this is for an avi file, but you should see SOMETHING):

```

mark@Office:~/Videos$ mplayer MVI_2056.AVI 
Creating config file: /home/mark/.mplayer/config
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing MVI_2056.AVI.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  11732.3 kbps (1432.2 kbyte/s)
Clip info:
 Digitization Time: SAT FEB 28 15:04:31 2009

 Software: CanonMVI06
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 705.6 kbit/100.00% (ratio: 88200->88200)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x7ff25ab7b680]BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0x7ff25ab7b680]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x7ff25ab7b680]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x7ff25ab7b680]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x7ff25ab7b680]640x480 -> 640x480
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  13.5 V:  13.6 A-V: -0.087 ct: -0.012 410/410  8%  6%  0.1% 0 0 

Exiting... (End of file)

```

---

### Post by JoeGoe on 2010-02-08
josephgomez@josephgomez-laptop:~$ mplayer dvd://
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 2 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000180
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000e513
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: lpcm (stereo) language:  aid: 160.
number of audio channels on disk: 1.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [dvdpcm] Uncompressed DVD/VOB LPCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16be, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dvdpcm] afm: dvdpcm (Uncompressed DVD/VOB LPCM)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 48000Hz 2ch s16be (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
[mpeg2video @ 0x2fd4ae0]ac-tex damaged at 18 10
[mpeg2video @ 0x2fd4ae0]Warning MVs not available
[mpeg2video @ 0x2fd4ae0]concealing 900 DC, 900 AC, 900 MV errors
A:  36.0 V:  36.0 A-V:  0.001 ct:  0.068 1074/1074  8%  0%  9.3% 1 0 
Exiting... (Quit)
josephgomez@josephgomez-laptop:~$





I can't access the DVD menus

---

### Post by usererror on 2010-02-09
Can you post the following from your terminal?

```
lspci | grep VGA
```

Do you have 3D effects turned on?  Can you turn off all desktop effects and try skype again?

---

### Post by JoeGoe on 2010-02-27
josephgomez@josephgomez-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
josephgomez@josephgomez-laptop:~$

---

