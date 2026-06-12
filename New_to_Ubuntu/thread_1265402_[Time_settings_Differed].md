---
title: "[Time settings Differed]"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by sarvankarthik6 on 2009-09-13
I installed UBUNTU 9.04 desktop cd Inside WINDOWS XP.

Time is different in both OS.

almost 9 haours different.

is it a problem?

plz help me. Im newbie.. plz advice in detailed way.:confused:

thanks in advance.

---

### Post by fooman on 2009-09-13
open a terminal and type or copy/paste the following into it:

```
gksudo gedit /etc/default/rcS
```press enter and type your password when prompted.

when the file opens,  edit the line that says "UTC=yes" to "UTC=no"

save and close the file.  then correct the times in both OS's....it will take a few reboots to see if it worked (it should).

hope that helps.

---

