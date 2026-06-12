---
title: "Network Problem"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by childam123 on 2009-03-24
I seem to be having a couple of problems.  The first problem is that I have networking enabled, however the Icon at the top of the screen says it is disabled, even though the "enable networking" has a checked box.  i am running Gnome.

Second problem, is that my Windows Xp computers can browse the Ubuntu files just fine.  But I cannot browse the Xp files from the Ubuntu machine.  i don't know what i am doing wrong

---

### Post by lavinog on 2009-03-24
What version of ubuntu is this?
does the networking work?
what is giving you the message that networking is dissabled?

The problem is that your ubuntu machine isn't resolving names for your windows machines.
can you connect to them by using their ip addresses?
from the ubuntu machine try this to see if it can find the ip address:
```
nmblookup winxpcomputername
```

---

### Post by Iowan on 2009-03-24
Just to see if it works - try using smb://server-ip-address/sharename.

---

