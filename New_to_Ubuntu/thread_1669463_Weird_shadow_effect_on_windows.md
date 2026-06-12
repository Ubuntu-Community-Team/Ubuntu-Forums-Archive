---
title: "Weird shadow effect on windows"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by CosmicFlux on 2011-01-17
Hey,

I've suddenly started experiencing a weird effect on all my windows. There is like a dark square over them and when I move one over the other it's like you can see the other window shape below as a black shadow, almost like transparency. 

I recently installed Mac4Lin and it asked something about metacity. I thought maybe that might have something to do with it so I tried turning it off and it worked, only I no longer have it as a window manager. 

This only happens when I'm using dual monitors. When I deactivate the second monitor it composits fine.


Cosmic

---

### Post by ArchieK on 2012-03-07
Hi had exactly same problem didn't help uninstalling mac4Lin but this worked

create an xorg.conf file in /etc/x11/ with this:

Section "Extensions"
Option	 "Composite"	"Disable"
EndSection

Cannot now find where I found this nugget and it's probably deprecated but it worked for me:)

---

