---
title: "Memory Leak Problem"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by fridgey on 2010-05-17
Alright, I've been using ubuntu/linux in general for about a month now, so I know some basics but I'm far from being able to troubleshoot advanced problems.  A few days ago I updated to 10.04, everything seemed to go fine.  Unfortunately it soon seemed to be running a bit slower, particularly when watching video.  After about 2 days of uptime, I went into system monitor to see if something was eating resources, suspecting wine being the problem, and was shocked to see my 1 gig of RAM basically full and 2.1 out of 2.7 gigs of swap used up.  Unfortunately the memory didn't appear to be tied to any particular process so I had no idea how to find out where it went.  Confused, I went with the old restart and hope it magically goes away strategy, but it hasn't.  I did some testing and found that memory was eaten basically every time I switched windows around... even something so simple as restarting fresh, opening a few random things (doesn't seem to matter what's open), and then minimizing/maximizing the system monitor would eat a few megs every time.  Googling made me aware of [https://wiki.ubuntu.com/X/Testing/GEMLeak ]("https://wiki.ubuntu.com/X/Testing/GEMLeak")which seems to fit my issue.  "grep "object bytes" /sys/kernel/debug/dri/0/gem objects" gives me a number around 500MB right now, after around 5 hours of use, which I gather is an issue.  However, "glxinfo | grep "GLX version"" says I'm using 1.2, which would lead me to think this _isn't_ the issue.  Anyway, I'm lost, so any help in figuring out/fixing this would be greatly appreciated.  Off to restart again...

---

### Post by BoneKracker on 2010-05-17
You're probably aware that RAM that's being used for cache or buffers isn't really a problem (in fact, it's a good thing).

**That said**, this volume of swapping does indicate something's wrong.  It does sound memory-leakish.  Your system would not prefer swapping to caching to that degree.

Ideally, you'd see RAM as fully utilized as possible (but most of that for cache/buffers), but you'd only see a bit of swap being used.

Just as an additional data point, could you post the output of 'free -m' a few minutes after boot and then again when it's in this state?  Also what's the output of 'cat /proc/sys/vm/swappiness'?

Also, you may want to take the command-line utility 'top' for a spin.  It's like what you've been looking at in the GUI, but much more configurable.  You may find it useful in identifying what's hogging memory.

---

### Post by fridgey on 2010-05-17
Yes, I can tell there's a problem, as functionality and responsiveness gets _very_ significantly worse as time goes by.  Also, right after a restart I can watch video in vlc fine, full screen or otherwise, but after even a fairly short period of time video playback gets sluggish to the point of being unwatchable.  Neither of these problems existed prior to the update.  Anyway, right after a fresh restart "free -m" gives me
```
             total       used       free     shared    buffers     cached
Mem:           938        358        580          0         56        138
-/+ buffers/cache:        163        775
Swap:         2753          0       2753

```and swappiness is set to 60 (haven't touched this).  I'll get the data for when things get bad and give top a looking at.  Thanks a lot for trying to help :)

---

### Post by BoneKracker on 2010-05-17
That looks right (including swappiness).

In case I'm not "here" when you post the 'free' output from the problem state, I just wanted to rule out some kind of caching-related problem before you pursue the memory leak angle.

It does sound to me like a memory leak, though, and running that down is really beyond me.  About all I can suggest is examining top to see if you can figure out with more granularity what's going on over time.

Beyond that, the kind of primitive trouble-shooting I'd probably try, given my limited expertise, would probably amount to "fault isolation".  If the problem occurs without you actually using applications, I'd probably try booting in a non-graphical runlevel and letting it run long enough for the problem to emerge, to rule out X and all the graphical applications.  If it still occurred, then you'd know its something fairly core to the system.  That sort of thing.

**Hopefully somebody's who's more knowledgeable about isolating memory leaks will provide some advice.** :)

---

### Post by fridgey on 2010-05-18
So, after a day of uptime (during which I've had very little time to actually _do_ anything on the system) there's more than 1 GB tied up in GEM objects.  Between this, and the fact that I've noticed I have the same video card (radeon igp 345m) as one of the testers who reported the update didn't solve the problem at [https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak) I feel I can safely say I've pegged down where the issue lies... but I'm still no closer to knowing what to do about it.  Anyone have any advice?  Something I can regress?  I really don't want to have to do a full reinstall, going back to 9.10 :/  This is, to say the least, very frustrating :mad:

---

### Post by BoneKracker on 2010-05-18
Yeah, looking at that link, I'd have to agree.

That pretty much blows.

I imagine you could just downgrade your Xorg, rather than reverting to an earlier system release.  Though I do recall my my ubuntu experience years ago that it is somewhat tightly integrated, so that could cause problems.

If you can't switch drivers, or switch GPUs, I suppose your only options are to do one of those two things (or switch distros).

---

### Post by fridgey on 2010-05-18
Wow, I feel dumb.  Turned off compiz and on first blush it appears the problem is suppressed *fingers crossed*.  Obviously not a "solution" as such, but I can live without the pretty until I have time to figure that out... can't believe that wasn't the first thing I tried.  Totally fooled by there being a major-ticket problem with a similar effect, lol.

---

### Post by BoneKracker on 2010-05-18
You probably also just freed up a bunch of memory, cpu time, and bus bandwidth for something actually useful.  Like running a memory-leaking web browser. :P

---

