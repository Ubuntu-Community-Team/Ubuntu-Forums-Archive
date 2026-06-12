---
title: "Toshiba M200 portege tablet - right-clicking in Ubuntu 9.10"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by CavemanJoe on 2009-12-04
Hey, folks.  I just made the switch from Windows XP, after having promised myself for years that I'd get around to it eventually. :)

So far I'm very happy, albeit with a few reservations that I'm sure some good software recommendations would overcome (more threads coming, I believe...) except for the fact that my tablet seems to be a bit screwy.  More accurately, I can't right-click.

(the Toshiba Portege M200 has an active digitiser - it's a convertible, the sort of laptop where you can write on the screen with an active stylus.  The right-click button is located halfway-up the stylus itself, and there's also a little button right on the top, where an eraser would be)

I've picked up a few basic Linux commands from tinkering with web servers, but this is the first time I've really used a GUI-based Linux machine.

I've been Googling around and seem to have found some answers - people recommend some edits to xorg.conf.  Thing is, I don't have a xorg.conf, and I was going to try to cobble one together until I saw a chap in [this thread]("http://ubuntuforums.org/showthread.php?p=8420629") saying that since 9.10, xorg.conf has been made redundant.  Thing is, if it's been made redundant, what should I be using instead?

Many, many thanks in advance,

-Caveman Joe

---

### Post by Favux on 2009-12-05
Hi CavemanJoe,

Welcome to Ubuntu Forums!

There's a couple of ways to do it.  Probably the easiest are Rec's script or using a modified wacom.fdi.  The .fdi (device information file) is what replaces xorg.conf along with HAL (hardware abstraction layer)/DeviceKit (what HAL became in Karmic).

See "Jaunty (9.04) & Karmic (9.10) Users" near the top of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Ask if you have more questions.

---

