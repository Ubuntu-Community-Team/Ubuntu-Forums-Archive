---
title: "Check driver interface?"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Tmicha8l on 2010-08-09
Hello

I'm trying to check my driver interface as I'm trying to follow a guide to get wireless working. The guide says it's in ~Kernel :( ?

Any help would be appreciated.

Kind Regards

---

### Post by sandyd on 2010-08-09
> **Tmicha8l said:**
> Hello

I'm trying to check my driver interface as I'm trying to follow a guide to get wireless working. The guide says it's in ~Kernel :( ?

Any help would be appreciated.

Kind Regards
run
```

lspci
```

---

### Post by jtarin on 2010-08-09
If your trying to determine what driver/module you have loaded...you can use the command ```
lsmod
``` to list all loaded drivers/modules.
Point us to the documentation would be better...or at least post the part that is confusing.

---

### Post by Peter09 on 2010-08-10
Just a word of warning - if you are going to follow a guide make sure it references Ubuntu and its not too old. Different distributions may have slightly different layouts and things do change over time. In general you should not need to do anything near the kernel to get your dirver working.
 
Best seek help here, as already suggested provide us with the output of the commands asked for above.

---

### Post by jtarin on 2010-08-10
Yes, run both commands. I suspect that carlee is prepared to ask you to run my command as I was going to ask you to run here command next.;)

---

