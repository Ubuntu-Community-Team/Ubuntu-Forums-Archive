---
title: "Open Office fonts have red and green sort of halo."
date: 2008-12-05
forum: New to Ubuntu
---

### Post by philinux on 2008-12-05
Not seen this in any other app.

---

### Post by s.fox on 2008-12-05
Not sure what you mean.  Could it be grammer and spelling mistakes for the words above?  

Could you please post a screen shot?

---

### Post by philinux on 2008-12-05
No it's the actual fonts themselves. No other app apart from OOo shows this effect. Screenshot attached.

---

### Post by OldGrey on 2008-12-05
I don't have an answer, but I have noticed that as well with OOo.

---

### Post by philinux on 2008-12-05
I thought it was the monitor at first but defo not.

Glad it's not just me then. Maybe needs a bug report.

---

### Post by Potters Son on 2008-12-05
Maybe it's your font rendering settings? If you go to System>Prefs>Appearance>Fonts (Ubuntu), you see four options about how fonts can be rendered on the screen:

1. Monochrome - no antialiasing
2. Best contrast - seems to do minor antialiasing
3. Best shapes - I think this one tries to be the most accurate for the truetype fonts.
4. finally, Subpixel smoothing (LCDs) - assumes an LCD monitor. With an LCD, the red/green/blue components of each pixel always occur in a certain order. This option says, "Hey, instead of just drawing a black dot on a white background in one pixel, why don't I draw two-thirds of the dot in one pixel and the remaining third in the one beside it?" On the wrong monitor, this black dot might look like a red dot next to a cyan one.

The only problem with this theory is that I'm using an LCD monitor, and your screenshot looks bad here too.

Another option is to look at OpenOffice.org's settings. If you go to Tools>Options>OpenOffice.org>View, you can change "screen font antialiasing." I don't remember how it was on default, but I have it set to 4 pixels, and it looks great.

Hope it helps!

---

### Post by philinux on 2008-12-05
I've played with prefs>fonts all combinations. No change.

However if I turn off anti-aliasing on OOo the colours go. But the fonts dont display as well. And it affects some of OO gui, makes some a bit spidery.

---

### Post by philinux on 2008-12-05
Reported as bug
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/305483](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/305483)

Please feel free to add any comments.

---

