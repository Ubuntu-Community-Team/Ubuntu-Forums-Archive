---
title: "Setting nice Levels and authentication issues"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by IkeRay on 2010-02-10
So, I know the reasoning for prompting for a password when installing apts or doing most things on the computer, I've accepted it and I don't have an issue.

but when I open system monitor and attempt to change priority of VLC to a high nice level (< 0) it closes the system monitor screen and says "starting administrative application" at the bottom.  if I open system monitor almost immediately to change it again, I get the same thing.  I can bump things to +0 nice (lowered priority) but I want to increase VLC to reduce pixelating/freezing while doing things in opera.  I've had success boosting it once or twice to -20 and it worked well, but now I keep getting this loop.

sorry meant to mention, its 9.04 (Jaunty?)

---

### Post by blazemore on 2010-02-11
From "man renice"
> Users other than the privileged  user  may  only  alter  the
     priority  of  processes they own, and can only monotonically
     increase their "nice value" within the range 0 to  19

This means it's right that the system should be asking you for authentication, but not right that it should crash like that.

---

### Post by IkeRay on 2010-02-13
any suggestions for this issue?

I've even opened the terminal and run sudo -l; left the window open and it still doing the crashing.

---

### Post by IkeRay on 2010-02-23
well, I've found a work around.

Administrator>Update Manager>check (requires password)
leave it open
Administrator>System Monitor>change nice levels

It's annoying to do all the time, but its better than not being able to up the levels at all.

---

