---
title: "Ati with Compiz effects cause flimmering video"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-01-20
I have a ATi HD 4670 card and if I try to look at a movie in totem will it start flimmering, when I turn Compiz off does the video act as normal. The flimmering is that I get a blackscreen in the video player for less then a sec. Any clues why?

Uploading xconf and glxinfo

---

### Post by stderr on 2009-01-20
I think this is the common problem many have encountered. Could you try going to System -> Preferences -> Multimedia Systems Selector, clicking the Video tab and switching the Video Output to X Window System X11 and see if that rectifies it under compiz? (Not really an ideal solution to leave in place though, more just to test).

If you've got VLC installed and witness the same effects with that, similarly, if you could try (in VLC) going to Tools -> Preferences -> Video (left hand side) and change Output from Default to X11 and restart VLC. Again, this isn't an ideal solution, and you may want to switch back afterwards.

Ultimately these are just workarounds. I rarely manage to get these Compiz glitches figured out. Typically I find the next release fixes it, the next breaks it again... ;)

---

