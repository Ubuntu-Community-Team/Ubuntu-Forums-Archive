---
title: "Firefox crashing"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by wumpsdad on 2009-08-31
Yep, just ran UBUNTU 9.0.4 from a CD for the first time on my 866MHz PC.  Firefox keeps crashing or freezing, have not got beyond 1 page yet!  The PC has a built in cable network plug, and ages ago, thinking it wasn't working, I added a network card.  Could this be the problem?
Also, after clicking on a button on the desktop, the new screen always leaves behind a little square of the old image around the mouse cursor after displaying the new image.  should it do this? 

thanks, 

Wumpsdad

---

### Post by win_soft2005 on 2009-08-31
looks like your PC is not ready for Ubuntu 9.04, what spec?

---

### Post by wumpsdad on 2009-08-31
866MHz, 256 MB I think, 15GB HD.  Compaq small form factor.

---

### Post by stderr on 2009-08-31
Think that may be the issue. Running from CD is pretty slow anyway, but only 256MB RAM will cause problems (lots of swapping to hard disk). If you haven't got a separate graphics card, then it'll have to offload processing to the CPU, and that will also cause problems on a 866. To give you some indication, I personally wouldn't install a recent version of Ubuntu on a PC with less than 512MB RAM at *bare minimum*.

It may be able to cope a bit better with Xubuntu (using the XFCE window manager over the GNOME desktop environment), although IMHO it's a less user-friendly solution. Xubuntu generally requires less RAM than Ubuntu.

---

