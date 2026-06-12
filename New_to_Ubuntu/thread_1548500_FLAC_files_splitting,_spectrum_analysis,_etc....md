---
title: "FLAC files: splitting, spectrum analysis, etc..."
date: 2010-08-08
forum: New to Ubuntu
---

### Post by darkmaxa on 2010-08-08
Question for people familiar with Ubuntu & FLACs.

Which tools you recommend for splitting large FLAC files (based on cue), spectrum analysis (to determine is real lossless or just transcoded from some lossy format). 

Also, which is the best tag editor for FLAC files for Ubuntu?

---

### Post by rotwang888 on 2010-08-08
> **darkmaxa said:**
> Question for people familiar with Ubuntu & FLACs.

Which tools you recommend for splitting large FLAC files (based on cue), spectrum analysis (to determine is real lossless or just transcoded from some lossy format). 

Also, which is the best tag editor for FLAC files for Ubuntu?

I use this command to split single Flac files
```
cuebreakpoints CDImage.cue | shnsplit -o flac CDImage.flac
```
You'll need to install shntool and cuetools first if you don't have them already.
 For spectrum analysis...haven't done this in ages.  I think Ardour will do the job but it might be overkill.
 I edit flac tags with Easytag.

---

### Post by rotwang888 on 2010-08-08
Check out Sonic Visualiser [http://www.sonicvisualiser.org/](http://www.sonicvisualiser.org/)

You may also want to have a look at [http://www.linux-sound.org/one-page.html](http://www.linux-sound.org/one-page.html)

---

