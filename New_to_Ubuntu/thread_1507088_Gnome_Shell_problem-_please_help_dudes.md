---
title: "Gnome Shell problem- please help dudes"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by JimmyBrotron on 2010-06-11
Hey, so i'm a relatively  new ubuntu user compared to some, but I'm also pretty knowledgeable. Recently i'd been running gnome shell a lot, but i had downloaded it from the standard repos, so i figured i'd get the updated version from the Rico guy's repository. since then, gnome shell won't run/open/idk. here's the message terminal gives me when i run "gnome-shell --replace":

(mutter:9487): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (/usr/lib/mutter/plugins/libgnome-shell.so: undefined symbol: gjs_context_get_native_context)]
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!


Please help me out dudes, i was really starting to like gnome shell and its capabilities.

FYI, I'm running ubuntu lucid lynx, 64 bit

---

### Post by Peter09 on 2010-06-11
I think there has been a bug in gnome-shell - remember its still under development. I should update gnome-shell again and see if they have fixed the bug.

---

### Post by JimmyBrotron on 2010-06-11
No I know, the thing is it was working until i downloaded the version from rico's repository. Is there any way i could just delete all the gnome shell files on my computer and re-download them?

---

### Post by KdotJ on 2010-06-11
Maybe try purging it?

```
sudo apt-get purge gnome-shell
```

than start over again?

---

### Post by JimmyBrotron on 2010-06-11
So i ran the purge command and that, now this is the message terminal gives me i get after re-installing gnome shell from the repositories and trying to run "gnome-shell --replace"

(mutter:7954): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

---

### Post by vmonkey on 2010-10-19
Same problem which apperared after adding Rico's reppositary. If there is someone able to solve it, please help.

---

### Post by Harry33 on 2010-10-20
> **JimmyBrotron said:**
> No I know, the thing is it was working until i downloaded the version from rico's repository. Is there any way i could just delete all the gnome shell files on my computer and re-download them?

JimmyBrotron,
What rico's repository exactly you mean?
I think all of them aren't working very well, and in fact there are warnings:
"Make sure you know what you are doing!" (Testing PPA)
and
"DO NOT USE THESE PACKAGES !!!" (Staging PPA).

You should perhaps go and try Maverick, the G-S in Maverick's off. repo works quite nicely.
Or, do jhbuild.

---

### Post by pete_m on 2011-01-29
Came acroos this thread when faced with a similar problem when starting to develop Clutter-based stuff.


My error message led me to start inestigating  "vblank_mode configuration parameter" - which i suspect i'll find in xorg.conf...

I've got Gnome shell - when first installed it didn't work at all, but as time passed and with regulat apt-get upgrade - it's since fixed itself, and works well now
[URL="https://www.ohloh.net/accounts/pete_m"]
https://www.ohloh.net/accounts/pete_m[/URL]

[http://ip.icefactory.heliohost.org/](http://ip.icefactory.heliohost.org/)

---

