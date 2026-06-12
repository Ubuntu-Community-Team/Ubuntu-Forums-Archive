---
title: "How to find the supported architecture ?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2010-02-02
I've installed ubuntu 9.10 on my AMD Athelon 3500+ x64 but the problem is that I can't remember the if this installation is a 64-bit one or a 32-bit one. 'Cos I downloaded the ISO and burned it on to a CD but I forgot to write what is the supported architecture.

Is there way to know that like the command lsb_release -a ?

---

### Post by ICEB3AR on 2010-02-02
```
uname -a 
```

---

### Post by lykwydchykyn on 2010-02-02
Try the "arch" command, it should tell you what architecture you're running.  Also, "uname -r" will tell you your currently running kernel.

---

### Post by sadaruwan12 on 2010-02-02
> **lykwydchykyn said:**
> Try the "arch" command, it should tell you what architecture you're running.  Also, "uname -r" will tell you your currently running kernel.

> **ICEB3AR said:**
> ```
uname -a 
```

Thank you both for the quick reply and you guys saved me thank you again.

---

