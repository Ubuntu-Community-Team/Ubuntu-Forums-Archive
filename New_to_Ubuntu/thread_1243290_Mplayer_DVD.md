---
title: "Mplayer DVD"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by hellomoto on 2009-08-18
Hi guys,

I am in the process of backing up my DVDs, but some of my DVDs don't seam to dump properly with mplayer even though they play with mplayer.

When trying to dump certain titles (but not all) I get the following:

```

$ mplayer dvd://1 -dumpstream -dumpfile stranger_than_fiction.vob
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 30 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: hi
subtitle ( sid ): 2 language: en
number of subtitles on disk: 3


```

mplayer tries to dump the vob but it just seams to hand and the .vob file never really gets any bigger than 30mbs even after a few hours!

---

