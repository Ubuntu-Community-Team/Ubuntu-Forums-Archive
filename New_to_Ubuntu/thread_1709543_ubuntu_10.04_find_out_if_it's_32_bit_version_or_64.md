---
title: "ubuntu 10.04: find out if it's 32 bit version or 64 bit version"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by mardibai on 2011-03-18
I have a very simple question, but i'm new to ubuntu ...

i installed ubuntu 10.04. many applications ask me before installing whether i have 32 bit or 64 bit version. how can i see that?

---

### Post by Scrineym on 2011-03-18
[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/]("http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/")

Hope this helps :P

---

### Post by andrewthomas on 2011-03-18
```
uname -a 
```
In the terminal

---

### Post by drs305 on 2011-03-18
This seemingly simple question has led to some long threads in the past.

The linked answer runs the command:
```
grep flags /proc/cpu
```
If "lm" is in the return, it's a 64-bit processor.

The "uname" command will return whether the system is *running* as 32 or 64 bit. "x86_64" is a 64-bit version. However, if I run the same command on a 32-bit VM on a 64-bit machine, the command returns indicate 32-bit (i686).

---

### Post by andrewthomas on 2011-03-18
> **drs305 said:**
> This seemingly simple question has led to some long threads in the past.

The linked answer runs the command:
```
grep flags /proc/cpu
```If "lm" is in the return, it's a 64-bit processor.

The "uname" command will return whether the system is *running* as 32 or 64 bit. "x86_64" is a 64-bit version. However, if I run the same command on a 32-bit VM on a 64-bit machine, the command returns indicate 32-bit (i686).
I assumed the OP was referring to the OS and not the processor.

---

### Post by drs305 on 2011-03-18
> **andrewthomas said:**
> I assumed the OP was referring to the OS and not the processor.

And for installing software that is what he would need to know and you provided a way of checking.

Since there were two differing results, I thought I'd differentiate them, although I probably should have elaborated that for installing software to an existing OS your response was the one needed.

---

