---
title: "Connecting Projector to laptop"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by prashant112358 on 2009-05-20
Hi  all,
  
               I am not able connect projector(beamer) to my laptop. My laptop  is Dell Inspiron. When I connect a projector to my laptop I have to following things to get the projector working :
               **1. Restart my laptop** (that results in closing all my programs and applications)
                 **2. Start a new X serve**r by logging into different user
   
                 So, is there any way wherein  I  can connect the projector without restarting my laptop or starting a new X server. I think theres a way in which you edit the xorg.conf file. Can anybody pls tell the changes to be  done in this file OR pls specify any other way.

THANKS IN ADVANCE

---

### Post by Nepherte on 2009-05-20
xrandr will do the trick. See
```
man xrandr
```
for more information.

Typically running: ```
xrandr
```
will show you all connected screens (outputs) and the supported resolutions (modes). 

Executing:
```
xrandr --output <outputname> --mode <modevalue>
```
will put on the screen (output) with the given resolution (mode)

To turn a screen off:
```
xrandr --output <outputname> --off
```

---

