---
title: "How To Enable Touchpad Scrolling?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Haziqonfire on 2010-10-11
I just downloaded Ubuntu 10.10 and I wanted to know how to enable the touchpad scrolling (Vertical).

I'm still new to Ubuntu and figuring it out. I went to "mouse" under System > Preferences > Mouse -- but I didn't see anything there.

Edit: I'm also using a Dell Latitude E6410.

---

### Post by bonfire89 on 2010-10-11
I have the same computer, and have the same problem I would like to know about this too.

---

### Post by sgosnell on 2010-10-11
I don't have a Dell (fortunately) but on my system, System/Preferences/Mouse brings up a dialog with 3 tabs, the rightmost being "Touchpad".  Clicking on that tab gives me the touchpad options, one of which is scrolling.  If that doesn't come up on your Dell, you have a problem, and I don't know how to enable it.  What touchpad does Dell use?  Synaptic?  Elantech?  Something else?  Do they provide a touchpad driver on the Dell website?

---

### Post by bonfire89 on 2010-10-13
nah, I don't even get those three tabs. It appears the real problem is that the touchpad is detetected as a generic mouse.

When I run cat /proc/bus/input/devices I get no sign of a touchpad.

And given the results on this search [http://www.google.ca/search?sourceid=chrome&ie=UTF-8&q=ubuntu+touchpad+shows+up+as+generic+mouse](http://www.google.ca/search?sourceid=chrome&ie=UTF-8&q=ubuntu+touchpad+shows+up+as+generic+mouse) looks like it is a known bug.

So, time to sit and wait or learn some new skills it looks.

---

### Post by Irahna on 2010-10-13
Open up Ubuntu Software Center and search "Touchpad"(creative I know). This shoud allow you to set the controls. If now you might want to search your model into Synaptic. Or just start with dell. This worked with my Asus eee pc 1005hab

---

### Post by UbuNoob001 on 2010-10-24
Same issue here, inspiron.

---

