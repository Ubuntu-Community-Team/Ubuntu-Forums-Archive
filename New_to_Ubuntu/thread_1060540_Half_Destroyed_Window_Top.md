---
title: "Half Destroyed Window Top"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by ultblad1 on 2009-02-04
I've had this problem from the moment I installed Intrepid Ibex 8.10, and I'm not sure if it's an universal problem, or just a problem with my computer, since I'm very new to Linux.

The problem is that if I leave a window open for a few minutes (~2), then the top of the window (which is usually orange) turns gray, and the name of the window disappears too. Also, sometimes the disappearance is not total, so part of the window's top will remain, corrupting some of the text.

I do not have any special visual effects enabled, just "normal" under effects. Does anyone know what this problem is, and how to fix it? Thanks.

A screenshot is attached with the terminal window having the affected top bar in current, and the affected text is in the encryption window in current2.
I own the normal Nvidia graphics card, with nothing fancy at all.

---

### Post by petervk on 2009-02-04
I have exactly the same error. I've just been ignoring it.

What kind of graphics card do you have? I have a Nvidia 6150.

---

### Post by ultblad1 on 2009-02-04
I am running an Nvidia GeForce 7050 graphics card.
So far I have been ignoring the error too, but it would be nice if this error could be fixed.

---

### Post by Crafty Kisses on 2009-02-04
I had the exact same problem too, back when I had a NVIDIA GeForce 7150, since I've upgraded to a NVIDIA GeForce 9800GTX, but the way you can fix this is you can use Emerald, which is a theme manager and can change the way your window borders look, so install this package:
```
sudo apt-get install emerald
```
Pick a border you like off of GnomeLook or something like that, and see if that doesn't work.

---

### Post by RomeReactor on 2009-02-04
Hi. That problem is about [this bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508"); to solve it, install the [nvidia-180-modaliases]("apt:nvidia-180-modaliases") package, then go to 'System->Administration->Hardware Drivers' and you'll see the nVidia driver, version 180. Install that, reboot, and the problem should be gone.

---

