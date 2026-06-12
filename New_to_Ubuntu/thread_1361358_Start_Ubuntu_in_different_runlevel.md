---
title: "Start Ubuntu in different runlevel"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by mamut0o1 on 2009-12-21
Hello; I was hoping someone could tell me how to stop Kubuntu from loading in graphical mode. I'd like to save memory resources by not loading into graphical mode. I just need the plain teminal level...I belive that's call runlevel 3.
can anyone help me out?


thanks!

---

### Post by bodhi.zazen on 2009-12-21
Ubuntu uses upstart and so there are no longer "run levels", although runlevel functionalitiy is preserved during the transition to upstart.

Even before upstart, runlevel 2, 3 ,4 , and 5 were all the same.

To boot without starting X, disable KDM.

You can do this for one run level, say run level 3, then add init 3 to you kernel line in grub =)

---

### Post by mamut0o1 on 2009-12-22
> **bodhi.zazen said:**
> Ubuntu uses upstart and so there are no longer "run levels", although runlevel functionalitiy is preserved during the transition to upstart.

Even before upstart, runlevel 2, 3 ,4 , and 5 were all the same.

To boot without starting X, disable KDM.

You can do this for one run level, say run level 3, then add init 3 to you kernel line in grub =)

Can you tell me how to stop / disable KDM so it wont show up again?
Thanks!

---

### Post by bodhi.zazen on 2009-12-22
I do not use KDM, see if this helps :

[http://ubuntuforums.org/showthread.php?t=1286032](http://ubuntuforums.org/showthread.php?t=1286032)

---

### Post by lewisforlife on 2009-12-22
> **mamut0o1 said:**
> Hello; I was hoping someone could tell me how to stop Kubuntu from loading in graphical mode. I'd like to save memory resources by not loading into graphical mode. I just need the plain teminal level...I belive that's call runlevel 3.
can anyone help me out?


thanks!

I believe adding the word TEXT to the end of your kernel line in grub would take care of your problem.  This will start your computer in text mode, you will not even have to mess with run levels.

---

