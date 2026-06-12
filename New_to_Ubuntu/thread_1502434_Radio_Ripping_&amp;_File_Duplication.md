---
title: "Radio Ripping &amp; File Duplication"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2010-06-05
I've been ripping streaming radio using streamtuner+streamripper... 

But when the same track is played again, its again downloading/ripping it...

Is there any way to prevent this file duplication???

or, is there any other feature-full radio ripping app???

---

### Post by randolf_ambrose on 2010-06-05
check this out!!!

---

### Post by ajgreeny on 2010-06-05
If they are mp3 streams, which is what streamripper seems to work best with, you could also use mplayer with the command
```
mplayer <URL> -dumpstream -dumpfile stream.mp3
```
which will save an mp3 stream as a file called *stream.mp3*

If it's not an mp3 stream, but some other format try
```
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav
```
which saves "real" or other stream as file outfile.wav which youcan then convert to mp3 if you wish with ffmpeg or if you prefer, other GUI apps.

---

### Post by randolf_ambrose on 2010-06-06
> **ajgreeny said:**
> If they are mp3 streams, which is what streamripper seems to work best with, you could also use mplayer with the command
```
mplayer <URL> -dumpstream -dumpfile stream.mp3
```
which will save an mp3 stream as a file called *stream.mp3*

If it's not an mp3 stream, but some other format try
```
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav
```
which saves "real" or other stream as file outfile.wav which youcan then convert to mp3 if you wish with ffmpeg or if you prefer, other GUI apps.

but thats more work involved...

as of now, i'm able to rip mp3 stream... 

my problem is, when the same track is played again, streamripper doesnt recognise that the file is already downloaded and thus downloads the same file when played again...

i would like to know if there is any code to put a hold to file duplication/downloading same file when its repeated  in the radio...

---

### Post by ajgreeny on 2010-06-06
Sorry, no idea about that problem.  I suspect it depends on the type of stream.  I only record streams direct from radio station broadcasts, which as far as I'm aware do not stream as separate tracks, but as a long continuous stream.  It is good for concerts etc etc, but not for tracks as you appear to want.

---

### Post by Cresho on 2010-06-06
exaile plus streamripper

---

### Post by randolf_ambrose on 2010-06-08
> **Cresho said:**
> exaile plus streamripper

lemme see if this works...

---

