---
title: "Can't change visual effects"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-09
When I try to apply window effects like scaling in, exploding window, etc. and apply it I get a black screen with just the mouse.  I had to do the following to fix it:

> The problem here is not because of Compiz, I think it's caused by KWin's compositing manager. I'm having a problem here too, and I can't find a way to enable the desktop effects yet.

My problem was: desktop becomes black after logging in, pointer is visible. If yours is the same, please try out these steps:

1. As soon as you get the black screen, press ctrl-alt-F1 to go to tty1
2. Login with your username and password.
3. Do this:
Code:

nano ~/.kde/share/config/kwinrc

4. Under the [Compositing] section, edit the line with:
Code:

Enabled=true

change it to
Code:

Enabled=false

save by ctrl-O, enter
5. Exit by ctrl-x, go back to X (the black screen) by ctrl-alt-F7
6. Press ctrl-alt-backspace (to restart KDM).

You should have your desktop again, without the fancy effects.

If you ever find solution to enable the effects, please share it with us!


Does anyone know how I can apply these settings without crashing?

---

### Post by igknighted on 2008-12-09
> **tegnoto89 said:**
> When I try to apply window effects like scaling in, exploding window, etc. and apply it I get a black screen with just the mouse.  I had to do the following to fix it:




Does anyone know how I can apply these settings without crashing?

I notice from your other thread (the wireless one) that you have an nvidia quadro fx 140M graphics chip (restated for others viewing).

This sounds like a bug with the graphics driver.  I would test this with other opengl applications, and maybe other composite WM's (compiz, xfwm4 or xcompmgr) to confirm, and file a bug with (a) nvidia if it occurs across other WM's or opengl apps, or (b) both kwin and nvidia if it is just a kwin issue.

---

