---
title: "screen saver crashes my system"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by charon2112 on 2009-05-17
Hi guys, I was browsing screen savers and the one called lattice caused my system to freeze.  Now I can't even change it, because just opening the SS browser dialog box causes my system to freeze up.  Is there a way through the terminal to change the screen saver?

thank you...

---

### Post by Didius Falco on 2009-05-17
> **charon2112 said:**
> Hi guys, I was browsing screen savers and the one called lattice caused my system to freeze.  Now I can't even change it, because just opening the SS browser dialog box causes my system to freeze up.  Is there a way through the terminal to change the screen saver?

thank you...

Hi,

Open ```
gconf-editor
``` via the Terminal, browse to the **apps/gnome-screensaver **settings and change the mode from "single" to "random". You can then quit gconf-editor, go to the screensaver browser and set it to a working one, or none at all.


I hope this helps...


Regards,

Didius

---

### Post by ajgreeny on 2009-05-17
Just for interest, I have a similar problem with the screen-saver **skyrocket**; when it starts it freezes solid, and I can do nothing with mouse, keyboard or anything, even Alt+Sys Rq +REISUB does not shutdown the system, so I had to do a power-off with the mains supply, not my favourite way to shutdown, though less of a problem than in windows.  I wonder if this is graphics card related; I have an ati 9200se card which is otherwise great with the system, but perhaps some screen-savers---?  What card do you run?

I usually use picture folder as my screen-saver just to see photos I had totally forgotten about, but was looking at alternatives yesterday, just out of interest.  I'll not do it again!

---

### Post by charon2112 on 2009-05-17
> **ajgreeny said:**
> Just for interest, I have a similar problem with the screen-saver **skyrocket**; when it starts it freezes solid, and I can do nothing with mouse, keyboard or anything, even Alt+Sys Rq +REISUB does not shutdown the system, so I had to do a power-off with the mains supply, not my favourite way to shutdown, though less of a problem than in windows.  I wonder if this is graphics card related; I have an ati 9200se card which is otherwise great with the system, but perhaps some screen-savers---?  What card do you run?

I usually use picture folder as my screen-saver just to see photos I had totally forgotten about, but was looking at alternatives yesterday, just out of interest.  I'll not do it again!


Thanks to both of you for responding!  I run an ATI Radeon X1650 PRO 512 meg...maybe it's an ATI issue?

---

