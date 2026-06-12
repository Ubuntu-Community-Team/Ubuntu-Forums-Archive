---
title: "install issues"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by pentium3ub on 2009-02-18
Hi, i recieved an extremely old Pentium 2 computer and i am attempting to install ubuntu 7.10.  The kernel loads, but the first message that appears on the black screen is this: "[ 132.044000] Buffer I/O error on device fd0, logical block 0"  The computer then runs through all sorts of other things such as setting the clock, and so on, then another error appears: [ 280.392000] 
piix4_smbus 0000:00:07:3: Host SMBus controller not enabled!"  What do i do from this point on?  Also, it may be useful to note that when i try to install xubuntu (the newest version) from a disk, the screen goes black and the monitor light changes to yellow (like asleep mode) and "no cables connected" flashes really fast on the screen every 10 seconds or so.  thanks; justin.

---

### Post by Cypher on 2009-02-18
Pentium 2 you say? What are the other specs of the machine? How much memory does it have? It must have at least 256MB to be able to run XFCE and you need more than that to run Gnome and KDE.

It is likely that the newest Kernel will stuble all over itself trying to run on the old P2, you might be better served by going back even farther in the Ubuntu releases to find something that "might" work..

But to be honest, the P2 machine is probably lacking in a lot of ways and is more appropriate as a door-stop than an actual machine..

---

### Post by oldos2er on 2009-02-18
Probably try a light distro, e.g. Damn Small Linux or Puppy.

---

### Post by scorchgeek on 2009-02-18
Sounds like there might be something wrong with the hard disk. Have you tried Live CD mode or another live distro? If you have under 384-512MB of memory, Live CD won't work, though. If live CD doesn't work, I would move the computer into use as a boat anchor or try a much lighter distro, as olddos2er suggested.

---

