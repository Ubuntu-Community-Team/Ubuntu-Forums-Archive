---
title: "Problem with 1440x900 resolution on Thinkpad laptop"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by zackdarnell on 2008-12-19
I just installed Ubuntu 8.10 64-bit on a Lenovo Thinkpad T400. When I set the screen resolution to 1440x900 (by unchecking "mirror screens" then selecting 1440x900), things don't look right. The top panel doesn't extend all the way to the right edge of the screen. The bottom panel is appx. 1" off the bottom of the screen and also doesn't extend all the way to the right edge. I can drag the bottom panel down to the bottom of the screen, though, and it will expand to fit the full width. I can't make the top expand to fit the full width, though. Also, when I maximize a window, it doesn't fill the whole screen- just the portion originally bounded by the 2 panels (i.e. it doesn't go all the way to the bottom or all the way to the right).

I previously had 8.04 installed, and never had this problem. 

Does anyone have any suggestions?

Thanks.

---

### Post by scorchgeek on 2008-12-19
Try killing the X server (by pushing Ctrl-Alt-Backspace) and try again.

---

### Post by zackdarnell on 2008-12-19
> **scorchgeek said:**
> Try killing the X server (by pushing Ctrl-Alt-Backspace) and try again.

Thanks, scorchgeek. I tried that, but it looks the same after. Panels still don't extend all the way over.

---

### Post by zackdarnell on 2008-12-19
A screenshot is attached.

---

### Post by Gone fishing on 2008-12-19
What happens if you just reset the properties of the panels by right clicking and changing the properties?

---

### Post by zackdarnell on 2008-12-19
> **Gone fishing said:**
> What happens if you just reset the properties of the panels by right clicking and changing the properties?

Any suggestions for what to change? I've tried "Expand" both selected and unselected, same for "Autohide". Still no change.

---

### Post by zackdarnell on 2008-12-19
I fixed it. Apparently I had a second display enabled. Who knew.

---

