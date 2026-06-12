---
title: "Posix shared memory"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by garrydog on 2009-02-05
Hi
Can someone please tell me ,exactly what i should type in the terminal to install POSIX SHEARED MEMORY .
Thanks .

---

### Post by Titan8990 on 2009-02-05
I am fairly certain that would need to be compiled into the kernel....

---

### Post by bwang on 2009-02-05
Why do you need it? Wikipedia tells me that this is "large block of RAM for a multi-processor system". If you have multiple cores, Linux should utilize them all--no need to install anything.

---

### Post by garrydog on 2009-02-05
Hi
I need it for installing an ATI driver .

---

### Post by clustermonkey on 2009-02-05
Shared memory segments are part of the System V interprocess 
communication mechanisms and are usually part of the standard
kernel.  There are message queues, shared memory segments and
semaphores.  See "man 7 IPC".  That should give you a pretty 
good idea what it's all about.  If there is no man page, it 
is not likely installed.  It shows in my 8.04LTS.

---

### Post by PsySc0rpi0n on 2009-10-27
Hi...

I have updated from 9.04 64bit to 9.10 64bit and need POSIX too to install ATI drivers...

What should i do???

My system is:

E8400
4Gb Gskill PC8500 (2x2Gb)
ATI X1950XT


greets

---

