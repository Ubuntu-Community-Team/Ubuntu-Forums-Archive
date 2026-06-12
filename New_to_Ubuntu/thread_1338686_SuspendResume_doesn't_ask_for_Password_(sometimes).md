---
title: "Suspend/Resume doesn't ask for Password (sometimes)"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-11-26
Before anything, Google searches revealed no information.

This started happening about 3 weeks ago. Sometimes when I resume from Suspend, Ubuntu goes right to the desktop without asking for a P/W. Being a Systems Administrator, I like to practice secure computing. As you can see, this presents a huge problem for me.

Here's my Apps/Gnome-Power-Management/Lock settings in GConf Editor:
[IMG]http://img6.imageshack.us/img6/3043/screenshot1mr.png[/IMG]


Has this happened to anyone before?
Were you able to fix it?
Should I file a bug report?

_Specs_
CPU:2.4 GHz Pentium 4
MB: Intel D845PESV
RAM: 1GB RAM
HD: 80GB WD 8MB cache PATA
Video: nVidia GeForce 7600 GS AGP
Sound: SoundBlaster Live! PCI
OS: Dual Boot; Win XP SP3 & Ubuntu 9.04

---

### Post by Cuco3 on 2009-11-28
** Has this happened to anyone before, please? **At least let me know if this is an isolated issue. Thank you.

---

### Post by Cuco3 on 2009-11-28
> **Cuco3 said:**
> ** Has this happened to anyone before or maybe you've heard of this problem, please? **At least let me know if this is an isolated issue. Thank you.please?

---

### Post by Arla on 2009-11-28
Yes I get this, when mentioned on Karmic board during Alpha I was, in essence told to "piss off", was a LITTLE more polite about it (but not much).

---

### Post by Cuco3 on 2009-11-28
> **Arla said:**
> Yes I get this, when mentioned on Karmic board during Alpha I was, in essence told to "piss off", was a LITTLE more polite about it (but not much).Thank you for your response. I wonder if there's a bug report already out. I'll search for one, but if not, I'll begin working on one and post the link here for others to view.

---

### Post by Arla on 2009-11-28
My amended response, there is some reason why apparently this is "expected" behaviour, I never really got, what I considered, a "good" answer as to why this would be expected, I believe it's something to do with time spent in suspend mode, but I'm not sure, but I was told it was expected behaviour in very short order, and since I'm fairly new to Ubuntu I didn't really have a leg to stand on saying it wasn't.

---

### Post by Cuco3 on 2009-11-29
> **Arla said:**
> My amended response, there is some reason why apparently this is "expected" behaviour, I never really got, what I considered, a "good" answer as to why this would be expected, I believe it's something to do with time spent in suspend mode, but I'm not sure, but I was told it was expected behaviour in very short order, and since I'm fairly new to Ubuntu I didn't really have a leg to stand on saying it wasn't.Well, I've found your threads/posts on this topic, and I must say that mod could have at least pointed you in the right direction, like suggesting a Google Search with the right terms to get an answer.

As for "expected behaviour," I find that hard to believe. Not asking for a PW after resuming from suspend/hibernate is a huuuuuuge security flaw no matter how they want to spin it.

Here are the links for anyone else interested:
[http://ubuntuforums.org/showthread.php?t=1261141](http://ubuntuforums.org/showthread.php?t=1261141)
[http://ubuntuforums.org/showthread.php?t=1261178](http://ubuntuforums.org/showthread.php?t=1261178)
[http://ubuntuforums.org/showthread.php?t=1256433](http://ubuntuforums.org/showthread.php?t=1256433)

---

### Post by Cuco3 on 2009-12-20
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+bug/498694](https://bugs.launchpad.net/ubuntu/+bug/498694)

---

### Post by Cuco3 on 2010-03-26
Works beautifully in Karmic 9.10

Don't know what the changes were from 9.04 to 9.10 but the solution is in there.

I won't mark it as solved due to the issue being with 9.04, but if anyone has the problem, jump on 9.10 for the fix.

---

