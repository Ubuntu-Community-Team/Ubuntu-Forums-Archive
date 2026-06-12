---
title: "Handbrake closes after start"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by dtom2444 on 2009-04-27
I'm trying to convert an mp4 video file to an mp4 PSP compatible file using Handbrake. The problem is that everytime a press start, it just closes. I've also tried other files but only to find the same results. 

Here is the EncodeLog for the first file: 
```
Handbrake Version: 0.9.3 (2008112300)
[10:30:47] hb_scan: path=/home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4, title_index=1
[10:30:47] scan: trying to open with libdvdread
[10:30:47] dvd: not a dvd - trying as a stream/file instead
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4':
  Duration: 00:05:20.99, start: 0.000000, bitrate: 277 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 25.00 tb(r)
[10:30:47] scan: decoding previews for title 1
[10:30:47] scan: 10 previews, 480x360, 25.000 fps, autocrop = 0/0/114/114, aspect 1.33:1, PAR 1:1
[10:30:47] scan: title (0) job->width:256, job->height:368
[10:30:47] libhb: scan thread found 1 valid title(s)
[10:30:47] lingui: Preset: Gaming Consoles->PSP
[10:30:47] 1 job(s) to process
[10:30:47] starting job
[10:30:47] job configuration:
[10:30:47]  * source
[10:30:47]    + /home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4
```

And here is the ActivityLog (i'm posting both because i'm not sure which is relevant):
```
[10:30:00] lingui: Handbrake Version: 0.9.3 (2008112300)
[10:30:00] hb_init: checking cpu count
[10:30:00] hb_init: starting libhb thread
[10:30:00] hb_init: checking cpu count
[10:30:00] hb_init: starting libhb thread
[10:30:13] hb_scan: path=/home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4, title_index=0
[10:30:13] scan: trying to open with libdvdread
[10:30:13] dvd: not a dvd - trying as a stream/file instead
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4':
  Duration: 00:05:20.99, start: 0.000000, bitrate: 277 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 25.00 tb(r)
[10:30:13] scan: decoding previews for title 1
[10:30:13] scan: 10 previews, 480x360, 25.000 fps, autocrop = 0/0/114/114, aspect 1.33:1, PAR 1:1
[10:30:13] scan: title (0) job->width:256, job->height:368
[10:30:13] libhb: scan thread found 1 valid title(s)
[10:30:47] hb_scan: path=/home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4, title_index=1
[10:30:47] scan: trying to open with libdvdread
[10:30:47] dvd: not a dvd - trying as a stream/file instead
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4':
  Duration: 00:05:20.99, start: 0.000000, bitrate: 277 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 25.00 tb(r)
[10:30:47] scan: decoding previews for title 1
[10:30:47] scan: 10 previews, 480x360, 25.000 fps, autocrop = 0/0/114/114, aspect 1.33:1, PAR 1:1
[10:30:47] scan: title (0) job->width:256, job->height:368
[10:30:47] libhb: scan thread found 1 valid title(s)
[10:30:47] lingui: Preset: Gaming Consoles->PSP
[10:30:47] 1 job(s) to process
[10:30:47] starting job
[10:30:47] job configuration:
[10:30:47]  * source
[10:30:47]    + /home/dtom2444/Desktop/DIOYY_-__Epic_Last_Song__Jack_Beats_Remix_.mp4
[10:30:47]    + title 1, chapter(s) 1 to 1
[10:30:47]    + container: mov,mp4,m4a,3gp,3g2,mj2
[10:30:47]    + data rate: 277 kbps
```

Thanks in advance for any help.

---

### Post by blueridgedog on 2009-04-27
If you try and launch handbrake from a terminal, do you get anymore information?

---

