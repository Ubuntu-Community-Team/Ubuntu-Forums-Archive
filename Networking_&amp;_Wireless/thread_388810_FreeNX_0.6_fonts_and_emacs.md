---
title: "FreeNX 0.6 fonts and emacs"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by afoglia on 2007-03-19
I just upgraded FreeNX from the seveas 0.4 version to the dentalonline 0.6 version.  Now, the fonts in my gtk and qt apps are poorly rendered.  The tops of l's and i's are red, the tops of B's and f's are checkerboard.  Really, every character has a small problem like that.

Also, I am no longer able to run emacs. The error is "X protocol error: BadValue (integer parameter out of range for operation) on protocol request 45".  The only advice google gave involved checking for errors in xfontsel, but I have none.  I've tried forcing a font (-misc-fixed-medium-r-normal-*-15-140-75-75-c-90-*-*) with the -font tag with no effect.

Any other ideas?  Anyone else get better font rendering and/or emacs to work with freenx 0.6, or should I just downgrade back to 0.4.

---

### Post by afoglia on 2007-03-21
In the meantime, I tried switching to the official NX server (better fonts, though bigger (probably 100dpi vs. 75)).  Still got the same emacs error.  Then upgraded to feisty.  Added a unix entry to my /etc/hosts file to point back to 127.0.0.1 as suggested elsewhere in these forums.  Still can't get emacs to load, but the error this time is: "*** glibc detected *** emacs: double free or corruption (fasttop): 0x085496e0 ***"

---

