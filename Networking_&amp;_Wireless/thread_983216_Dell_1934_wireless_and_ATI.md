---
title: "Dell 1934 wireless and ATI"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Riaku on 2008-11-15
Hey guys, I have a dell Inspiron with a 1934 wireless card and an ATI Radeon x1250. How can I get these two to work O_O o_O I'm been trying for 6 hours. :(

---

### Post by rlzyoner on 2008-11-15
For my Dell machine, i need to use ndiswrapper for the broadcom drivers.
Have you tried this

---

### Post by Riaku on 2008-11-15
No, I haven't How do you do it? And for the ATI Radeon I've already tried the restricted drivers

---

### Post by rlzyoner on 2008-11-15
Ok i'm not at my own machine at the minute but you can load the .inf file into ndiswrapper withe the following command

sudo ndiswrapper -i /path/to/inf/file

run the command
ndiswrapper
to find out about its usage

---

### Post by Riaku on 2008-11-15
When I ttal ndiswrapper I get this error

[http://i36.tinypic.com/35bce1g.jpg](http://i36.tinypic.com/35bce1g.jpg)

---

### Post by Riaku on 2008-11-15
Ok I have ndiswrapper installed andI have the mutil device dell driver what do I do now?

---

### Post by Riaku on 2008-11-15
Bump

---

### Post by sirebral on 2008-11-15
If NDIS gives you problems check this thread out: [http://ph.ubuntuforums.com/showthread.php?t=779754](http://ph.ubuntuforums.com/showthread.php?t=779754)

Not sure about the ATI Problem.  I have CCC installed on my DELL, and that came with an 8.10 upgrade.

---

