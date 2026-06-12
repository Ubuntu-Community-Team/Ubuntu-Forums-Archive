---
title: "Segmentation Fault on Ubuntu 9.10, x64"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by tyliew333 on 2010-08-17
[LEFT]Hey guys,

I have been facing a problem for a week and yet I still could not get any solutions. I have a piece of C code which containing malloc(). I compile the same C code and run on 2 different machines, one is Ubuntu 10.04 (32 bit) while another machine is Ubuntu 9.10 (64 bit). When I compile and run on Ubuntu 10.04 (32 bit). It worked fine.  But when I compile and run on Ubuntu 9.10 (64 bit), it gave me Segmentation fault whenever it reaches malloc () in my C code. 

I'm new to ubuntu, anyone can tell me where lies the problems and solutions?

Thank in advance.

regards, tyliew
[/LEFT]

---

### Post by Paul820 on 2010-08-17
You might be better asking that question here [http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

Lots of C programmers there.

---

### Post by john newbuntu on 2010-08-17
You might want to check on the way malloc() gets used in the two architectures.  It could be because of malloc's return type (void pointer) that gets interpreted differently, especially when you cast to a return type that is narrower or wider.

---

### Post by tyliew333 on 2010-08-17
> **john newbuntu said:**
> You might want to check on the way malloc() gets used in the two architectures.  It could be because of malloc's return type (void pointer) that gets interpreted differently, especially when you cast to a return type that is narrower or wider.

Yes, the issue has been solved. The problem is different architecture give different size for pointer. You could refer to [http://ubuntuforums.org/showthread.php?t=1554810](http://ubuntuforums.org/showthread.php?t=1554810) just in order to see the problem in advanced.

By the way, thank you.

---

