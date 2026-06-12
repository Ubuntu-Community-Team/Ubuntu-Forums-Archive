---
title: "Audio/Video skipping;Dragon Player Works"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by grewolf on 2010-05-07
I have recently upgraded to Lucid Lynx from Karmic koala.  Karmic was great and I had no issues that I was aware of.  Now in Lucid lynx I have audio and video skipping in all the players I use eg. amarok, vlc, rytmbox, xine.  The only one that works is Dragon Player and it has some other issues.  

It seems like lots of people have had problems with skipping in Lucid and I was hoping that if I could understand why dragon player works and (for example) why vlc doesn't I could be well on my way to having vlc work (my preferred player)

Looking for a good place to start trouble shooting.  I have run vlc in the terminal vlc -v and it gives me lots of errors.  
 ```
main demux warning: no access_demux module matching "file" could be loaded
[0x88dd920] main audio output warning: the mixer got a packet in the past (247401)
[0x88dd920] main audio output warning: the mixer got a packet in the past (221276)
[0x88dd920] main audio output warning: the mixer got a packet in the past (195151)
[0x88dd920] main audio output warning: the mixer got a packet in the past (169026)
[0x88dd920] main audio output warning: the mixer got a packet in the past (142901)
[0x88dd920] main audio output warning: the mixer got a packet in the past (116797)
[0x88dd920] main audio output warning: the mixer got a packet in the past (90672)
[0x88dd920] main audio output warning: the mixer got a packet in the past (64547)
[0x88dd920] main audio output warning: the mixer got a packet in the past (38422)
[0x88dd920] main audio output warning: the mixer got a packet in the past (12297)
[0x88dd920] main audio output warning: mixer start isn't output start (4722)
[0x88dd920] main audio output warning: PTS is out of range (-34779), dropping buffer
[0x88dd920] main audio output warning: the mixer got a packet in the past (44067)
[0x88dd920] main audio output warning: the mixer got a packet in the past (17942)
[0x88dd920] main audio output warning: mixer start isn't output start (6889)
[0x87f5bb8] main video output warning: early picture skipped
[0x87f5bb8] main video output warning: early picture skipped
[0x87f5bb8] main video output warning: early picture skipped
[0x87f5bb8] main video output warning: early picture skipped
[0x87f5bb8] main video output warning: early picture skipped
[0x88dd920] main audio output warning: PTS is out of range (-19375), dropping buffer
[0x88dd920] main audio output warning: PTS is out of range (-34842), dropping buffer
[0x88dd920] main audio output warning: the mixer got a packet in the past (110517)
[0x88dd920] main audio output warning: the mixer got a packet in the past (84392)
[0x88dd920] main audio output warning: the mixer got a packet in the past (58267)
[0x88dd920] main audio output warning: the mixer got a packet in the past (32142)
[0x88dd920] main audio output warning: the mixer got a packet in the past (6038)
[0x88dd920] main audio output warning: mixer start isn't output start (2318)
[0x8909dd8] scaletempo audio filter warning: bad input or output format
[0x8909dd8] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x88faed8] scaletempo audio filter warning: bad input or output format
[0x88faed8] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x88dd920] main audio output warning: output date isn't PTS date, requesting resampling (52735)
[0x88dd920] main audio output warning: buffer is 51104 late, triggering upsampling
[0x88dd920] main audio output warning: output date isn't PTS date, requesting resampling (48063)
[0x88dd920] main audio output warning: timing screwed, stopping resampling
[0x88dd920] main audio output warning: buffer is 102534 late, triggering upsampling
[0x88dd920] main audio output warning: output date isn't PTS date, requesting resampling (54309)
[0x88dd920] main audio output warning: audio drift is too big (145702), dropping buffer
[0x88dd920] main audio output warning: audio drift is too big (132785), dropping buffer
[0x88dd920] main audio output warning: resampling stopped after 12772053 usec (drift: -33295)
[0x87f5bb8] main video output warning: late picture skipped (42387 > -27)
[0x87f5bb8] main video output warning: late picture skipped (678 > -27)

```

Not that I understand this.

---

