---
title: "Wacom Intous 4 Left Handed"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by buddyd16 on 2010-01-14
How do I set up my wacom intous 4 tablet so that the input is in left handed mode rather than the standard right handed mode? (so that I can rotate the tablet so that he buttons are on the right instead of the left)

Also how do I set up the eraser side of the pen to act different from the pen side? (gimp does not recognize that the two ends are different input types)

thank you

---

### Post by Favux on 2010-01-14
Hi buddyd16,

Just add to the usb section of the 10-linuxwacom.fdi:
```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>

```
below the stylus line and above the info.callout line.

In Gimp did you configure the extended input devices?  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by buddyd16 on 2010-01-14
thank you very much for the help I'll give that a try and read through the wiki.

---

