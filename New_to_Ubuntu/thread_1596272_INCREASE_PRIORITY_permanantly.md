---
title: "INCREASE PRIORITY permanantly"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by PHINCY L PIOUS on 2010-10-14
Hi friends , is there any way to increase the priority of a program permanantly? i mean if i wanted to call the xkill via a keyboard shortcut when all my programs are hang up? i have created a keyboard short cut already.

---

### Post by bazzal1941 on 2010-10-14
You can set priority per user, have a look at /etc/security/limits.conf. I realise this may not be what you want to do but it might help.

---

### Post by bazzal1941 on 2010-10-14
You might also consider a simple command line of the form "nice -n -10 command" where in this case -10 will be added to the default nice value.

---

