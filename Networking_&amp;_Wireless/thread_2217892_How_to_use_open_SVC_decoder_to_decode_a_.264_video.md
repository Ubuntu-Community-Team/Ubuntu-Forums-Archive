---
title: "How to use open SVC decoder to decode a .264 video ?"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by ghada2 on 2014-04-18
I  am trying to use open SVC decoder to decode a .264 video. However, I  noticed that the output video always produces smaller number of frames. 

  

I tried many methods shown below :


> mplayer -fps 24 BBB.264

or :

> mplayer -fps 24 BBB.264 -frames 7200

Only 3599 decoded !!
Displayed video lasts for only 2.5 min instead of the original 5min. 
  ===================
I am also interested in getting a yuv version of the encoded video for PSNR calculation 
I tried 
> mplayer -fps 24 BBB.264 -vo yuv4mpeg

ffmpeg -i stream.yuv -vcodec rawvideo output.yuv
  but the smaller number of frames persists. 


I tried other output formats including PNG and AVI but the problem persists. I would appreciate any advice on this issue.

---

### Post by squakie on 2014-04-18
You could try using VLC to stream the video to a file, converting it.  I use this to capture video/audio from a USB Dazzle DVC-100 to capture old VHS tapes, etc., from analog sources.  It's also possible you may need libdvdcss (from libdvdread4) if the video/input is copy protected.

---

