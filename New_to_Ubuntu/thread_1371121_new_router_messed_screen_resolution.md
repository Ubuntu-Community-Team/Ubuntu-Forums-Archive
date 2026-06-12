---
title: "new router messed screen resolution"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by mystmaiden on 2010-01-03
My router bit the tent this week, and I got a new one. Plugged it in and the mouse quit working. After much fiddling and messing about plugging and unplugging the mouse and the router and shutting down numerous times I got the mouse and the router going. Now my screen resolution is completely messed up. When I try to fix it, there is no option for 1024x768 on the drop down. Before when something would knock my resolution out of kelter a simple restart would do the trick, but not so now. It just shows 'unknown' monitor. I'm running Jaunty. 

I am really nervous about messing with xorg ...

mystmaiden

---

### Post by Methuselah on 2010-01-03
I don't really understand the relationship between the things that happened.
Did you make any manual changes to xorg.conf before?

Post the output of
```

xrandr -q

```

---

### Post by Captain_tux on 2010-01-03
I have to agree with Methuselah... I don't understand how a router (a system external to your PC) can change a PC's settings.

---

### Post by dearingj on 2010-01-03
This is just a guess, but it sounds to me like your various cables aren't being properly shielded from each other. I'd suggest moving them farther apart, and placing something non-electrical between them if possible. Also try to eliminate any static electricity that may have built up on them or your computer.

---

### Post by dearingj on 2010-01-03
I'd also suggest trying your mouse, monitor, and any other affected components (one at a time) with a different computer to see if the problems persist. I once had to troubleshoot a mouse that was damaged (short circuited?) in such a way that it worked fine but caused good keyboards to fail - any keyboard, on any computer.

---

### Post by mystmaiden on 2010-01-07
Thanks everyone, it seems it was the mouse afterall. I didn't even think about the fact that I'd changed the mouse out about the same time.

Good catch!

---

