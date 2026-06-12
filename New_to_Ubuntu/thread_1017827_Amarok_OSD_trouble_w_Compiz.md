---
title: "Amarok OSD trouble w/ Compiz"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by anomnomnomaly on 2008-12-21
I've been really enjoying Amarok's OSD feature, where every time the song changes a customizable display pops up showing what song I'm listening to, artist, album, etc., and then fades away after a few seconds. Before I started using Compiz, this display would be always on top, which is how it needs to be because if I can't see it over any other windows I have open, then what's the point of having it in the first place, right?

Since I started using Compiz, OSD is no longer always on top, but rather it seems to pop up *underneath* any windows I have open! If I have anything full screen, of course, I can't see it at all. Any idea how I can get the OSD to be always on top? I suspect this has something to do with the Focus Prevention Level setting in Compiz. Right now I have it set to Low. I tried the lowest setting, Off (I want OSD to steal the focus when it comes up), but OSD still pops up under everything else. I think I may be able to fix this problem by adding a Focus Prevention Window rule; I haven't messed with this at all as I don't know how, so right now the Focus Prevention Window setting is "any." To clarify, I don't want Amarok to be always-on-top, just Amarok's OSD.

---

### Post by anomnomnomaly on 2009-01-18
It looks like I can get OSD to be always-on-top using Window Rules:
[http://wiki.compiz-fusion.org/WindowMatching#head-b1469a83eae85a4daf639a6b9d48b58b999a214e](http://wiki.compiz-fusion.org/WindowMatching#head-b1469a83eae85a4daf639a6b9d48b58b999a214e)

The question is, how do I identify Amarok's OSD so I can apply rules (i.e. Above, Sticky) to it?

found this regarding how to identify a window in Compiz,
[http://wiki.compiz-fusion.org/WindowMatching#identify](http://wiki.compiz-fusion.org/WindowMatching#identify)

but I don't really know enough about Amarok's OSD to be able to apply any of these options... there is no title bar, and I don't know the class name, XID, etc. of the OSD. Any ideas?

---

### Post by Keilaron on 2009-01-20
According to the [Amarok OSD transparency]("http://ubuntuforums.org/showthread.php?t=903606") thread, what you want is this:
```
(name=amarokapp & role=osd & type=normal)
```
Worked for me (with Window Rules) after a restart of Amarok.

(Sorry, I don't know how to figure the above out -- I tried to use wmctrl, but it didn't seem to list the OSD window.)

---

### Post by anomnomnomaly on 2009-01-20
Woohoo! That fixed it. I just went into the Window Rules plugin in CCSM and added (name=amarokapp & role=osd & type=normal) for Above.

---

