---
title: "vnc access beryl XGL"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by aliyanage on 2007-01-27
Hi all,

I was just wondering, does anybody know whether it's an issue to connect to via vnc to an ubuntu machine which is setup with beryl XGL?

I've installed vnc and tried connection over local host but somehow I just get a black screen...

any ideas why this could be?


regards
aliyanage

---

### Post by frederic.tardif on 2007-02-06
did you ever find the solution of this issue because i have the same trouble.

---

### Post by aliyanage on 2007-02-06
no mate, unfortunately I didn't have time to spend a lot of time in this... I will be spending time to fix this on Thursday and Friday, cause I'll be off work... so I'll let you know by then unless you find a solution :-D

---

### Post by ryscar on 2007-02-09
I was having the same problem.  I was able to get it to work by killing Beryl via ssh then reconnecting.  After that, everything was fine.

Hope that helps!

Ryan

---

### Post by frederic.tardif on 2007-02-09
I also tryied that, but even if I kill beryl, or if i use metacity as a window manager, Xgl still seems to be used as a renderer.

---

### Post by combatwombat_nz on 2007-07-23
Run the vnc server with the following switch: 
-noxdamage

---

