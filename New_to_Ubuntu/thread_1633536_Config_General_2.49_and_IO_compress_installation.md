---
title: "Config General 2.49 and IO compress installation"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by drordh on 2010-11-29
hey i am using Ubuntu 32 bit

i am trying to install  Config General 2.49 and IO compress and then i got this error 

.!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
ERROR: Can't create '/usr/lib/perl/5.10/Compress'
Do not have write permissions on '/usr/lib/perl/5.10/Compress'
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 at -e line 1
make: *** [pure_perl_install] Error 13

why??

---

### Post by oldos2er on 2010-11-29
If you ran **make install**, try **sudo make install** to give write permission.

---

