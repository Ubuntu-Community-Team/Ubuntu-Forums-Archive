---
title: "Can't read wubi files on windows"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by arixion on 2009-10-09
I just installed WUBI on my windows Vista laptop (LG R410). I downloaded Explore2FS and tried to load C:\ubuntu\disks\root.disk, but all I got was blank.


What did I do wrong?

:confused:

Regards,
Arix

---

### Post by halitech on 2009-10-09
I'm not totally sure but I think that because wubi installs to a virtual filesystem inside a loop file, you can't read it from windows. I may be wrong but I think it needs to installed in a true file system in order to use windows tools to read the files

(stands back and waits for someone to proove me wrong)

---

### Post by arixion on 2009-10-09
Hmm... sigh. But really, if it is possible? By the way, what is a loop system? bsolute Newb here talking...

---

### Post by halitech on 2009-10-09
Like I said, I'm not totally sure and I've never used wubi (only have XP in a VM and seldom use it) but thats what I've read on here.

As far as the looback, hopefully this will explain it better then I can

[http://en.wikipedia.org/wiki/Loop_device](http://en.wikipedia.org/wiki/Loop_device)

---

