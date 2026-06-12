---
title: "merging mpg video clibs using PiTiVi"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by furoido on 2009-06-08
Hi guys,
Just tried to merge 3 mpg video clips on Pitivi video editor, but something gone wrong. Basically, the new video freezes at the end of what was the first clip, although the sound seems to carry on for the other 2 clips....
Anyone got any ideas of how to fix or properly merge my clips.
Also, I originally tried using Mplayer video player, but when I launch it, all I get is the Mplayer logo and nothing else?!!!

---

### Post by MrWES on 2009-06-08
> **furoido said:**
> Hi guys,
Just tried to merge 3 mpg video clips on Pitivi video editor, but something gone wrong. Basically, the new video freezes at the end of what was the first clip, although the sound seems to carry on for the other 2 clips....
Anyone got any ideas of how to fix or properly merge my clips.
Also, I originally tried using Mplayer video player, but when I launch it, all I get is the Mplayer logo and nothing else?!!!

Have you tried this:
```
cat *.mpg > big.mpg
```

---

### Post by reeseslover531 on 2009-06-08
I use this for AVIs when I merge them, I find that it realigns things and is in general a good thing.
[code]mencoder -forceidx -oac copy -ovc copy movie_new.avi -o movie.avi[\code] 
It works well for avis and I think it should work fine for mpgs as well.

Good Luck!

---

### Post by MrWES on 2009-06-08
> **reeseslover531 said:**
> I use this for AVIs when I merge them, I find that it realigns things and is in general a good thing.
[code]mencoder -forceidx -oac copy -ovc copy movie_new.avi -o movie.avi[\code] 
It works well for avis and I think it should work fine for mpgs as well.

Good Luck!

To merge and/or split avi's, use transcodes avisplit and avimerge. 

Bill

---

### Post by reeseslover531 on 2009-06-09
> **MrWES said:**
> To merge and/or split avi's, use transcodes avisplit and avimerge. 

Bill

wow I haven't seen that before, excellent!

---

### Post by johnuk on 2010-08-15
I tried avimerge after seeing someone mention it on here, probably MrWes.

It worked fine for a couple of clips. 

Then I tried over 26 and the audio seemed to double in speed, the syncing failed and it was all skippy. 

I haven't tried re-merging with it, to see if it was just a one off, but am giving PiTiVi a go first. 

Thought I'd mention this in case anyone else notices it.

---

