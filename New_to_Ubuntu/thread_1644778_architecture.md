---
title: "architecture"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by mcsheffrey on 2010-12-13
What's the command that tells you your computer architecture i.e. amd64/inteli386 ?
Tks  Roy

---

### Post by A_M_S on 2010-12-13
you can try:

```
sudo lshw -C CPU

```

---

### Post by mcsheffrey on 2010-12-13
Thank you, will save that command.

---

### Post by oldos2er on 2010-12-13
Or **cat /proc/cpuinfo**

---

### Post by cipherboy_loc on 2010-12-13
Even better:
```
arch
```

Much easier to remember than a cat of some /proc file. :popcorn:

Cipherboy

---

### Post by StephenDavison on 2010-12-13
And yet one more way:
   uname -m

---

### Post by bodhi.zazen on 2010-12-13
> **cipherboy_loc said:**
> Even better:
```
arch
```

Much easier to remember than a cat of some /proc file. :popcorn:

Cipherboy

> **StephenDavison said:**
> And yet one more way:
   uname -m

Neither arch or uname show you the CPU architecture, they show you the KERNEL arch.

You need to cat /proc/cpuinfo and understand how to interpret it.

IMO

```
grep ' lm ' /proc/cpuinfo
``` is easy and reliable.

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

---

