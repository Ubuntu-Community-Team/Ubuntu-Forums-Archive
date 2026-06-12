---
title: "[SOLVED] Glxinfo problem"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Glurf on 2008-12-17
When I type the command "glxinfo | grep rendering", I get the error 

"direct rendering: No (LIBGL_ALWAYS_INDIRECT set)"

I googled it, and people are saying it has something to do with compiz, but I haven't been able to find a solution. I need a "direct rendering: yes" to play a game, so does anyone know how I can fix this problem?

---

### Post by doobiest on 2008-12-17
In a terminal type in 'env' and see if this shows up
LIBGL_ALWAYS_INDIRECT=1

you could then try typing this into the terminal 

LIBGL_ALWAYS_INDIRECT=0


Google isnt helping me find out where it initially gets set but I suspect its in your xorg.conf so go check /etc/X11/xorg.conf for that.

---

### Post by Glurf on 2008-12-17
> **doobiest said:**
> In a terminal type in 'env' and see if this shows up
LIBGL_ALWAYS_INDIRECT=1

you could then try typing this into the terminal 

LIBGL_ALWAYS_INDIRECT=0


Google isnt helping me find out where it initially gets set but I suspect its in your xorg.conf so go check /etc/X11/xorg.conf for that.

Even when I set it to 0, it still gives me the same error, and when I close the terminal, it sets it back to 1. I'll disable compiz if I have to, or whatever is causing the error, its not to big of a problem.

---

### Post by Glurf on 2008-12-17
Ok I fixed the problem, it says "direct rendering: Yes" now. I went to System > Preferences > Appearance > Visual Effects Tab, and set it to none. The desktop isn't as flashy now, but if my game works, I don't care.

---

### Post by doobiest on 2008-12-17
Did you check your xorg.conf??

In retrospect I wouldnt expect setting an environment variable in the terminal to work. I would however expect if you did it from a tty console then boot X that tty it would work.

---

