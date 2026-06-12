---
title: "CPU Overload in 10.04 LTS?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by panthe0n on 2010-05-10
Hey guys, just installed 10.04 LTS on my laptop. I had shifted all my files over to an XP machine so I could put them back on once Ubuntu had installed. So I started shifting my music folders over and I noticed that the surface of my laptop was really really warm. So I checked on the System Monitor and my CPU was floating around the 95-100% mark. Would any of you know why? I freaked out so I cancelled shifting my files over and turned off my laptop. Just started it again and the CPU values are fine again, but would any of you know what would've caused it? Surely it couldn't have been me just shifting files, could it?

---

### Post by Paqman on 2010-05-10
> **panthe0n said:**
> Surely it couldn't have been me just shifting files, could it?

Nope.

If it happens again, have a look in System Monitor and see if you can spot what process is chewing up all the CPU. Something must have gone berserk.

---

### Post by 3rdalbum on 2010-05-10
Don't be scared when you see your CPU working at 100%. It's perfectly safe to run at 100% - that's its guaranteed maximum, it can work forever at 100% without ill effects.

What I'm going to suggest is that your XP hard disk that you were copying files to is formatted as NTFS. In order to write to NTFS drives, it does take a fair amount of CPU power. Don't worry about it.

If you're not copying to NTFS and not running anything that you know will tax the CPU, then check out the System Monitor or the Top command to see what program is using so much CPU time.

---

### Post by Paqman on 2010-05-10
> **3rdalbum said:**
> 
What I'm going to suggest is that your XP hard disk that you were copying files to is formatted as NTFS. In order to write to NTFS drives, it does take a fair amount of CPU power. Don't worry about it.


^ This makes sense.

---

