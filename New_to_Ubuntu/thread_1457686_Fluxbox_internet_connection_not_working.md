---
title: "Fluxbox internet connection not working"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by lolzwut on 2010-04-18
I can't connect to the internet on fluxbox wm. Can someone help?

---

### Post by -humanaut- on 2010-04-18
Try installing Wicd and replacing Gnome Network manager.

---

### Post by lolzwut on 2010-04-18
Never mind. I figured it out. In case anyone wants to know I just put "nm-applet &" (without quotes) in ~/.fluxbox/startup. I put it right before the exec fluxbox line.

---

