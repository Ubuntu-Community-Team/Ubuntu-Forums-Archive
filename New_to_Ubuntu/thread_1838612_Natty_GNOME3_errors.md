---
title: "Natty GNOME3 errors"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by arjunajith on 2011-09-04
Hi
:popcorn:

I've been using ubuntu since 8.10
but it has been only a short while since I've started understanding what I type in the terminal.

So I need some help.
I suppose you all know the ppa:gnome3.... method to install gnome-shell

I have 1.5gigs of RAM (DDR1 though) and
and Nvidia Geforce 7300SE Video card (Bus : 64bit, Mem : 256MB)

enough to run say fifa 11 in wxp, unity in Natty etc.. overall a nice home GPU.

:arrow: But the thing is, once I install gnome3, It has less fps than me playing crysis on this system. I upgraded the drivers (proprietary) to the recommended one. 

And doggone my system turned into a picture frame with a mouse.. 
:lolflag:
nothing could be done except Ctrl+Alt+(F1-F6).

Then i had to ppa purge back to unity.
Can anyone help me wit this?:confused:

and also the "additional drivers" application (now when using unity) says that the proprietary driver is installed but not in use.

---

### Post by LowSky on 2011-09-05
Gnome 3 doesn't work very well in 11.04. I hear it will work better in 11.10.

---

### Post by sandyd on 2011-09-05
> **arjunajith said:**
> Hi
:popcorn:

I've been using ubuntu since 8.10
but it has been only a short while since I've started understanding what I type in the terminal.

So I need some help.
I suppose you all know the ppa:gnome3.... method to install gnome-shell

I have 1.5gigs of RAM (DDR1 though) and
and Nvidia Geforce 7300SE Video card (Bus : 64bit, Mem : 256MB)

enough to run say fifa 11 in wxp, unity in Natty etc.. overall a nice home GPU.

:arrow: But the thing is, once I install gnome3, It has less fps than me playing crysis on this system. I upgraded the drivers (proprietary) to the recommended one. 

And doggone my system turned into a picture frame with a mouse.. 
:lolflag:
nothing could be done except Ctrl+Alt+(F1-F6).

Then i had to ppa purge back to unity.
Can anyone help me wit this?:confused:

and also the "additional drivers" application (now when using unity) says that the proprietary driver is installed but not in use.
post output of
```

lsmod
```

---

