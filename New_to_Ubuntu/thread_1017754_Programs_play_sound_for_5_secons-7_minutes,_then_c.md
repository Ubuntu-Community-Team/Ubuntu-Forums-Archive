---
title: "Programs play sound for 5 secons-7 minutes, then crash"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by abben on 2008-12-21
EDIT: I should say "Then lockup". They don't crash, they cause my whole computer to freeze entirely.

So, my xubuntu system recognizes my sound card, but whether it be a movie, a youtube video, or an mp3, my computer inevitably freezes up when I play sound.

Has anyone heard of this happening? Any relevant packages to reinstall?

---

### Post by 2hot6ft2 on 2008-12-21
> **abben said:**
> So, my xubuntu system recognizes my sound card, but whether it be a movie, a youtube video, or an mp3, my computer inevitably freezes up when I play sound.

Has anyone heard of this happening? Any relevant packages to reinstall?
Sounds like it may be a codec problem.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Also
Believe it or not the freezes seem to tie into the sound Pulse Audio (when not configured properly) can send the cpu to 100% causing the freeze. This has been reported by several people and the solution is here for that.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I was having freezes too and since completing the how to have not had a freeze at all.

This may or may not be your particular issue but it's where I would start after reading everything I have.

Other sound options
Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse as linked above
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be). 
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

There are more but this gives you some alternatives that are being used.

---

