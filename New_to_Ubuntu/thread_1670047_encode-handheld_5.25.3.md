---
title: "encode-handheld 5.2/5.3"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by ep6 on 2011-01-18
hi all , im new to ubuntu and i´ve been trying to use holyroses encode handheld 5.2/5.3 and i cant make head of tails of so if anyone can explain me everything from step 1  i would really appreciate it.
Link of thread   [http://newyork.ubuntuforums.org/showthread.php?t=874957](http://newyork.ubuntuforums.org/showthread.php?t=874957)
links of encode-handheld 5.2 and 5.3 should be in there please help me :|

---

### Post by gordintoronto on 2011-01-18
You want an explanation of all 680 steps? Encode Handheld is packaged for programmers, not normal people.

This will appear later this month in Full Circle Magazine:

Q  I am trying to get an option in WinFF to convert an MPEG file to an iPod compatible video.

A  (Thanks to fakeoutdoorsman in the Ubuntu Forums) Forget WinFF. The H.264 iPod presets are terribly out-of-date. Try using FFmpeg directly from the command line:
ffmpeg -i input.mp4 -vcodec mpeg4 -map_meta_data 0:0 -s 480x320 -acodec libfaac output.m4v
(Note that you must first cd to the folder where the input file resides.)

---

