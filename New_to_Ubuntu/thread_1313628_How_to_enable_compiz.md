---
title: "How to enable compiz ?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Innernet on 2009-11-03
At System > Preferences > Appearance > Visual effects; shows None.

Selecting "Normal", a message "Desktop effects could not be enabled"

From some instructions in the first two paragraps here:
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)
Tells Compiz is not enabled, that could be a reason why I cannot make the "Cube" to work.

How do I make the "cube" work with the mouse wheel ?

At System > Preferences ; I have both:
-CompizConfig Settings manager
-Simple CompizConfig Settings manager

Tried both, inside the first at General > General options > Desktop size > Horizontal virtual size is "4" ; Number of desktops stuck in "1"

Somewhere I need your expertise to enable Compiz? and make the 'cube' work.

---

### Post by jimmy the saint on 2009-11-03
What video card do you have?  Do you have the drivers activated for it?  Check under System>Administration>Hardware Drivers.

---

### Post by Innernet on 2009-11-03
Thanks for responding.
Shows no drivers.  Video/audio is integral with an Intel mainboard D845GVSR.  Where is the selection of such Intel 845 hiding ?

I think I saw that Intel 845 in 9.04, cannot find it now.

---

### Post by jimmy the saint on 2009-11-03
The intel 845 was blacklisted, meaning that it will not work for Compiz.  Apparently, there is a conflict with the card and compiz which results in hard freezes.  here is a bug report discussing the issue

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/469303](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/469303)

---

### Post by Innernet on 2009-11-03
Thanks.  That is bad news.  I will have to go back to my very reliable 7.10 instead, which works great with such mommyboard.

I do have the drivers CD for the 845, but unsure if applies to Windows only.  ](*,)

---

### Post by fo rizzle on 2009-11-03
Actually, I have another blacklisted card, and it works fine! Just run
```
SKIP_CHECKS=yes compiz
```

and see what happens! It worked for me...

---

### Post by fo rizzle on 2009-11-04
Actually, I have another blacklisted card, and it works fine! Just run
```
SKIP_CHECKS=yes compiz
```

and see what happens! It worked for me...

---

