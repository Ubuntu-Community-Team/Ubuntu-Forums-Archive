---
title: "Screensaver"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Erom on 2009-02-06
Hey all-

The default screen saver that shipped with Ubuntu 8.10 doesn't seem to want to work for me - I'm using a clean, totally default install, and the screen dims after the appropriate time lapse but just when it would go black, it instead jumps back to full brightness and appears to restart the idle timer (IE, if I tell the screensaver to run after 1 min of idle time, the screen dims then jumps back to full bright once every minute.)

I've tried a bunch of the 'savers, they all seem to do the same thing.

Ideas?

-Erom

---

### Post by fooman on 2009-02-06
you already have the "activate screensaver when computer is idle" box checked off....correct?

if yes....it happened to me once and all i did was open the screensaver preferences window,  *un*check the "activate screensaver when computer is idle" box and close the screensaver preferences box.

then reopen screensaver preferences....  and once again put a check next to "activate screensaver when computer is idle",  close the box and see if that makes any difference.

---

### Post by Erom on 2009-02-06
Yup, I have that checked. And I just tried the toggle dance to no avail. Is there some way to run the 'saver from console so I would maybe get the error message I might be missing?

---

### Post by fooman on 2009-02-06
try this in a terminal:

```
 gnome-screensaver-command --activate
```

---

### Post by Erom on 2009-02-06
Hah, well look at that, it runs from console just fine. Now I'm confused!

EDIT: Problem solved but weirdness remains- if I run it from the command line, it works, and then continues to work! *Until the next time I run the screensaver configuration GUI!* Then the 'savers fails every time until I run it from console again! 

So I guess I'm good to go, but wow is that weird.

---

