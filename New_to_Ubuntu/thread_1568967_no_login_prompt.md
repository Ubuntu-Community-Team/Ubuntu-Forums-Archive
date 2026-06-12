---
title: "no login prompt"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by new__buntu on 2010-09-06
So I've got a machine dual booting winxp and ubuntu. My problem is fairly straightforward - when I boot to Ubuntu (normal boot) all I get is the background to my usual login screen - the computer doesn't seem to respond to any input, either from the mouse (despite showing a cursor) or from the keyboard. The only thing I can think of that might have caused this is that I did a hard restart while the computer was suspended. Any ideas on how to fix my problem? Thanks in advance.

---

### Post by garvinrick4 on 2010-09-06
You have a live cd put it in and boot off of it and then run:
```
sudo e2fsck /dev/sdaX
```

X being whatever your ubuntu partition # is.

```
sudo fdisk -l 
``` (small L) will tell you your partition #

---

### Post by new__buntu on 2010-09-06
Symptom clarification: it turns out my login screen isn't frozen, it's just taking an inordinately long amount of time to start up. So I can technically still get into Ubuntu, it's just really annoying at the moment.

---

### Post by new__buntu on 2010-09-06
More information: I've done a clean ubuntu install, and the problem persists. Also, sometimes on boot up I'll get a screen for a couple of seconds saying that gnome-power-manager isn't responding, but it's never up long enough for me to react to it.

Also: garvin, that didn't seem to change anything, was that supposed to fix the problem or to diagnose it?

---

### Post by new__buntu on 2010-09-10
bump

---

### Post by cnbiz850 on 2010-09-12
I am just getting the same problem.  It has been fine.  Today the window manager had some problem with closing windows, so I restarted it (it has been run for a few days).  The login prompt is delayed for about 30 seconds and then come up.  But, a few seconds after I typed in my password, a popup warning saying something like "Power Manager is not responding.  Interrupt will cause data loss".  If I force continue, then I can login, but the login process is clearly slower.

---

### Post by cnbiz850 on 2010-09-12
Well, it appears that the problem here was related to the battery.  I know that battery has not been working for a year.  I am not sure if it is the battery that is dead or the circuits to the battery that has trouble (I assume it is the former, but any advice on how to determine that?).  Anyhow, I kept the battery in place.  When I detached the battery, things seem to go normal.

---

### Post by iiiears on 2010-09-12
Take a look at /var/logs (they include a time stamp for each entry) That can help you to narrow things down a bit.

---

### Post by taur on 2010-09-12
I have this problem too on a desktop (hence not battery related), could you specify more in detail which log firs I should be looking at ?

---

### Post by new__buntu on 2010-09-13
This is strange, but after I cat'ed a few of the logs and my computer seems to have returned to normal. It baffles me though, and I doubt that what seems to have fixed my computer likely won't fix others', so I'm not marking this solved just yet.

---

