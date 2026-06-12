---
title: "Terminal Command Fails with - Unable to resolve host"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by mistypotato on 2009-07-23
Hi,

I am trying to use the Terminal to run MondoArchive.

But, the command line looks like this....

myusername@mycomputername2

(in other words, it has added a "2" after my computer's name for reasons I don't know).

When I type a command, it says it is unable to resolve the host, which I take to mean it cannot find itself?  

Where can I change the computer name back to its original name (minus the digit) ?

thanks

---

### Post by drs305 on 2009-07-23
Check these two files:

```

gksudo gedit /etc/hosts /etc/hostname

```

---

