---
title: "Mplayer tells me my computer is too slow when playing videos"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Sugi on 2009-01-17
I keep this message when I try to play larger movie files, but the thing is.  My computer isn't in full use.  My cpu is at about 55% and Memory about 30%.  This wouldn't be a problem, but my audio is off by a second.  And I know the audio works correctly, because I have tried it on other computers.  Any idea on how to fix this?

```
           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.
```


Sugi

---

### Post by Cypher on 2009-01-17
What kind of computer do you have?
```

cat /proc/cpuinfo

```
will give us some info about your systems capabilities..

---

### Post by Sugi on 2009-01-17
Here's some basic designs:
Intel(R) Core(TM)2 CPU 2.00 Ghz
cpu MHz 996.000
Cache Size 4096 KB

Let me know if you need more information.  Thanks

Sugi

---

### Post by Cypher on 2009-01-17
Hmm, the CPU MHZ doesn't seem to be right..I've got
```

model name	: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping	: 6
cpu MHz		: 1600.000
cache size	: 2048 KB

```
So your 2.00 GHz CPU should come out to about 1400 MHz, and not 996..

---

### Post by Sugi on 2009-01-17
I have a laptop, that's probably why.

Sugi

---

### Post by oldos2er on 2009-01-17
Have you tried the suggestions it's giving you?

---

### Post by fenian on 2009-01-17
Try changing the video out settings in Mplayer.Open Mplayer right click in the window and go to Prefrences,click the Video tab and choose xv.

---

### Post by Sugi on 2009-01-17
```
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
```

I have tried them, but these are the only ones that should mater.  The only problem is, the autosync doesn't work.  Do I just add -autosync or do I have to input a vaule?
Example: mplayer -autosync 30 /path/to/buggy/video.wma

Sugi

---

### Post by Sugi on 2009-01-18
But remember, this is not a sync issue.  This is something wrong with my computer or it playing slow.

BUMP

Sugi

---

