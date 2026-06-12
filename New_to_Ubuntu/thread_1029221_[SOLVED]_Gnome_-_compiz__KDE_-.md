---
title: "[SOLVED] Gnome - compiz : KDE - ??"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-03
Hey!
I was wondering, what is KDEs compiz?
I have installed KDE4.x.x (stable) in Ubuntu, I thought that KDE is "just" a GUI, like a shell in win, but now I see that it is much more than that. So when I log on in KDE session I don't have compiz effects, open, close, minimize, 3d cube, etc. but I have less apealing (to me) KDE effects, like explode, and fade eff.
Naturally, I tried to turn on compiz, but it seems that compiz is not entirely compatible with KDE, especially the windowmanager, metacity. I have found out about KWin, to witch people address as the compiz for KDE, but it has no effects like compiz (burn, vacuum, beam up, 3d cube), is it posible to add these effects to KWin? Is KWin in fact in right click menu? And is it in System settings? How can I see if I actually have Kwin installed? Becuse I don't see any menu with KWin headline, so Im thinking it is those settings for aperance, window decorations, colours, animations etc> Am I right?

---

### Post by Ben Page on 2009-01-03
I realize that ubuntu is Gnome oriented OS, but is it possible that NO ONE knows KDE?

---

### Post by txcrackers on 2009-01-03
Compiz and KDE 4.x don't play nice because KWin is building in compositing features, which is what Compiz provides, so they conflict (essentially). With 4.1 you get most of the Compiz effects except for the "biggie" ones like the desktop-cube.

In KDE 4.2, the desktop cube (and cylinder and sphere!) are bundled in so there's no need for Compiz at all. (The sphere is really strange/awesome.)

---

### Post by anjilslaire on 2009-01-03
Even in gnome, when you run Compiz you are *not* running metacity, which is the default gnome window manager. I believe you can run Compiz on KDE4 if you wish, but it does require some adjusting.
If
KDE = Gnome, then
Kwin = Metacity

You want to disable Kwin in order to run Compiz, last I checked. I didn't care for KDE4 when t launched in 8.10 at th time, so I've gone to Xubuntu with Compiz on my desktop. 
Although, I'm tempted to try KDE4 on my Mini 9...

---

### Post by Ben Page on 2009-01-08
I was just wondering what is KDEs "compiz". After some research, I found out that KWin is in fact KDEs "compiz" witch is built in KDE (4.1 at least).
It is posible to run compiz with KDE by compiz--replace command but there are some serious issues when doing this, windows look crapy, decorations cannot be replaced, and GTK theme is ugly (also cant be replaced, at least not by simply selecting it).
Now I hear that KDE 4.2 has cube effect, but still, its not all about the cube, KDEs effects just dont look decent enough to even compare to compiz effects. So answer to my Q is:

               Gnome - Compiz = KDE - KWin

---

### Post by anjilslaire on 2009-01-08
Actually its more like:
Gnome - Metacity 
KDE   - Kwin

Metacity is the default window manager in Gnome.
Compiz is just an alternative window manager with some very nice 3d effects.
KWin is the default window manager in KDE, and it also happens to have ***some*** 3d compositing effects thanks to the new Plasma feature introduced in KDE4.

---

