---
title: "scripting question"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by eddski on 2010-06-22
I want to learn scripting and have some videos for it, but I wanted to know if there is a big difference between Linux shell scripting and Unix shell scripting?

---

### Post by jbrown96 on 2010-06-23
Shell scripting depends far more on the shell (i.e. bash, csh, tsch, etc.) than the type of Unix. If you are just using shell-scripting to run certain commands, then yes, there will be quite a large difference. However, there's no way to make those portable.

Pure scripting is portable but you usually have to stick with a certain shell. Bash is the overwhelming default on practically all Unixes. 

Shell scripts aren't really designed to be portable, and other types of Unix aren't really all that common. I'd be more worried about learning a single shell, than about portability.

---

### Post by Zeike on 2010-06-23
> **eddski said:**
> if there is a big difference between Linux shell scripting and Unix shell scripting?

If portability to many systems is a big issue for you I suggest you consider using a script language such as perl or python rather than a shell script.  Of course this choice is very dependent on the purpose of your scripts.

---

