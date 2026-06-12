---
title: "SMBus controller, what is it?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Paul T. on 2011-06-28
I'm running Ubuntu on an old Compaq Presario laptop, although it runs fine I keep getting error message on start up about 

"SMBus controller not enabled update BIOS or use force=1"

What is SMBus & should I be worried about it?

---

### Post by nomko on 2011-06-28
What SMBus is you can read it here: [http://en.wikipedia.org/wiki/SMBus](http://en.wikipedia.org/wiki/SMBus)
 
Is there an option in your BIOS to switch/turn off the controller? Check for it. Else the force=1 option has to be added in a boot file (can't look for it now since i'm not working on a Linux system).

---

### Post by Paul T. on 2011-06-28
The BIOS is very basic with few options to change, searching web it seems Compaq disabled any advanced BIOS features. The only thing I can find that is disabled is the "PXE Function"

---

