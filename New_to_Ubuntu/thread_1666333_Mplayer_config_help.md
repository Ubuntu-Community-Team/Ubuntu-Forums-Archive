---
title: "Mplayer config help"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by gngf123 on 2011-01-13
I seem to have a problem with subtitles, I have configured them to do most of the stuff I want them to do in ~/.mplayer/config, but have one last remaining issue.

Subtitles display themselves at the correct time just fine, but then stay on screen until another subtitle is displayed. This can be annoying when there are long periods of no talking.

Anyone know the command I need? A simple subtitle time-out command would be ideal.

---

### Post by Smart Viking on 2011-01-13
It would be useful to see your ¨~/.mplayer/config.

---

### Post by Vaphell on 2011-01-13
what type of subtitles? usually subtitles (at least the formats i know/use) alone define both start and end time/frame and there is no need for any timeout.

---

### Post by gngf123 on 2011-01-13
> **Vaphell said:**
> what type of subtitles? usually subtitles (at least the formats i know/use) alone define both start and end time/frame and there is no need for any timeout.

Not sure how to answer this one. So far all of the subtitles I have tried are softsubs contained inside the video file in question.

> **Smart Viking said:**
> It would be useful to see your ¨~/.mplayer/config.

Still playing about, this is all I have at the moment:

```
really-quiet="1"

ffactor="1" #black outline
subfont-text-scale=2
subpos="95" 
subfont-blur="1"

stop-xscreensaver="yes"
```

---

