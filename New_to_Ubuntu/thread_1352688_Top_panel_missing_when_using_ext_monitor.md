---
title: "Top panel missing when using ext monitor"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-12-11
Set up Netbook Remix for my friend. Works like a dream apart from 2 issues.
... one already highlighted below to do with the pulsating brightness...Have found a way around it but is still annoying.

Second problem is the disappearing top panel. I have exactly the same problem with my own laptop PC when I try to set the external monitor to 1280x1024 - the top panel vanishes in Karmic. When I mirror both screens, the problem is solved...except I have to mirror at a lower resolution than I would like.

On the Netbook Remix machine (9.10 also) the panel is lost at any reasonable setting for the external monitor....but reappears when the two are mirrored....while this is passable for my laptop, it is a joke on the Netbook as the big screen mirrors the tiny screen.

Any suggestions?

---

### Post by joes7 on 2009-12-11
It happened to me aswell, don't worry :)! Just open a new terminal and write:
```

xfce4-panel

```
Do not close the terminal. Shut down your PC, making sure that the "Save Session" button is selected.

---

### Post by abeisgreat on 2009-12-11
I believe this issue is because of the resolutions. What I *think* is happening is that the external monitor is a higher res than the notebooks. Gnome, by default, puts the toolbar at the top of the screen. When you extend your desktop with the second monitor, linux gets confused, and it places the toolbar at the top of the larger screen. But may have the same horizontal placement. Therefore, it would appear to disappear. As for a solution, I don't know. But I think that is the cause.

---

