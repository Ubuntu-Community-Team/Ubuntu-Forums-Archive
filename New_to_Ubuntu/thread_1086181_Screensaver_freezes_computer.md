---
title: "Screensaver freezes computer?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Hakizi on 2009-03-03
I have a problem where every time my screen saver comes on, my computer freezes up and I'm forced to hard reboot. I tried going to the screen saver settings, but even just that freezes up the computer. After searching the internet, I've found this is not an isolated incident, but I've found no way to solve it. Just that it happens.
Any help would be greatly appreciated

---

### Post by stoogiebuncho on 2009-03-03
This doesn't really solve your problem, but if you want to disable your screensaver from the terminal, just enter this:

```
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 0
```

---

### Post by Hakizi on 2009-03-04
Thanks!
At least I don't have to worry about it freezing now

---

### Post by mbpeyk on 2009-03-04
I had the same thing happen to me but i changed the screen saver to the one called cosmos and it works fine for me. I don't know what the problem is but it only happened on certain screen savers. Mostly the ones that had a lot happening, like the antinspect and matrix view.

---

### Post by WhiskyChris on 2009-03-04
I had the same problem as well, I read somewhere that it was a problem with the OpenGL screensavers (which relates to the fact that I don't believe my OpenGL is working properly with some programs that need it...)

Switching to the blank screen seems to have worked so far.

---

### Post by Hakizi on 2009-03-05
It would be fine for me to change the screen saver, but I can't.
The screen saver settings freezes the computer when it opens. :/

---

### Post by SamNSane on 2009-03-05
> **Hakizi said:**
> It would be fine for me to change the screen saver, but I can't.
The screen saver settings freezes the computer when it opens. :/

If you have the gnome configuration editor isntalled (package name gconf-editor) you can run it to change the screen saver setting without actually invoking the screensaver applet that is locking your system up.

The location of the setting you need to change is in apps / gnome-screensaver. In the right-hand pane of gconf-editor just change the "themes" setting from whatever it currently is to empty square brackets, like this:

[]

That sets you up with the blank screensaver. Then you should be able to open the screensaver applet and choose another screensaver -- if you feel like messing around with it any more.

;)

I think the lockups caused by certain screensavers are indicative of video driver issues. Several of the screensavers will lock one of my laptops when its using the standard drivers. It has an nVidia Quadro Go 1400 card. If I install the restricted drivers, then then screensavers work without locking the system up.

---

