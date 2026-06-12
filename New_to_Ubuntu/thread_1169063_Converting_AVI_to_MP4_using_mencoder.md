---
title: "Converting AVI to MP4 using mencoder"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by psychx on 2009-05-24
I need help converting an AVI to MP4. I am using mencoder. My goal is to convert AVI files into MP4, so that they can be transferred and playable on a Sony PSP 3000. It is my understanding that the PSP requires video to be in MP4 format, similar to the PS3.

Here is what I am doing:

```
mike@mike-linux:~$ mencoder '/home/mike/Desktop/pilot1.avi' -o '/home/mike/Desktop/pilot1.mp4' -oac copy -ovc lavc -lavcopts vcodec=mpeglvideo -of mpeg
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.53GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _MPEG_. See -of help.
success: format: 0  data: 0x0 - 0x15de8000
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  976.4 kbps (119.2 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:624x352  fps:23.98  ftime:=0.0417
PACKET SIZE: 2048 bytes, deltascr: 245760
Cannot find codec 'mpeglvideo' in libavcodec...
Couldn't open video filter 'lavc'.
Failed to open the encoder.

Exiting...

```

The string that I am using for mencoder is:```
mencoder original.avi -o new.mp4 -oac copy -ovc lavc -lavcopts vcodec=mpeg1video -of mpeg
``` ; of course changing the video files to the correct path/file.

It does not seem to be working, and I think I am missing the mpeglvideo codec. I notice that I have libavcodec-unstripped-51 from Synaptic Package Manager. I also see libavcodec51 (which I do not have downloaded).. I'm not sure what to do from here.

Can anyone shed some light on this for me? I very much appreciate your time. Thank you,

Mike

---

### Post by blueridgedog on 2009-05-24
I can't comment on mencoder, but I think handbrake can do what you are after.

---

### Post by psychx on 2009-05-24
Thank you very much. Handbrake seems to be running flawlessly. I am waiting for this video to be done encoding, but so far, it seems like it is doing an excellent job. If I don't post back here, then everything has worked. Helped me out a bunch, I have been using Terminal for some time now. Once again, I really appreciate it.

---

### Post by blueridgedog on 2009-05-24
I generally use handbrake to put content on my video iPod and really like it.  I hope it works for you as it is a great program.

---

### Post by powel212 on 2009-05-24
I would also recommend Avidemux as a mencoder front end. I love it as it is easy to use and flawlessly creates very high quality videos.

Powel

---

