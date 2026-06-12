---
title: "xorg.conf equivalent in 8.10?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Bogdanovist on 2009-03-13
Hi All,

I'm trying to get my external mouse to operate as for a left handed user (button functions switched left to right) but maintain a RH configuration for the touchpad of my laptop (don't ask me why, I just prefer it this way and it's driving me crazy not having it like this!!).

Anyway, I posted in this [thread]("http://ubuntuforums.org/showthread.php?t=1091641") my problem, but got no response. Since then I have discovered [this]("http://ubuntuforums.org/showthread.php?t=252240&highlight=left+handed+mouse+touchpad") thread (and a few others) that give solutions to this problem that involve changing the xorg.conf file. I've tried these to no avail and I suspect that the issue is the treatment of the xorg.conf in the later versions (these solutions are a little old). I've heard that xorg.conf had been somewhat depricated and indeed, there is no mention of a mouse in my xorg.conf file. Trying to add an entry for a mouse with the appropriate button config options just causes an error on startup 'failed to parse the xorg.conf file correctly". Maybe there is just a minor syntax issue, or maybe it is a deeper problem?

So does anyone know what the equivalent method of customising settings is for newer versions of Ubunut/Gnome? I hope there is still a way of solving this problem. Any advice will be appreciated!

---

### Post by humphreybc on 2009-03-13
I too have had trouble getting any of my changes in xorg.conf to actually do anything. I was trying to follow a tutorial to get dualmode working on my touchpad, but when I went into xorg.conf I saw there was hardly anything there.

I'm not so sure how it works now though sorry. Make sure you backup your original xorg.conf otherwise your GUI will crash and then you'll be in the shitter.

---

### Post by Bogdanovist on 2009-03-13
Yeah, it looks like old advice on xorg.conf additions is now out of date. The question is where has the functionality gone? Hopefully there is somewhere else that setting can be easily changed, or else this would represent a reduction in customisability :confused:

---

