---
title: "rdesktop to XP machine &quot;unable to resolve host&quot;"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by phil79 on 2006-10-15
This is the third time I have tried linux in the last four years....I gave up on the last two times, but my God this Ubuntu is good...

Anyway - I want to rdesktop to my XP-pro machine...it's visible in:

Windows network->mshome->DREADNOUGHT

And I have enabled it for remote-login.

But when I try to rdesktop to it I get:

rdesktop -u philip -g 1280x1024+0+0 dreadnought

ERROR: dreadnought: unable to resolve host

I have tried upper and lower case, please can someone help me ???

Thanks.

--
P

---

### Post by apjone on 2006-10-15
sounds like a dns problem, give the xp machne a static ip and enter it into /etc/hosts

---

### Post by spd106 on 2006-10-15
Also check out this thread [http://www.ubuntuforums.org/showthread.php?t=274490](http://www.ubuntuforums.org/showthread.php?t=274490)

---

