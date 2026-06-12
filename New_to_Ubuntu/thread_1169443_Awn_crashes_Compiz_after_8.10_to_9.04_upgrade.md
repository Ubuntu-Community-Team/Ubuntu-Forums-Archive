---
title: "Awn crashes Compiz after 8.10 to 9.04 upgrade"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by ashton88 on 2009-05-25
1 out of 4 times when I mouse-over or interact with the awn bar the awn bar will quickly disappear and a warning box will come up:

> **Starting avant-window-navigator**
Warning: Screen isn't composited. please run
compiz (-fusion) or another compositing manager.

Sure enough I try to flip the cube and I can't do it.  Compiz is gone.  Usually it is enough that I do a

```
compiz --replace &
```

and the awn bar comes back.  Compiz is reloaded, and it all works again until a few more interactions with the awn bar, and then it starts all over again.

Occasionally (about every 6th time) when I reload compiz awn gets confused and the icons stay at the top left of my screen.  At that point I need to do a:
```
killall awn && awn &
```


Everything is working perfectly under Intrepid, but yesterday I upgraded to Jaunty and this seems to be the only problem (so far)!

Avant Window Navigator 0.3.2
compiz 0.8.2
Video Driver Nvidia 180.51

Thanks!

---

### Post by ibizatunes on 2009-05-25
Personally i would reomve AWN and install gnome do, its in repos in 9.04 and that is more dynamic that AWN and personally i would say better

[http://do.davebsd.com/](http://do.davebsd.com/)

---

### Post by ashton88 on 2009-05-25
Thanks for the tip - it gave me some new insight!

I unloaded awn, and installed gnome-do.  Was playing around with that and it happened again - compiz crashed.  Since gnome-do doesn't depend on compiz it didn't crash as well.

But this would seem to indicate that awn had nothing to do with the initial crash?  Although the frequency is much less when I am not running awn - I ran for a good hour before compiz crashed.

What other information can I provide here / look at to help narrow this down?  What programs should I purge/reinstall?  I am going to go reinstall my video drivers just as a shot in the dark.

Thanks!

---

### Post by ashton88 on 2009-05-26
For anyone else having this problem I have posted this on the Compiz forums along with a dump from one of the crashes here: 

[http://forum.compiz-fusion.org/showthread.php?p=73493#post73493]("http://forum.compiz-fusion.org/showthread.php?p=73493#post73493")

---

