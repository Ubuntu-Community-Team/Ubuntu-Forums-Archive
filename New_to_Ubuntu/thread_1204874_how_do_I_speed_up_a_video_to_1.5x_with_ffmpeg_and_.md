---
title: "how do I speed up a video to 1.5x with ffmpeg and yuvfps?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by davidstri on 2009-07-05
I have a video that I want to speed up to 1.5x. I got it to speed up to 2x with the command ```
ffmpeg -i input.wmv -f yuv4mpegpipe - | yuvfps -s 50:1 -r 50:1  | ffmpeg -f yuv4mpegpipe -i - -b 6k -y output.avi
```
but when I use this command ```
ffmpeg -i input.wmv -f yuv4mpegpipe - | yuvfps -s 37.5:1 -r 37.5:1  | ffmpeg -f yuv4mpegpipe -i - -b 6k -y output.avi
```, it doesn't give me an error but it makes a video that is 5.5kbs. I am thinking that it is a problem with the frame rate and the bit rate, but I really don't know. Please help. Thanks

BTW the output of the second command that makes a 5.5kb video gives me this

```
FFmpeg version SVN-r19334, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul  3 2009 13:43:59, gcc: 4.3.3
FFmpeg version SVN-r19334, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul  3 2009 13:43:59, gcc: 4.3.3
[wmv3 @ 0x8f1afa0]Extra data: 8 bits left, value: 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'vloggin.wmv':
  Duration: 00:04:44.71, start: 5.000000, bitrate: 3927 kb/s
    Stream #0.0(eng): Audio: wmav2, 48000 Hz, 2 channels, s16, 192 kb/s
    Stream #0.1(eng): Video: wmv3, yuv420p, 1024x576, 3673 kb/s, 25 tbr, 1k tbn, 1k tbc
[wmv3 @ 0x8f1afa0]Extra data: 8 bits left, value: 0
Output #0, yuv4mpegpipe, to 'pipe:':
    Stream #0.0(eng): Video: rawvideo, yuv420p, 1024x576, q=2-31, 200 kb/s, 90k tbn, 25 tbc
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
   INFO: [yuvfps] yuv2fps (version 0.2) is a general frame resampling utility for yuv streams
   INFO: [yuvfps] (C) 2002 Alfonso Garcia-Patino Barbolani <barbolani@jazzfree.com>
   INFO: [yuvfps] yuvfps -h for help, or man yuvfps
Input #0, yuv4mpegpipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: rawvideo, yuv420p, 1024x576, 37 tbr, 37 tbn, 37 tbc
Output #0, avi, to 'vlog.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 1024x576, q=2-31, 6 kb/s, 37 tbn, 37 tbc
Stream mapping:
  Stream #0.0 -> #0.0
frame=    0 fps=  0 q=0.0 Lsize=       6kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead inf%
```

---

