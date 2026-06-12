---
title: "ntfs filesystem reported as fuseblk in system monitor"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2009-04-11
[B]system moniter is reporting my NTFS drives of windows in fuseblk format ...


and suddenly my system started running very very slow....
[/B]
please help me out..

please i love ubuntu and i donn wanna make a reinstall.. (i will loose all my updates and softwares packages.)

---

### Post by SunnyRabbiera on 2009-04-11
This is actually normal, Ubuntu does not directly support NTFS so uses a workaround to make a NTFS system readable/writable thus the fuseblk entry.
As for slowdowns, that part I am unsure of as it really depends on how your hardware interacts with linux/Ubuntu

---

### Post by shreyanshjain8 on 2009-04-11
hey thanx..

but please can u tell me that how to force check the ubuntu filesystem drive at the time of restarting...

---

### Post by SunnyRabbiera on 2009-04-11
Once every 20 or so boots Ubuntu checks itself automatically for filesystem errors and faults.
There is no "defrag" feature as there really isnt need for one with the Ubuntu file system.
Can you give us the details of your slowdowns?
A lot of common triggers of slowdown in Ubuntu is either from Firefox or flash, more from flash as it does slow down things a little.
Details?

---

